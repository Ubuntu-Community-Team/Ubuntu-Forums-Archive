---
title: "monitor problem"
date: 2011-07-01
forum: Desktop Environments
---

### Post by bradpurvis on 2011-07-01
i installed a driver for my graphics card (nvidia 7300gt) and my primary monitor is not being recognized now. i have no panels on my second monitor and no icons. i need to fix this, any ideas?

---

### Post by bradpurvis on 2011-07-01
some help would be greatly appreciated. i don't want to reinstall over this

---

### Post by pjd99 on 2011-07-01
Before the changes, did your primary monitor display the icons/panels  etc? And was the desktop extended to the second monitor? (i.e. is the  second monitor performing as it was before?)

Can you access the nvidia-settings software to check the config?

Maybe try hitting Alt-F2 then entering:
```

gksu nvidia-settings

```You'll need to type your password as well.

If you cant see it on the working display and think the icons etc are showing on the display you cant see, hit Alt and try to drag it over from the non-viewable workspace.

Sounds like a configuration issue, maybe someone with more up to date knowledge on setting xorg.conf can help.

---

### Post by bradpurvis on 2011-07-01
i tried all of what you said, i hit alt+f2 and no window came up. i can't get my mouse to my other screen at all

---

### Post by pjd99 on 2011-07-01
For the moment, can you remove the nvidia drivers and revert to the open source ones.

Can you get to a terminal session by hitting CTRL+ALT+F1? if so, log in and perform the following (may not be 100% correct, depending on Ubuntu version)
```

sudo apt-get remove nvidia-current
sudo apt-get install xserver-xorg-video-nv        (should be there already)
sudo dpkg-reconfigure xserver-xorg -phigh
sudo /etc/init.d/gdm restart

```Might get you working again, but without 3D support till you can figure out what the problem is.

Old, but may be of use:
[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

---

### Post by bradpurvis on 2011-07-01
i ended up reinstalling :( my monitor still won't work and my secondary is primary now. unity now works for some reason too. i'm really confused

---

### Post by bradpurvis on 2011-07-01
now if i enable the desktop cube at all the tops of my windows disappear. what should i do about that?

---

### Post by wildmanne39 on 2011-07-02
> **bradpurvis said:**
> now if i enable the desktop cube at all the tops of my windows disappear. what should i do about that?Hi, you need to reset unity, click on unity and compiz reset in my signature and follow the instructions for resetting unity. To get the cube working in natty use this link.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.

---

