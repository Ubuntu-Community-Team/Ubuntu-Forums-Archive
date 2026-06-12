---
title: "Beryl on Nvidia GeForce 2 400"
date: 2007-02-25
forum: Desktop Environments
---

### Post by radioraheem on 2007-02-25
I've tried searching with multiple terms but all I'm getting is a lot of false-positives so far.

I've got the nvidia drivers installed and beryl manager/themes manager run fine in Xubuntu 6.10.

The problem is when I tell the beryl-manager to switch to beryl from XFCE you can see the desktop try to switch but then it immediately defaults back to XFCE.  I'm not sure how I can run this via the terminal to catch any error reporting so I don't have much to work with right now.

I'm not a complete newb so I'm hoping someone can point me in the right direction.

Thanks in advance.

---

### Post by shareMenaPeace on 2007-02-25
When you start beryl from termial with
```

beryl-manager

```
you should see an error ... or check the log aswell

System -> Administration -> System Logs

---

### Post by abstrakt on 2007-02-25
Which drivers are you using?

I know for my Geforce4 ti4600, which is an older generation like yours, I needed to go back to the version 9361 official drivers from Nvidia.  Without knowing more about your situation, that's the first place I'd send you to look.

---

### Post by shareMenaPeace on 2007-02-25
Envy is an automatic script to install nvidia or ati drivers, which seems to work well.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

But o idea which drivers those are...

---

### Post by radioraheem on 2007-02-25
I'm  using Xubuntu so I don't have the default system log viewer (as far as I'm aware anyway).  If you know what log I should check I can let you know what's there.

Running beryl-manager doesn't give any new info.  The menu runs without a problem, the systray icon runs without a problem, but when I use the menu to select beryl as the window manager it tries and then defaults back to XFCE without giving any error/debug info.

Coincidentally I used Envy to install the nvidia driver on this machine.  First time using it and it seemed to work well.  I didn't have to make any changes to what it did to make everything (screen, Xorg) work correctly.

I'm not sure what driver it's using though.  In my xorg.conf the driver line simply states 'nvidia'.

---

### Post by shareMenaPeace on 2007-02-25
See your log with 

```
gedit /var/log/Xorg.0.log
```

Browse the xorg.conf log for lines beginning with EE or WW specialy of the grafic card.

Maybe it is xedit for you, not sure.

---

### Post by radioraheem on 2007-02-25
The only entry in that log I could find that seems to be an issue is:

> (WW) 32-bit ARGB GLX visuals require the Composite extension.

I installed Beryl using a guide on these forums and installed the driver with Envy.  Not sure what I missed in the process.

---

### Post by radioraheem on 2007-02-25
Yup, that did it.  Switched "Composite" "Disable" to "Composite" "Enable" in my xorg.conf and now beryl is running.

Thanks all!  You rock!

---

### Post by shareMenaPeace on 2007-02-25
Nice!:popcorn:

---

