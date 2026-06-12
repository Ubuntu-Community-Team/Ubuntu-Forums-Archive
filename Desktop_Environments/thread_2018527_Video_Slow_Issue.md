---
title: "Video Slow Issue"
date: 2012-07-06
forum: Desktop Environments
---

### Post by securitymeddler on 2012-07-06
All, 

Just installed Ubuntu 12.04 x64 on a new dell T5500. Things run okay in Unity 2d. But in regular mode keyboard response feels like it's almost a second delay. Hitting the Windows key takes a good second for the Unity launcher thing to come up. 

I am pretty new to all this and really don't know where to start. I tried the base Ubuntu driver and two different ones in the additional drivers program.

if this helps: 
lspci | grep -i nvid
03:00.0 VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 295] (rev a1)

---

### Post by msammels on 2012-07-06
It's probably nothing to do with your video. Can you run:

```
sudo top
```

And find out what's using the most CPU?

---

### Post by securitymeddler on 2012-07-06
Thanks for the reply. 

I've restarted the whole system clean and still the same issue. nevertheless here is my top

```

top - 12:43:55 up  3:01,  3 users,  load average: 0.61, 0.65, 0.67
Tasks: 291 total,   2 running, 287 sleeping,   0 stopped,   2 zombie
Cpu(s):  0.7%us,  0.8%sy,  0.0%ni, 98.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  24684704k total,  8199228k used, 16485476k free,    82176k buffers
Swap: 25161724k total,        0k used, 25161724k free,  5469112k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3263 danwilso  20   0 2473m 644m 589m S   15  2.7  40:18.72 VirtualBox         
 3667 danwilso  20   0 1168m 257m  38m S    8  1.1   7:07.08 firefox            
 2532 root      20   0  349m 244m  49m S    7  1.0   5:27.27 Xorg               
 4500 danwilso  20   0  583m  19m  11m S    1  0.1   0:02.90 gnome-terminal     
 2707 danwilso  20   0  659m  16m  11m S    1  0.1   0:32.02 metacity           
 3235 danwilso  20   0  616m  10m 7240 S    0  0.0   0:24.24 VBoxSVC            
    1 root      20   0 24424 2412 1348 S    0  0.0   0:04.56 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.02 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    9 root      20   0     0    0    0 S    0  0.0   0:00.02 kworker/1:0        
   10 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.02 watchdog/1         
   13 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0     


```

---

### Post by 3Miro on 2012-07-06
How much video RAM do you have and how much have you assigned to Virtual Box? Do things work faster if you close Virtual Box?

I have seen video performance decrease with virtual box simply open on another workspace.

---

### Post by securitymeddler on 2012-07-06
I can confirm the video issue happens when VirtualBox is or isn't running. Just happened to be working in Office at that moment. 

I had a recommendation to switch to Gnome from Unity, but same issue. In 2d envionments things are great though. 


Video RAM is 
256  MB GDDR3

---

### Post by 3Miro on 2012-07-06
Unity 3D and Gnome-shell both use OpenGL effects from  your video card. Unity 2D and Gnome classic use the CPU and generally run faster. My guess is that the problem is with the video card. You can try to install Compizconfig-Settings-Manager and turn some of the Unity effects off, but if Gnome-shell doesn't work very well either, then you may be better off sticking to 2D.

For 2D environment, you can also use KDE (disable effects), XFCE or LXDE.

---

### Post by securitymeddler on 2012-07-06
That's what I have read on a couple forums too. It's disappointing as I was under the impression this was a supported video card. 

Any recommended video cards? I don't need anything fancy at all I just prefer a visually appealing interface. The 2d interface isn't something I want to look at for 8 hours  a day.

---

### Post by LHammonds on 2012-07-06
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

[https://www.linux.com/news/hardware/drivers/8203-is-my-hardware-linux-compatible-find-out-here](https://www.linux.com/news/hardware/drivers/8203-is-my-hardware-linux-compatible-find-out-here)

[http://unix.stackexchange.com/questions/9553/how-do-i-choose-a-graphics-card-for-linux](http://unix.stackexchange.com/questions/9553/how-do-i-choose-a-graphics-card-for-linux)

---

### Post by 3Miro on 2012-07-06
I had reasonable performance on Nvidia GT 210 (with 1GB of RAM). I also have used Unity 3D with great success on GTX260, GTX250, GTX570. My guess is that GTX550 will work great too as well as the 400 series (430, 450, 460 ... ).

---

