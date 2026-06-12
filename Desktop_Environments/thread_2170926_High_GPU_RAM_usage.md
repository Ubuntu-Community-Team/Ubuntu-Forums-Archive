---
title: "High GPU RAM usage"
date: 2013-08-28
forum: Desktop Environments
---

### Post by Homer on 2013-08-28
Hello,

I recently upgraded my desktop from 10.04 to 12.04.  Since that, I have problems using smplayer to play video with VDPAU enabled.  Seem like something (unity?) is consumming too much GPU RAM and there is not enough to play video then.

My graphic card is GeForce 9600GT 512MB.

nvidia-smi output:
```
+------------------------------------------------------+                       
| NVIDIA-SMI 4.304.88   Driver Version: 304.88         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name                     | Bus-Id        Disp.  | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap| Memory-Usage         | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce 9600 GT          | 0000:02:00.0     N/A |                  N/A |
|  0%   50C  N/A     N/A /  N/A |  80%  409MB /  511MB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+

```

Any idea how to fix this problem?

---

### Post by grahammechanical on 2013-08-28
run
```
top
```

or install htop and see specifically what is using how much of CPU and memory. You can also install System Load Indicator and that will give a realtime representation of CPU, memory and hard disk usage, among other things. Hard disk activity can affect performance. 

Regards.

---

### Post by Homer on 2013-08-28
> **grahammechanical said:**
> run
```
top
```

or install htop and see specifically what is using how much of CPU and memory. You can also install System Load Indicator and that will give a realtime representation of CPU, memory and hard disk usage, among other things. Hard disk activity can affect performance. 

Regards.

There is no CPU or RAM problem.  Problem is with **GPU RAM**.  top does't display wich app use GPU RAM.

---

### Post by serg2 on 2013-08-28
why do you think it is bad?  may be it uses linux style RAM consumption, that puts all available memory into buffers/caches

---

### Post by Homer on 2013-08-28
> **serg2 said:**
> why do you think it is bad?  may be it uses linux style RAM consumption, that puts all available memory into buffers/caches

I don't really know.  I'm looking why mplayer crash with VDPAU.  I read that VDPAU doesn't work well with cards with less than 128MB of GPU RAM. So I assumed VDPAU need at least that amount of GPU RAM.

---

### Post by Michael_Appleton on 2014-01-16
I posted a question here that is related: [http://askubuntu.com/questions/383987/high-vram-memory-unity-compiz-with-nvidia](http://askubuntu.com/questions/383987/high-vram-memory-unity-compiz-with-nvidia)

I'm sure using 90% or over 200mb of vram just for the desktop is excessive, and it noticeably affects performance. Try runnig with a different desktop environment and you'll see the usage go down and likely performance increase. Unity is a bit of a hog, at least on nvidia gpus!.

---

