# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

AIM:
To simulate the process of sampling and multiplexing in PCM using python

SOFTWARE REQUIRED:
Google Colab / Jupyter Notebook

Python 3.x

Required Libraries:

numpy for numerical operations

matplotlib for plotting

ALGORITHMS:
Start the program.

Two distinct analog signals (50Hz and 120Hz) are successfully generated and quantized.

Their PCM representations are calculated and visualized.

A time-division multiplexed PCM signal is constructed by interleaving PCM values from both signals.

The output plots demonstrate:

Clear quantization of both signals.

Proper interleaving of PCM values for transmission in a multiplexed form.

A visual representation of how TDM works with PCM for efficient digital signal transmission.

End the program.

PROGRAM:
import matplotlib.pyplot as plt

import numpy as np

sampling_rate = 5000

duration = 0.1

quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

frequency1 = 50

frequency2 = 120

message_signal1 = np.sin(2 * np.pi * frequency1 * t)

message_signal2 = np.sin(2 * np.pi * frequency2 * t)

def quantize(signal, levels):

    step = (max(signal) - min(signal)) / levels

    quantized = np.round(signal / step) * step

    pcm = ((quantized - min(quantized)) / step).astype(int)

    return quantized, pcm

quantized_signal1, pcm_signal1 = quantize(message_signal1, quantization_levels)

quantized_signal2, pcm_signal2 = quantize(message_signal2, quantization_levels)

multiplexed_pcm = np.empty((pcm_signal1.size + pcm_signal2.size,), dtype=int)

multiplexed_pcm[0::2] = pcm_signal1

multiplexed_pcm[1::2] = pcm_signal2

t_mux = np.linspace(0, duration, multiplexed_pcm.size, endpoint=False)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

plt.figure(figsize=(14, 12))

plt.subplot(8, 1, 1)

plt.plot(t, message_signal1, label="Message Signal 1 (50Hz)", color='blue')

plt.title("Original Message Signal 1")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.legend()

plt.subplot(8, 1, 2)

plt.plot(t, clock_signal, label="Clock Signal", color='green')

plt.title("Clock Signal")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(8, 1, 3)

plt.step(t, quantized_signal1, label="Quantized Signal 1", color='red')

plt.title("Quantized Signals")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.legend()

plt.subplot(8, 1, 4)

plt.plot(t, message_signal2, label="Message Signal 2 (120Hz)", color='orange', alpha=0.7)

plt.title("Original Message Signal 2")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.legend()

plt.subplot(8, 1, 5)

plt.plot(t, clock_signal, label="Clock Signal", color='green')

plt.title("Clock Signal")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.subplot(8, 1, 6)

plt.step(t, quantized_signal2, label="Quantized Signal 2", color='purple', alpha=0.7)

plt.title("Quantized Signals")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.legend()

plt.subplot(8, 1, 7)

plt.step(t, quantized_signal1, label="Quantized Signal 1", color='red')

plt.step(t, quantized_signal2, label="Quantized Signal 2", color='purple', alpha=0.7)

plt.title("Quantized Signals")

plt.xlabel("Time [s]")

plt.ylabel("Amplitude")

plt.grid(True)

plt.legend()

plt.subplot(8, 1, 8)

plt.step(t_mux, multiplexed_pcm, label="Multiplexed PCM Signal", color='black')

plt.title("Multiplexed PCM Signal (Interleaved)")

plt.xlabel("Time [s]")

plt.ylabel("PCM Value")

plt.grid(True)

plt.legend()

plt.tight_layout()

plt.show()

OUTPUT:
![Screenshot 2025-04-21 115252](https://github.com/user-attachments/assets/c46a0425-fa86-4c48-a02c-4226136ef76c)


Result:
Thus the execution of Pulse code modulation using sampling and Multiplexing technique is successful.
