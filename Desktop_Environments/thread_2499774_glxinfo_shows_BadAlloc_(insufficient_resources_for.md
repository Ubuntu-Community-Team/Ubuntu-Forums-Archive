---
title: "glxinfo shows BadAlloc (insufficient resources for operation)"
date: 2024-08-10
forum: Desktop Environments
---

### Post by nomadicsun on 2024-08-10
Hi folks,

I was trying to install gpu drivers following the steps in [Prerequisites for Linux NICE DCV servers - NICE DCV (amazonaws.cn)]("https://docs.amazonaws.cn/en_us/dcv/latest/adminguide/setting-up-installing-linux-prereq.html"),

After installing the nvidia gpu driver (nvidia-driver-535) in my ubuntu 20.04 LTS server, 

I tried to run the glxinfo which can be installed via '[COLOR=#16191F][FONT=Monaco]apt install mesa-utils[/FONT][/COLOR]', but it shows as below,

```

root@dcvserver03:~/bin# glxinfo
name of display: :0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  151 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  0
  Current serial number in output stream:  50

```

and the funny thing is, if i export DISPLAY=:1 and 'startx', then run glxinfo, it show as below,

```

root@dcvserver03:~/bin# export DISPLAY=:1
root@dcvserver03:~/bin# startx &
[1] 52270
root@dcvserver03:~/bin#
root@dcvserver03:~/bin# glxinfo |less
name of display: :1
display: :1  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
...


```

and for the display :0, it is the Xorg process started by gdm3.

and i tried to gdb glxinfo, and it exit at this line 460 in file mesa-demos-8.4.0/src/xdemos/glxinfo.c,  if (glXMakeCurrent(dpy, win, ctx)) 

i am a newbie for the linux graphical programming, can anyone help to direct what's the possible reason? Thanks very much!

---

### Post by currentshaft on 2024-08-10
glx

---

### Post by #&amp;thj^% on 2024-08-10
Also please show us this:
```
sudo systemctl get-default
```

```
sudo DISPLAY=:0 XAUTHORITY=$(ps aux | grep "X.*\-auth" | grep -v grep | sed -n 's/.*-auth \([^ ]\+\).*/\1/p') glxinfo | grep -i "opengl.*version"
OpenGL core profile version string: 4.6 (Core Profile) Mesa 24.0.9-0ubuntu2
OpenGL core profile shading language version string: 4.60
OpenGL version string: 4.6 (Compatibility Profile) Mesa 24.0.9-0ubuntu2
OpenGL shading language version string: 4.60
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 24.0.9-0ubuntu2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```

---

### Post by nomadicsun on 2024-08-10
Thanks for the reply, below is the output.

> 
root@dcvserver03:~# sudo systemctl get-default
graphical.target

root@dcvserver03:~# DISPLAY=:0 XAUTHORITY=$(ps aux | grep "X.*\-auth" | grep -v grep | sed -n 's/.*-auth \([^ ]\+\).*/\1/p') glxinfo | grep -i "opengl.*version"
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  151 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  0
  Current serial number in output stream:  51


root@dcvserver03:~# export DISPLAY=:0
root@dcvserver03:~# XAUTHORITY=$(ps aux | grep "X.*\-auth" | grep -v grep | sed -n 's/.*-auth \([^ ]\+\).*/\1/p')
root@dcvserver03:~# echo $XAUTHORITY
/run/user/123/gdm/Xauthority /root/.Xauthority


root@dcvserver03:~# glxinfo | grep -i "opengl.*version"
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  151 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  0
  Current serial number in output stream:  51





---

### Post by nomadicsun on 2024-08-10
eh, i'd to know the reason why glxinfo show the error for DISPLAY :0.

I compiled the glxinfo command from source code which can be download from [src/xdemos/glxinfo.c · main · Mesa / demos · GitLab]("https://gitlab.freedesktop.org/mesa/demos/-/blob/main/src/xdemos/glxinfo.c?ref_type=heads"), but still same error.
I guess it may related with the Xorg session which is started by gdm3 service, but don't know how to investigate further, can you advice? Thanks!

---

### Post by currentshaft on 2024-08-10
dj

---

### Post by nomadicsun on 2024-08-10
yes, it will affect nicedcv, and dcvgldiag will complian the X server doesn't support 3D acceeration.

nvidia-smi shows result is normal.
> 
root@dcvserver03:~# nvidia-smi
Sun Aug 11 11:04:15 2024
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.183.01             Driver Version: 535.183.01   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  Quadro RTX 6000                Off | 00000000:24:00.0 Off |                    0 |
| N/A   25C    P8              13W / 250W |      0MiB / 23040MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
|   1  Quadro RTX 6000                Off | 00000000:74:00.0 Off |                    0 |
| N/A   25C    P8              13W / 250W |      0MiB / 23040MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+


+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|  No running processes found                                                           |
+---------------------------------------------------------------------------------------+


---

