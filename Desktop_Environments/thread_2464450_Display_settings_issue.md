---
title: "Display settings issue"
date: 2021-07-02
forum: Desktop Environments
---

### Post by daca4 on 2021-07-02
Hello Community,

   I am writing this post to ask You for help. I have connected 4 screens and I would like have them ordered as matrix. 
   In this configuration I am not able to move window to the bottom (see on the picture). But i am able move mouse around all area. 

   [IMG]https://i.ibb.co/nP5tpsq/Screenshot-from-2021-07-02-11-37-09.png[/IMG][IMG]https://ibb.co/3RLQKy5[/IMG]

  ```
lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 21.04
Release:    21.04
Codename:    hirsute



```

```
nvidia-smi Fri Jul  2 11:55:28 2021       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 460.80       Driver Version: 460.80       CUDA Version: 11.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  Quadro M4000        Off  | 00000000:81:00.0  On |                  N/A |
| 55%   64C    P0    51W / 120W |   2317MiB /  8124MiB |      2%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      6955      G   /usr/lib/xorg/Xorg                996MiB |
|    0   N/A  N/A      7103      G   /usr/bin/gnome-shell              186MiB |
|    0   N/A  N/A      7620      G   ...AAAAAAAAA= --shared-files      278MiB |
|    0   N/A  N/A      7794      G   ...AAAAAAAAA= --shared-files      429MiB |
|    0   N/A  N/A     10952      G   gnome-control-center              416MiB |
+-----------------------------------------------------------------------------+



```

    Please help me, how can I fix it ? 

Best Regards,
Dawid

---

### Post by vladi-boffi on 2021-07-05
try xrandr from shell

---

### Post by zircon_34 on 2021-07-07
Or you could use arandr, which has a gui to control display settings for xrandr.

---

