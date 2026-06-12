---
title: "This is weird..."
date: 2010-09-04
forum: Desktop Environments
---

### Post by SantaFe on 2010-09-04
I was running Ubuntu just fine, and GNOME still works correctly, my problem is I decided to once again to add XFCE so I could choose between the two upon boot up.  For some reason however, after running awhile, I'll notice I suddenly have a different wallpaper on the screen (the one I used in GNOME) instead of the different one I picked for XFCE.  Upon right clicking I find I have the GNOME right click menu (and can use the GNOME theme changer) instead of the XFCE right click menu.

Funny thing is, I still have the XFCE panel, and the rest of XFCE appears to work correctly, and it does work correctly if I reboot but then after awhile it sort of messes up again.

Is this just a bug of having XFCE4 & GNOME as Window managers?  It doesn't seem to mess up when I'm in GNOME, just in XFCE4 and even then it doesn't make XFCE4 unusable, just a minor quirk that I thought someone here might know how to correct.

Thanks! ):P


EDIT:  Found out it was Nautilus running in the background.  Stopped it & rebooted & problem went away. ;)  Now gotta figure out how it got started, as I was using Thunar, not Nautilus as my File Manager. ):P

---

### Post by azertyh on 2010-09-05
hi,
i am in the same case : ubuntu 10.04 and installed xfce (just the window manager) but gnome and xfce work.
my only problem under xfce is the right-click to umount devices.
how did you install xfce?

---

### Post by SantaFe on 2010-09-05
I Used Synaptic Package Manager & typed XFCE4 in the search box.  Then right clicked on the box opposite XFCE4 & chose Mark For Installation & apply.

Two other ways can be found here: [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

Or here: [http://www.howtogeek.com/howto/ubuntu/install-xfce-xubuntu-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-xfce-xubuntu-on-ubuntu-linux/)

---

### Post by SantaFe on 2010-09-05
Well I sort of fixed the problem by creating a new launcher on my panel called Fix XFCE & used this as the command: **killall -HUP xfdesktop**

Not an pretty way to solve the problem, but at least I don't have to reboot to fix it anymore.  Still wondering why GNOME doesn't want to leave XFCE alone desktop wise.:lolflag:

---

