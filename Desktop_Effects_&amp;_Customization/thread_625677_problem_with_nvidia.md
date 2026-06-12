---
title: "problem with nvidia"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by wholehog2 on 2007-11-28
hello,

I have installed kubuntu 7.10 on my pc ( DFI AD77 infinity, athlon xp 2600+, nvidia geforce 7600gs), all is ok with the nv driver, but I would like the 3d desktop whith effects. So I try to install nvidia-glx-new package but when I reboot my computer, I have this error message :

FATAL : error running install command for nvidia
(EE) nvidia(0) : failed to load the nvidia kernel module
(EE) nvidia(0) : *** abording ***
(EE) screen(s) found, but none have usable configuration

I am a beginner in linux and I don't know what I must do.
then I try to install the proprietary driver, but I have a black screen when I reboot the computer and the pc is lock.

Can you help me ?

---

### Post by Paul S on 2007-11-28
```
(EE) nvidia(0) : failed to load the nvidia kernel module
```

This probably means that something didn't get installed or configured properly

```
but I have a black screen when I reboot the computer and the pc is lock

```

You may actually be at a terminal.  If you hit <return>, you should get a command line prompt.  If you do, log in with your username and password.  If you don't get a prompt, then reboot and during the boot up, keep hitting the 3-key sequence Control-Alt-F1 to see if you can get to a virtual terminal.  When you do, login.  Then type "sudo aptitude reinstall nvidia-glx-new" and <return> to try reinstalling it.  Watch for any error messages.  If none, reboot, and it should work.  If it doesn't, login again and try editing your /etc/X11/xorg.conf in the terminal with the command "sudo nano /etc/X11/xorg.conf" .. look for the driver and make sure it's "nvidia".  Also, check if the driver gets loaded with the command "lsmod | grep nv" .. make sure you see "nvidia" listed.  If not, execute "sudo modprobe nvidia" and report back any error messages.

HTH

---

### Post by mellowd on 2007-11-28
You can also install and use Envy, it makes this all a lot easier

---

