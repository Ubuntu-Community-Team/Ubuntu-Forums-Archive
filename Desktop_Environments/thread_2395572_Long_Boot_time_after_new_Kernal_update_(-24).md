---
title: "Long Boot time after new Kernal update (-24)"
date: 2018-07-03
forum: Desktop Environments
---

### Post by waburden-4 on 2018-07-03
Re: ubuntu 18.04 64 Bit

Post update to new version 24 kernel my hang to login is approx. 3.5 - 4 minutes instead of the usual 13 seconds. During this time no more than 2 of 5 radio buttons display red under the Ubuntu Logo. After the hang, the boot proceeds to login normally.

 I hit the power button on my laptop and got the following display with the last line which seeming to indicate an issue: "Started Gnome Displ;ay Manager.ss finishes up...ce....tem changes.PP link was shut down". 

Someone in a similar post suggested moving the mouse cursor during the boot but that did not work for me. 

Kernel Version - 23 boots normally.

---

### Post by chasb2 on 2018-07-04
Confirming the same behaviour:  No UI change to radio buttons at all beneath Ubuntu logo screen, no cursor activation with either USB radio mouse or touchscreen for about 80-90 seconds, after which a cursor appears and the system moves to Gnome (default Xorg)logon.
Reverting to previous kernel - 23 returns an acceptable time for handing to Gnome after boot.  About 15 seconds.
Have configured Grub2 to boot into version 23.  
Can anyone confirm that this isn't a security risk?

---

### Post by jeremy31 on 2018-07-04
You could see what is causing the long boot time with ```
systemd-analyze blame
```
I have no issues using 4.15.0-24

---

### Post by chasb2 on 2018-07-04
Thanks** jeremy31**.  All systemd-analyze blame reports is that plymouth is hanging.  
A bit more reading around the forums gives some useful advice:...

This thread
[https://ubuntuforums.org/showthread.php?t=2395459](https://ubuntuforums.org/showthread.php?t=2395459)
may help those who, like me, can't get any useable response in the
splash screen from mouse, touchpad, or most keyboard input.

Looking now at finding out how to bypass the Plymouth boot progress screen altogether.

Confirming the workaround that my setup clears the Plymouth screen and gets me to login when I hold down the SHIFT key during boot.

---

### Post by jeremy31 on 2018-07-04
chasb2 so the fix is to do what?  I would suspect it would be to edit /etc/default/grub and remove splash from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by chasb2 on 2018-07-04
> **jeremy31 said:**
> chasb2 so the fix is to do what? 

Not a fix, but the workaround that works for my system, where the keyboard and mouse and touchpad hardware is getting stalled by
another process, to hold the SHIFT key during boot, as I wrote above.


> I would suspect it would be to edit /etc/default/grub and remove splash from GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

That doesn't get rid of the hang for my system, but it does give me the terminal rolling commentary black screen so I can get an idea of what's
getting hung, because I can't exit Plymouth to get to that because I'm not being given keyboard control to execute CTRL+ALT F2 -    or anything else.

Preliminary look says the snappy daemon is doing the holdup.
I have an idea that each system will have unique start conditions where it's the luck of the hardware draw whether the new kernel creates this hang.
I'll wait a few days and see if there's any more reports to help find a pattern.
Thanks for the help there.

---

### Post by apeitheo2 on 2018-07-05
You could give this a try:
```
sudo apt install haveged
sudo systemctl enable haveged
```

[https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140)

It's a known bug and the fix should be released soon, but in the meantime, haveged works. Click the above link for more info.

---

