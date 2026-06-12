---
title: "downloading new desktop environments"
date: 2008-01-09
forum: Desktop Environments
---

### Post by adamj575 on 2008-01-09
hi im interested in downloading different desktop environments to try them out. from past experience i know that if i download the kde desktop i wind up with a bunch of programs i dont want or need. what all extra comes with xfce? is there anyway to download fluxbox and is there anyway to get kde without all the extra software? again i just want to experiment. i am very happy with my customized gnome desktop :)

---

### Post by dlegend on 2008-01-09
I installed XFCE on top of GNOME and KDE and it doesn't really add many applications to the menu. Fluxbox doesn't add anything to the menu also. For installing different DEs check out this site with an easy to follow tutorial: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Also, if you want to clean up your GNOME/KDE menus you can use this:

[http://programming-designs.com/linux/menu-cleaner.sh](http://programming-designs.com/linux/menu-cleaner.sh)

It will modify the .desktop file for each application so they will show up only in their DE (ie. GNOME apps only show up in the GNOME menu and KDE apps in KDE's menus).

I got the menu cleaner script from this site: [http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/](http://ubuntu-tutorials.com/2007/07/18/removing-kde-icons-in-gnome-remove-gnome-icons-in-kde/)

However, they no longer have the script hosted there (or last time I checked) so I uploaded it to my site for people to use.

Hope this helps! If you have any more questions, feel free to ask.

---

### Post by Tenken on 2008-01-10
Instead of installing the whole kubuntu-desktop, you could just install kdebase, it is in the repos along with fluxbox.

---

### Post by rjmdomingo2003 on 2008-01-10
If you are keen on using fluxbox, look at this: [http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+menu](http://ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+menu)

---

### Post by urukrama on 2008-01-10
Don't install the kubuntu-desktop or xubuntu-desktop packages. As suggested earlier, go for the kde-base and xfce4 packages. They just contain the desktop environment, without all the added extra applications, and you will get a faster kde/xfce.

For Fluxbox, rjmdomingo already gave you the best guide on these forums. For IceWM, use [aysiu's guide]("http://psychocats.net/ubuntu/icewm"). For Openbox or Pekwm, have a look at the links in my signature.

---

### Post by adamj575 on 2008-01-10
I cant seem to find any desktop environments in the repositories???????? ive searched and it keepd showing up no results found.

---

### Post by urukrama on 2008-01-12
What search terms did you use?

Also, make sure you have all the proper repositories enabled. You will need the 'universe' repositories. In Synaptic, go to Settings > Repositorie and tick the right boxes. Or edit the /etc/apt/sources.list file and uncomment the repos you want to include (remove the # before the right line).

It could also be that your repositories list is corrupted (I've had a similar problem in tha past). You will need to get a new source list then. To do so, try [this website]("http://www.ubuntu-nl.org/source-o-matic/").

---

