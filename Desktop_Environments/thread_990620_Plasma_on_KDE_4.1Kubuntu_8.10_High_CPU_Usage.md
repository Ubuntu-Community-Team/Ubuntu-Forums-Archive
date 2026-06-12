---
title: "Plasma on KDE 4.1/Kubuntu 8.10: High CPU Usage"
date: 2008-11-22
forum: Desktop Environments
---

### Post by buddha001 on 2008-11-22
Just upgraded to Kubuntu 8.10/Intrepid. Everything went smoothly, but I've now noticed that Plasma is using up my entire cpu - 80+% cpu usage and it progressively gets worse the longer I keep it running. At some point I can't even switch programs, it's just frozen. I've removed all desktop plasmoids and pretty much only have the taskbar running.

Anyone else seeing this? Any ideas how to solve this?

---

### Post by inobe on 2008-11-23
open terminal and type **top** then hit enter.

locate what is using that amount and post back

---

### Post by freedom on 2008-12-22
Same here....
KDE 4.1.3 
plasma and Xorg uses together 90% CPU... :confused:
plasma alone around 60% and it is same with or without plasmoids and with composite effects enabled or disabled.
GPU is ATI HD 2600 and driver is latest fglrx from repo.
Does anyone have an idea?

---

### Post by quicklearner on 2009-12-25
I am having the same problem. 
But its kwin. 
Here is my  top result.
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6592 root      20   0  480m  92m 6700 R   24  2.3   9:08.56 Xorg
 7306 shiplu    20   0 61956  20m  14m R   13  0.5   3:55.09 kwin
 7883 shiplu    20   0  251m 120m  28m S    9  3.0   1:03.04 firefox
 7735 shiplu    20   0  224m  87m  27m S    1  2.2   0:37.05 xulrunner-bin
 7326 shiplu    20   0 49660 8556 7084 S    0  0.2   0:00.24 kaccess
 7503 shiplu    20   0 27864 8724 6616 S    0  0.2   0:00.28 kded
 8005 shiplu    20   0  118m  23m  15m S    0  0.6   0:01.17 konsole
    1 root      20   0  3056 1900  576 S    0  0.0   0:01.25 init


```

---

### Post by schnelle on 2009-12-25
I had these problems and I solved them by installing Kubuntu 9.10 and KDE 4.3 :) . Kde 4.1 (even 4.2) is an alpha release compared to Kde 4.3.

---

### Post by gunksta on 2009-12-25
I agree, especially on older ATI hardware where you can no longer use the proprietary drivers - newer versions of KDE are your friend. Plasma makes use of some nice blending affects and translucency affects that exposed many weaknesses in older drivers, which can cause your CPU usage to spike --- and stay there.

If upgrading is not an option, I would recommend installing the XFCE desktop. I had to use XFCE as my primary desktop on an older laptop during the KDE 4.0-4.2 days because of the driver problems under Plasma. I used the XFCE desktop, but continued to use all of my favorite KDE applications, because they continued to work just fine. 

With KDE 4.3, this is no longer necessary on this older computer with ancient ATI hardware.

---

### Post by quicklearner on 2010-01-10
I have disabled the plasma. But after few days, The problem starts again. 
:( 
```


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                           
 6805 root      20   0  410m  65m 5568 R   62  1.6  17:20.58 Xorg                                                                                                                              
 8680 shiplu    20   0  223m  92m  23m R   40  2.3  10:52.05 xulrunner-bin                                                                                                                     
 8823 shiplu    20   0  174m  75m  20m S    2  1.9   0:16.42 xulrunner-bin                                                                                                                     
 8935 shiplu    20   0  190m  59m  27m R    2  1.5   0:25.18 amarokapp
```

---

### Post by gunksta on 2010-01-11
It's not clear to me what's going on here (outside of the rather depressing CPU usage shown in your previous post).

Are you still running 8.10? If so -- this is your problem. I hate to be this blunt about it, but the first few releases of KDE 4 were full of problems like this.

Upgrade to Karmic, or accept that you are going to burn a whole in your mobo if you fan fails. There's nothing anyone here can do about it.

If you are running Karmic, then this is definitely an issue that warrants further investigation.

It just occurred to me that there is a small work-around you could try. Install XFCE and log into the XFCE desktop. Don't install Xubuntu unless you want to pull in a bunch of unnecessary dependencies like Thunderbird and what not. You just need the desktop. Look through Synaptic and install only what seems necessary. If you need help doing this, let me know and I'll post an apt-get command here for you to use.

XFCE has a Window manager than includes BASIC (super BASIC) compositing. Log into the XFCE Desktop and activate this compositing. XFCE has a control-center like thing and look around under Windows Manager or something to find this. It may be activated by default, I'm not sure. I haven't used XFCE since 8.10. If you CPU usage skyrockets while using the XFCE compositor, part of your problem is a crappy driver for your video card, which may or may not be improved by updating to Karmic.

If it's really just Plasma - XFCE should NOT trigger high CPU usage.

Also remember that many problems under KDE 4.0-4.1 also had to do with KWin. Make sure you have disabled the Dekstop Affects. Turning off Plasma will NOT disable the desktop affects, since they are part of KWin, not Plasma and these could be eating up your CPU cycles too.

Have I mentioned that you should really NOT use 8.10 anymore?

---

### Post by gunksta on 2010-01-11
It also looks like you are running xul-runner with some application that is causing problems too. 40% CPU usage for xul-runner looks like a problem to me too.

---

### Post by quicklearner on 2010-01-11
> **gunksta said:**
> It also looks like you are running xul-runner with some application that is causing problems too. 40% CPU usage for xul-runner looks like a problem to me too. 
May be. 

I disabled plasma and all desktop effects when I first encounter this problem(24% cpu). Then It become normal for some days.  Then suddenly I saw the problem (62% cpu) again. 

2 days ago, I got an update. It was an update on xu-lrunner  and firefox stuff. Now I dont see any high cpu usage. 

Lets see if It starts again. 
.

---

