---
title: "Black screen after running apt-get update"
date: 2011-08-02
forum: Desktop Environments
---

### Post by SuperGauntlet on 2011-08-02
Ok, so heres my situation:

I got sick of unity yesterday and tried to install Gnome3. While doing this, i ran apt-get update. I believe that this updated my xorg to 1.1+ (or whatever) making it incompatible with the proprietary ATI drivers I'm running. So I tried a whole bunch of stuff, from reinstalling the drivers from the ttyl1 prompt, to doing startx from the command line and using synaptic to remove the proprietary drivers and install radeon, etc, etc.
I think the issue right now is that there are bits of the proprietary driver left that are messing with the open source driver. Whenever I do startx, i get artifacting all over the screen, which never seems to go away.

Any ideas?

---

### Post by wildmanne39 on 2011-08-02
Hi, more then likely it is a problem with gnome3 being installed here is a link to look at.
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

---

### Post by SuperGauntlet on 2011-08-02
> **wildmanne39 said:**
> Hi, more then likely it is a problem with gnome3 being installed here is a link to look at.
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

Do you have a good alternative DE? I'm not particularly attached to GNOME.

---

### Post by wildmanne39 on 2011-08-02
Hi, xfce or kde are good.

Are you able to get past grub or is the black screen s soon as you try to boot?

If it is caused by gnome3 you will need to try to fix it or reinstall.

---

### Post by SuperGauntlet on 2011-08-02
> **wildmanne39 said:**
> Hi, more then likely it is a problem with gnome3 being installed here is a link to look at.
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)

ALSO: now i can't even do startx from the command line. it attempts to start, but does not work after it is unable to find any screens.

---

### Post by SuperGauntlet on 2011-08-02
I'm able to get past GRUB and the screen goes slightly purple, but then it either goes blue (my monitor showing no input) or completely black. Then when I hit ctrl+alt+del twice, it shows the ubuntu shutting down splash - with the dots and everything.

So I don't think it's Gnome.. But it could be.

---

### Post by SuperGauntlet on 2011-08-02
Alright, now what I've done is reinstalled x.org and x.org core, and then reinstalled the radeon Open Source driver. This still doesn't work. 

Also, I'm pretty sure it's not Gnome as I can get to the desktop from the ttyl prompt by running 'startx.'

---

### Post by wildmanne39 on 2011-08-02
Hi, ok you may have had an update to your video card driver that is the most likely thing if it is not gnome3.

You can try to set nomoeset parameters to allow you to boot ubuntu so you can check your video driver, here is a link for that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Duncan Williams on 2011-08-03
Don't know if this is relevent to your situation, but.
A week or so ago I did a general update in update manager.
amongst other updates was the new kernel update
**linux 2.6.38-10-generic**

This mangled my nvidia driver installation and I ended up having to re-install my system.
[http://peppermintos.net/viewtopic.php?f=9&t=3893](http://peppermintos.net/viewtopic.php?f=9&t=3893)

---

