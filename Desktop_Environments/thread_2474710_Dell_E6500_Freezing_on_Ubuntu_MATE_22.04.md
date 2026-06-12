---
title: "Dell E6500 Freezing on Ubuntu MATE 22.04"
date: 2022-05-06
forum: Desktop Environments
---

### Post by captaincyril on 2022-05-06
Hi,


I have a Dell E6500 Core 2 Duo which was running without any problems on Ubuntu MATE 20.04 and Ubuntu MATE 21.10. 21.10 was better at speed and the experience was more smooth as the proprietary driver (not nouveau) of NVIDIA was used.


[COLOR=#000000][FONT=Verdana]Graphics Card:
NVIDIA® Quadro® NVS 160M5 256MB DDR3[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Intel® Graphics Media Accelerator 4500MHD[/FONT][/COLOR]


Ever since I upgraded to Ubuntu 22.04 the computer has been freezing specially when I use the browsers FireFox and Chrome. So I downloaded 22.04 ISO and reinstalled it and the problem persisted. Then I reinstalled 20.04 and this time the driver wouldn't install due to the updated kernel I guess. Then I upgraded to 21.10 and then to 22.10 and still the problem persisted.


The system is freezing when I use any browser or even when I open many apps at the same time:
Visual Studio Code, FileZilla, System Monitor, Terminal, Telegram.


The system does not turn off the monitor when I put it on sleep or if by mistake it turns off then the system wouldn't turn on. It was working fine on 21.10 with NVIDIA driver.


The driver needed is NVIDIA 340.180 which is no longer support by NVIDIA for Ubuntu 22.04.


What are my options now?

---

### Post by captaincyril on 2022-05-09
I disabled Hardware Acceleration on FireFox and Chrome and things are working normally.

---

