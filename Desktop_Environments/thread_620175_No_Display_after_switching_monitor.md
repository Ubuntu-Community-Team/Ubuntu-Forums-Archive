---
title: "No Display after switching monitor"
date: 2007-11-22
forum: Desktop Environments
---

### Post by DrScum on 2007-11-22
I am running Ubuntu 7.04.

The other day I was working on another computer installing freespire. For this I just switched the monitor from the Ubuntu system to the system to be set up. When switching the monitor back I get a black screen after the system goes through the booting motions. I can still see the Grub menu but in yellow on black whereas it used to be white on black.
Obviously something got changed in the monitor and I don't know how to change it back.

---

### Post by 1/0 on 2007-11-22
What happens if you switch by ctrl+alt+f2? What about safe mode?

---

### Post by DrScum on 2007-11-22
ctrl-alt-F2 the first time darkens the display from the sort of grayish to complete black for a second and all the following times has no effect

safe mode? If you mean recovery mode, that leaves me with a console.

I guess what I would need is the command to reconfigure the display options but I am a Windows convert and thus my console experience ended with Win 3.1

---

### Post by 1/0 on 2007-11-22
Yeah, recovery mode (switched disros so many times). Well, if you get to console that's good. Question is where the problem starts. Anything in /var/log/messages (towards the end) or /var/log/xorg.0.log?

I would check xorg.conf.

```
sudo nano /etc/X11/xorg.conf
```

Check the HorizSync, VertRefresh and Gamma. Also the DefaultDepth and the corresponding Mode/ModeLine.

---

### Post by DrScum on 2007-11-22
The problem starts when the system switches to the grafic display i.e. during boot when the switch from the ubuntu logo occurs. Normally then you see a gray very fine checkered screen with the mouse as x in the center. That screen I don't see anymore.

---

### Post by 1/0 on 2007-11-22
Then I'd say xorg.conf is corrupted for some reason. Make a copy of it so you have something to go back to. 

I would then reconfigure xorg by:

```
dpkg-reconfigure xserver-xorg
```

Then reconfigure GDM (if you're using KDM just change it to that):

```
dpkg-reconfigure gdm
```

Reboot and see if it works (maybe reinstall the graphics driver). Also If you've got a Nvidia graphics card. See if temporarily changing nvidia to nv in xorg.conf helps.

---

### Post by DrScum on 2007-11-22
Well, that'll give me something to do. Thanks for your help.

---

### Post by 1/0 on 2007-11-23
Let me know if it worked out for you.

---

