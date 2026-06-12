---
title: "Openbox dependency - xorg vs xinit"
date: 2013-04-06
forum: Desktop Environments
---

### Post by PeterTaps on 2013-04-06
Folks,

I have built a minimal Ubuntu 12.10 system. Now, I need to install openbox on it. As I understand, I need to first install Xwindow system before installing openbox. I am confused if I should install package xorg or package xinit.

There also seems to be another package called xorg-xinit. 

Although installing xorg seems to work, I am wondering if xinit or xorg-init is sufficient to start openbox.

Thank you in advance for your help.

Regards,
Peter

---

### Post by Helkaluin on 2013-04-06
The xorg package depends on the xinit package, at least in Raring.

The xorg package is a metapackage that pulls in all the relevant X stuff.

xinit is used to start xorg without a display manager (e.g. LightDM, GDM, KDM, SLiM).  With xinit you start xorg from a tty by typing startx.

---

### Post by ibjsb4 on 2013-04-06
I say just go ahead and install it.  You have xorg installed it should pull in any other needed packages.  Are you using as DM?

---

### Post by PeterTaps on 2013-04-06
Thank you all for your help.

My intention is to keep my box as lightweight as possible. If xinit is lighter than xorg and the only difference is that I have to type "startx," looks like xinit is what I need. Is this right?

I also am wondering if I need a DM to get Openbox to work.

I guess I can ask my question in a slightly different way.

On an Ubuntu minimal box that does not have any x-thing installed (xorg, xinit, etc.), if I just "apt-get install openbox," will it automatically pull in whatever x-thing is needed to make it run? I guess this would be the best way to go about doing it.

Thank you in advance for your help.

Regards,
Peter

---

### Post by ibjsb4 on 2013-04-06
If you install "lightdm" it will pull in xorg.

If you install "slim" you need to install xorg.

Openbox is not a DM.

---

### Post by Irihapeti on 2013-04-06
My experience with installing openbox from a minimal install: you have to install xorg AND openbox. Installing openbox doesn't automatically pull xorg in as a dependency.

Xinit is something separate. Unless it also installs xorg, it won't give you a graphical desktop. The main reason for installing it is so that one can use startx from a tty.

---

### Post by PeterTaps on 2013-04-07
Thank you all for your help. Looks like I must always install xorg first before installing openbox.

Regards,
Peter

---

