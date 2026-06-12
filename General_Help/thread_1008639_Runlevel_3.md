---
title: "Runlevel 3"
date: 2008-12-11
forum: General Help
---

### Post by wr.oreilly on 2008-12-11
I am running a Gateway FX
NVIDIA 9800 GT 512
Intel Wi-Fi 5100
Intel Core 2 Duo P8400 2.26
Conexant High Definition SmartAudio 
NVIDIA HMI Audio
--

I am currently running a Dual-Boot Vista (64)/Ubuntu 8.04 (64-bit)and trying to install the NVIDIA Graphics card. 
(NVIDIA-Linux-x86_64-177-82.pkg2.run) in the terminal, and it says I am running an "X" server. Doing some digging I found the Runlevel (After typing telinit, I found I am running 2) needed to be on 3? So, I opened etc/event.d/rc3 <--- (something similar to that) and tried following the instructions in the text document; but after I tried typing:
Start on runlevel 3
stop on runlevel [!3]

and it keeps going until "console output", which the termninal says is not installed, and says to type apt-get controller..... which then says it is unavailable to install. 

I just am trying to get my Laptop set up with drivers, and I'm already fearing the Intel Wi-Fi driver...
I have to use Windows to use the Internet so ask if you need any clarification. 

I am a n00b and am trying to get acquainted with ubuntu so any help in very basic steps would be awesome!

---

### Post by reality1011 on 2008-12-11
Runlevel 2-5 are for multi user... they should all preform the same

---

### Post by bodhi.zazen on 2008-12-11
Well, more then that, Ubuntu uses upstart so runlevels are becoming obsolete and are provided for back compatibility only.

On Ubuntu the run levels are all the same.

If you want an easy way to install the Nvidia driver, either use the one in the repos or envy :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by x1a4 on 2008-12-11
Or, if you don't want to use the drivers in the repositories or Envy, hit Ctrl+Alt+F1 and login as yourself.  Then run
```
sudo invoke-rc.d gdm stop
```
and install the driver.  When finished run
```
sudo invoke-rc.d gdm start
```
to restart GDM.  You will still be logged-in at the console so hit Ctrl+Alt+F1 again and press Ctrl+D to logout then Ctrl+Alt+F7 to go back to your X session.

---

### Post by nzadLithium on 2008-12-11
does 8.04 have new enough drivers in the repo's to support wr.oreilly's card?

Maybe wr.oreilly should upgrade to 8.10 and install the drivers from the hardware driver program then?

---

