---
title: "Monitor Setup"
date: 2019-03-27
forum: Desktop Environments
---

### Post by sheenlim08 on 2019-03-27
Hello and I hope you all are having a wonderful day, I need some help on the Monitor support with Xubuntu.

I have 2 Video Cards of type Quadro FX 3800
```
sheenlim08@HPZ820-WKS:~$ nvidia-smi 
Wed Mar 27 15:47:35 2019 
+------------------------------------------------------+ 
| NVIDIA-SMI 340.107 Driver Version: 340.107 | 
|-------------------------------+----------------------+----------------------+
| GPU Name Persistence-M| Bus-Id Disp.A | Volatile Uncorr. ECC |
| Fan Temp Perf Pwr:Usage/Cap| Memory-Usage | GPU-Util Compute M. |
|===============================+======================+======================|
| 0 Quadro FX 3800 Off | 0000:06:00.0 N/A | N/A |
| 30% 79C P8 N/A / N/A | 729MiB / 1023MiB | N/A Default |
+-------------------------------+----------------------+----------------------+
| 1 Quadro FX 3800 Off | 0000:41:00.0 N/A | N/A |
| 30% 73C P12 N/A / N/A | 3MiB / 1023MiB | N/A Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes: GPU Memory |
| GPU PID Process name Usage |
|=============================================================================|
| 0 Not Supported |
| 1 Not Supported |
+-----------------------------------------------------------------------------+
sheenlim08@HPZ820-WKS:~$
```


When using the X.org X Server as the video driver, my monitor is being detected whatever DisplayPort I use on the two video card.
However, when I install the Nvidia drivers, none of the DisplayPort in 2nd video card are working. Plugging the monitor to them does not even provide a result to dmesg. I can only seem to utilize the 2 monitors using Nvidia drivers when I connect them both to the first video card.

Any ideas how to make the nvidia drivers work with two video cards?

---

### Post by Autodave on 2019-03-27
What driver did you install and where did you get it from?

---

### Post by sheenlim08 on 2019-03-27
I used the additional drivers Tab on "Software & Updates", the version is 340.107 which also seems to be the same version available to be downloaded from the nvidia website for my video card.

---

