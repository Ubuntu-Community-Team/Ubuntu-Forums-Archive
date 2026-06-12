---
title: "Stale PID?"
date: 2009-05-12
forum: General Help
---

### Post by bayernanhaenger on 2009-05-12
Hi all,
I've done a search, and no one seems to answer the thread about this "stale PID" problem...

Basically, I'm running Ubuntu 9.04.  I've got Compiz on.  Every so often, my screen will flicker black, stop, and go to the login screen.  It's equivalent of what would happen if you hit Ctrl-Alt-Backspace.  

The log file is:
May 12 22:45:36 klusmaat-laptop kernel: [ 4014.765297] [drm] Num pipes: 1
May 12 22:45:36 klusmaat-laptop gdm[2833]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 12 22:45:37 klusmaat-laptop acpid: client 2838[0:0] has disconnected 
May 12 22:45:37 klusmaat-laptop acpid: client connected from 5744[0:0] 
May 12 22:45:38 klusmaat-laptop kernel: [ 4016.936497] [drm] Setting GART location based on new memory map
May 12 22:45:38 klusmaat-laptop kernel: [ 4016.938874] [drm] Loading R500 Microcode
May 12 22:45:38 klusmaat-laptop kernel: [ 4016.938945] [drm] Num pipes: 1
May 12 22:45:38 klusmaat-laptop kernel: [ 4016.938960] [drm] writeback test succeeded in 2 usecs
May 12 22:45:43 klusmaat-laptop pulseaudio[5889]: pid.c: Stale PID file, overwriting.
May 12 22:45:46 klusmaat-laptop anacron[6141]: Anacron 2.3 started on 2009-05-12
May 12 22:45:46 klusmaat-laptop anacron[6141]: Normal exit (0 jobs run)

I'm pretty confident it is :
May 12 22:45:43 klusmaat-laptop pulseaudio[5889]: pid.c: Stale PID file, overwriting.

this that is the problem.  I'm new to the inner workings of Ubuntu, but this stale PID business keeps recurring at the same time as my crashes.

How to solve?

Many thanks.

---

### Post by spiderbatdad on 2009-05-12
the fatal x error is when the screen goes blank and restarts. Maybe some more information would help. What graphics cards? Are you resuming from suspended sessions?

---

### Post by bayernanhaenger on 2009-05-12
> **spiderbatdad said:**
> the fatal x error is when the screen goes blank and restarts. Maybe some more information would help. What graphics cards? Are you resuming from suspended sessions?

Right.  I'm getting that.

I have a graphics card that is ATI MObility Fire GL V5200 w/ 256MB of RAM.

I am not resuming from suspended sessions.  Typically, I boot up, and it happens about an hour (or 1.5 hours) into the session.  Then, it repeats itself occasionally.

---

### Post by spiderbatdad on 2009-05-12
From what I have seen, ATI graphics cards and Linux can be a troublesome combination. Also your system is low on RAM for Ubnutu...256 is better suited to Xubuntu. I don't think that explains the fatal x error though. I could easily be wrong. The dmesg log contains a diagnostic message from the kernel of the boot process and other things. Sometimes helpful information can be had there. For example boot parameter (options) settings to help Ubuntu run on your hardware.

---

### Post by bayernanhaenger on 2009-05-12
> **spiderbatdad said:**
> From what I have seen, ATI graphics cards and Linux can be a troublesome combination. Also your system is low on RAM for Ubnutu...256 is better suited to Xubuntu. I don't think that explains the fatal x error though. I could easily be wrong. The dmesg log contains a diagnostic message from the kernel of the boot process and other things. Sometimes helpful information can be had there. For example boot parameter (options) settings to help Ubuntu run on your hardware.

Ah.  

As to the RAM, I upgraded to 2gb.  I think the 256 RAM is for the graphics card.  That, or my college's tech services department failed at posting the right specs.  Either way, 2gb ram is what i have.

How would i access this dmesg log?  Or use boot parameter?

---

### Post by spiderbatdad on 2009-05-13
I dont believe any boot options will help regarding the ATI card. Many users have reported repeated x crashes using this card in Jaunty. Some say use the driver provided by ATI: [http://support.amd.com/us/gpudownload/fire/Legacy/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.9&lang=English](http://support.amd.com/us/gpudownload/fire/Legacy/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.9&lang=English)
Others say use the following method:
[http://k3mist.com/linux/ubuntu-jaunty-ati-restricted-proprietary-fglrx-driver-direct-rendering-mobility-radeon-hd-series/](http://k3mist.com/linux/ubuntu-jaunty-ati-restricted-proprietary-fglrx-driver-direct-rendering-mobility-radeon-hd-series/)

---

### Post by bayernanhaenger on 2009-05-13
> **spiderbatdad said:**
> I dont believe any boot options will help regarding the ATI card. Many users have reported repeated x crashes using this card in Jaunty. Some say use the driver provided by ATI: [http://support.amd.com/us/gpudownload/fire/Legacy/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.9&lang=English](http://support.amd.com/us/gpudownload/fire/Legacy/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.9&lang=English)
Others say use the following method:
[http://k3mist.com/linux/ubuntu-jaunty-ati-restricted-proprietary-fglrx-driver-direct-rendering-mobility-radeon-hd-series/](http://k3mist.com/linux/ubuntu-jaunty-ati-restricted-proprietary-fglrx-driver-direct-rendering-mobility-radeon-hd-series/)

Thanks for the help.  I will try this out soon, and post back here.

---

