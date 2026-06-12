---
title: "Fatal server error: no screen found"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by gullwingdoors on 2007-07-01
I'm getting this error when I try to install. Problem is, it's a laptop. There definitely is a screen attached. Why is it not recognizing the screen? (even though it is displaying on it) What can I do to fix this? Thanks!

---

### Post by khedron on 2007-07-01
> **gullwingdoors said:**
> I'm getting this error when I try to install. Problem is, it's a laptop. There definitely is a screen attached. Why is it not recognizing the screen? (even though it is displaying on it) What can I do to fix this? Thanks!

Hmm. Is this when you boot the Live CD, or once you have installed it and are trying to boot into Ubuntu? 

 The reason it can display the error message on screen is probably that there are two display modes: text and graphical. The text one is basically a failsafe. 

 I reckon that there are two possible causes to the error: 

1. Your /etc/X11/xorg.conf is misconfigured. This contains all the settings for X, which controls the graphical display mode.

 2. There is some graphical driver that is failing to load.

 I think I'll be able to troubleshoot more when I find out whether the problem occurs when using the Live CD or when trying to boot from the installation on the hard disk.

---

### Post by neptho on 2007-07-01
As noted above, we need to know what it's complaining about.  As well, a laptop model may help, but it'll help much more if you can find what video card is present (ATI, NVidia, Intel), and the model.

---

### Post by gullwingdoors on 2007-07-01
It is a one year old Dell Inspiron E1505. The graphics card is an ATI Mobility Radeon X1300. The error occurs when trying to install from the live CD.

Oh, I should mention also, that right before the error comes up, my screen blinks a few times, like it's trying to change the screen's settings or something.

---

### Post by neptho on 2007-07-01
Those of us with ATI cards are still left a bit wanting with Feisty, hopefully this will be addressed in Gutsy.  It's fairly easy to make it work with Feisty, however.  When you go to install, and it crashes out, login,  and run the following:

```
%sudo apt-get install xorg-driver-fglrx
%sudo aticonfig --initial
%sudo aticonfig --overlay-type=Xv
```

Then, restart X with:

```
%sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm start
```

Finally, after you install everything and reboot into Ubuntu, it will have a problem again, since you were running the installation from a RAM disk.  Rerun the whole thing again:

```
%sudo -c 'echo "deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main
restricted"' >> /etc/apt/source.list
%sudo apt-get update
sudo apt-get install xorg-driver-fglrx
%sudo aticonfig --initial
%sudo aticonfig --overlay-type=Xv
```

Then, restart X with:

```
%sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm start
```

Make sure you are able to use the ethernet just in case; I have heard of problems with people manually editing their apt lists to use the CDROM for the fglrx install after it's actually installed - that's what the APT addition above *should* do.  Remember to comment out that line when you're up and running in X11

---

### Post by gullwingdoors on 2007-07-02
Ok, this is going to sound really noobish I'm sure, but I've never really done much with the command prompt. What do i do exactly? I tried just typing in the code you posted, but it's not doing anything.

You said I need to login? How do I do that? The install doesn't get far enough to make a username and password.

Thanks for the replies.

---

### Post by neptho on 2007-07-02
> **gullwingdoors said:**
> Ok, this is going to sound really noobish I'm sure, but I've never really done much with the command prompt. What do i do exactly? I tried just typing in the code you posted, but it's not doing anything.

You said I need to login? How do I do that? The install doesn't get far enough to make a username and password.

Thanks for the replies.

Press Ctrl-Alt-F1 to go back to a normal terminal when X crashes out, they type the things after the "%", the "%" just means you are at a command line shell.  It may look different, but that's fine.

---

### Post by newbie2 on 2007-07-03
[http://ubuntuforums.org/showthread.php?t=490937](http://ubuntuforums.org/showthread.php?t=490937)

---

### Post by neptho on 2007-07-03
> **newbie2 said:**
> [http://ubuntuforums.org/showthread.php?t=490937](http://ubuntuforums.org/showthread.php?t=490937)

That's not going to be very helpful.  If you annoy them enough, they may discontinue the whole project.  Either way, they do not want to hear from end users, they want to hear from developers.

---

