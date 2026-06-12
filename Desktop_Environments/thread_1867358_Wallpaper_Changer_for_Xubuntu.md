---
title: "Wallpaper Changer for Xubuntu ?"
date: 2011-10-22
forum: Desktop Environments
---

### Post by Rodney9 on 2011-10-22
In Xubuntu 11.10 I have tried 'desktop nova' plus 'wallch', but neither work, they run but the wallpaper does not change.

Any clues ? or other way to change the wallpaper periodically in Xubuntu ?

---

### Post by gsmanners on 2011-10-22
There's an amusing thread on that subject: [http://forum.xfce.org/viewtopic.php?pid=23156](http://forum.xfce.org/viewtopic.php?pid=23156)

---

### Post by Rodney9 on 2011-10-22
Fixed Desktop Nova by adding the xfce module, thanks to Computer Bob at [http://www.computerbob.com/wp/fixing-desktopnova-on-debian-6021-xfce.php](http://www.computerbob.com/wp/fixing-desktopnova-on-debian-6021-xfce.php)

---

### Post by gsmanners on 2011-10-22
I see. Package bug. Interesting.

> A few seconds of detective work in the Synaptic package manager revealed the answer: Debian Squeeze Xfce had installed DesktopNova, but it had incorrectly installed only the desktopnova-module-gnome module package, which DesktopNova doesn&#8217;t use in Xfce, instead of the desktopnova-module-xfce module package that DesktopNova requires in order to work in Xfce.

I confirmed the problem by completely uninstalling and then reinstalling DesktopNova one more time.

And again, it incorrectly installed the Gnome module instead of the required Xfce module.

So I uninstalled the Gnome module, installed the Xfce module, and (in DesktopNova&#8217;s settings) selected the Xfce (xconf) 0.2 module.

Then I clicked on the button to restart the DesktopNova daemon.

And suddenly, the default Debian Xfce desktop wallpaper was gone and I was looking at a beautiful photo from my folder of desktop wallpapers.

---

### Post by stevehanler on 2011-10-28
I use Wally. Instructions for using it in xfce4 are here: [http://www.youtube.com/watch?v=i4Qd3zW0sk4](http://www.youtube.com/watch?v=i4Qd3zW0sk4)

---

