---
title: "loading more than one desktop"
date: 2009-07-31
forum: Desktop Environments
---

### Post by davethewave83 on 2009-07-31
I installed Ubuntu for my mom, but decided to use xubuntu by installing it within ubuntu using the package manager. When the desktop loads, the old gnome desktop appears with the old wallpaper and icons,then it is overlayed by xfce. How do i stop the original profile from loading first?

---

### Post by XubuRoxMySox on 2009-08-01
I assume you installed XFCE using synaptic or ```
sudo apt-get install xubuntu-desktop
```

After installation, make sure you don't have automatic login enabled (it is normally not enabled anyway).

Log out, and when you go to log back in, choose Options>Session and select XFCE for that login session.

You may install as many desktop environments as you like in Ubuntu to compare them, and remove the ones you don't. Some are pretty, some are slow, some are rich in effects and "eye candy," and some are super-quick lightweight simplicity (see my sig).

At each login, Options>Session to choose which d.e. you want to use for that session.

Hope that helps,
Robin

---

### Post by davethewave83 on 2009-08-01
> **dixiedancer said:**
> I assume you installed XFCE using synaptic or ```
sudo apt-get install xubuntu-desktop
```

After installation, make sure you don't have automatic login enabled (it is normally not enabled anyway).

Log out, and when you go to log back in, choose Options>Session and select XFCE for that login session.

You may install as many desktop environments as you like in Ubuntu to compare them, and remove the ones you don't. Some are pretty, some are slow, some are rich in effects and "eye candy," and some are super-quick lightweight simplicity (see my sig).

At each login, Options>Session to choose which d.e. you want to use for that session.

Hope that helps,
Robin

Thanks, this is how it was done but it just went all wonky. On the next reboot it did the same thing (loading gnome desktop then xfce on top) but the xfce bar was all distorted, the time, power and other buttons were no longer in the right corner but instead all squished to the left in an ugly way, then firefox stopped working correctly. Firefox could load but buttons like the search button and hyperlinks failed to do anything, they wouldn't even try to work they'd just depress and do nothing. 

I just put windows back on it for her, it would seem that I messed it up by installing xfce over gnome:confused: I thought this was something that was able to be done. 

Also it did not install drivers for her intel extreme graphics integrated video anyways so perhaps it is for the best. 

I feel like such a failure :(

*edit*
another thing that was noted was that the desktop resolution in Xubuntu would not save it's state. It would be set to 800x600 and change it's self back to a higher resolution the next reboot. 

The xorg.conf had to be edited to tell it to keep 800x600.
also it was not auto-mounting the secondary partition (NTFS) at boot but this was an easy fix by adding it to the fstab

---

### Post by Dullstar on 2009-08-01
Now that's abnormal...

---

### Post by GolemdX on 2009-08-01
On a side note, the website [http://www.lxde.org/](http://www.lxde.org/) doesn't seem to be loading for me.

---

### Post by XubuRoxMySox on 2009-08-02
Wow that is weird. I wish I could explain that. If it's a new installation anyway, maybe a fresh install would fix it.

The lxde site seems to be down for a few days. A little advance warning would have been nice (if this was expected), lol. **But it's available in Ubuntu's repositories** and sets up a *very* lightweight (much lighter even than Xfce in fact), almost "Windowsy" desktop (people say it reminds them of Win 98 ).

You put icons on the desktop just by dragging them from the File Manager (PCManFM) to the desktop, or put 'em in the taskbar.

I use it because all the Windows users who share this computer can do so effortlessly with all the simplicity of a familiar desktop with "clickable" icons. And because it's so super lightweight, it runs superbly on older computers.

Your issue might be just a bad installation that might be fixed with a fresh install. 

-Robin

---

### Post by Dullstar on 2009-08-02
Although the purpose of LXDE does not appear to be to make a main desktop environment.

---

