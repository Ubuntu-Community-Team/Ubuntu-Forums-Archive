---
title: "Blank bootup screen on kubuntu gutsy"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by gladson1976 on 2007-12-26
hi all,

i've just installed kubuntu 7.10 gutsy and it works fine. there's only one thing thats bugging me is that the boot screen doesn't show up. when i start kubuntu all i get is a blank screen. but after sometime, i get the login menu. till then all i have is a blank screen and the only indication that its working is the hdd indicator.

ps. i had ubuntu 7.04 fiesty b4 this and that worked out fine. installed kubuntu over that from the canonical cd

thx

---

### Post by Zorael on 2007-12-26
Does your Grub tell the kernel to use a custom resolution? Meaning, do you have a vga=7xx argument in your Kubuntu entry in /boot/grub/menu.lst?

There's a known bug that makes everything go black if so. At boot, and in any virtual terminal (Ctrl+Alt+F1 to F6). I don't know if someone found an easy fix yet.

You can set it to use a smaller font, though, and it's fairly easy.
```
$ sudo dpkg-reconfigure console-setup
```

Accept all settings without changing them (unless you want to, like keyboard layout), EXCEPT when it comes to the part where it asks you if you want your terminal output in VGA or Fixed mode. Pick VGA. I use font size 8.

I believe it's also possible to unlock more Fixed options if you manage to unblacklist some framebuffer module or another, but I'm not quite sure which or how it's done. Google it. :>

edit-- You may also want to double-check that you have the usplash package installed, that your /boot/grub/menu.lst Kubuntu entry is properly sending the "splash" argument to the kernel, and that you don't have any weird resolution set in /etc/usplash.conf.

---

### Post by stanz on 2007-12-27
I noticed the black screen, but thought they took out the logo and progress bar?
Dhaaaa....well anyway,
I checked my /boot/grub/menu.lst and its got 'quiet splash' entered.
And in /etc/usplash.conf its got: 'xres=1280' 'yres=1024'. My screen is '1024x768', is this the kinda weird resolution your referring to?
Thanks in advance...

---

### Post by gladson1976 on 2007-12-27
hi Zorael,

am at work right now (WinDoze #-o) will check it out as soon as i get home. :)

---

### Post by thefirstM on 2007-12-27
What you need to do is change the resolution value in your /etc/usplash.conf file to whatever you monitor's maximum (or preferred) resolution is.  I had a similar problem with my system where it was trying to drive my 1024x768 15" flat panel at 1280x1024.  This was with regular Ubuntu, but they should be the same.

---

### Post by Tonren on 2007-12-27
I just followed thefirstM's instructions, and my shutdown splash was successfully enabled.  However, my boot splash is still not there!  I'm going to try Zorael's suggestion now.  Also, this problem might be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/156225").

**EDIT**: WHOO!  It works.  Between thefirstM and Zorael's suggestions (dpkg-reconfigure console-setup and fixing the resolution in /etc/usplash.conf), my splash is now fully functional.  Thanks, guys!  ++

---

