---
title: "Setting Up Xfce"
date: 2005-06-03
forum: Desktop Environments
---

### Post by tbrenner on 2005-06-03
Ello,

I was just wondering if anyone could help me setup Xfce?  I'm running a 233mHz laptop and a straight-foward GUI like Xfce would be great.  I'm really new to linux and would appreciate ANY help.  

Cheers.

 ](*,)   Me right now

---

### Post by bored2k on 2005-06-03
Method  (installs XFCE once on GNOME):
```
1. http://ubuntuguide.org/#extrarepositories
2. sudo apt-get update
3. sudo apt-get install xfce4
```

---

### Post by tbrenner on 2005-06-03
Do I need the internet for this to work?  I am currently not able to access the internet.  Is there anything I can download on my windows machine, burn to a disk, and install on the linux laptop if I do need a connection?

---

### Post by bored2k on 2005-06-03
Well yes you need internet, where else could you get it ?

Yes I suppose you could get them, but you need -every- dependency. Download the packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . I believe they should install correctly if you have GNOME installed. If you get any -packageX- needed during installation, get that package from the web (every package should display a list of needed dependencies on the packages website).

>   a2ps emacsen-common gtk2-engines-xfce libdbh1.0-1 libgtkhtml2-0
  libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3
  mousepad rox-filer xfcalendar xfce4 xfce4-appfinder xfce4-cpugraph-plugin
  xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins
  xfce4-mixer xfce4-mixer-lib-alsa xfce4-panel xfce4-session xfce4-systray
  xfce4-toys xfce4-trigger-launcher xfce4-utils xfdesktop4 xffm4 xfprint4
  xfwm4 xfwm4-themes


After you get those, the regular way is to type sudo dpkg -i for each package.. this can be tedious unless someone has a better plan.

---

### Post by psychicdragon on 2005-06-03
Xfce has a binary installer that you can use. Unfortunately it depends on some packages that may not be on the hoary cd (is there a list of all the packages on the cd anywhere?)

Required packages: 
libice-dev
libsm-dev
libgtk2.0-dev
libdbh1.0-dev

There's more information and a download link here:
[http://www.os-cillation.com/article.php?sid=43](http://www.os-cillation.com/article.php?sid=43)

This may be a little easier than the method bored2k suggested, I'm not to sure though.

---

### Post by pdk001 on 2005-06-03
i'm trying to install xfce right away

---

### Post by az on 2005-06-03
There are at least two projects similar to Kubuntu that are in the works for Breezy.  In the same way that Kubuntu is ubuntu with KDE, Xubuntu is aimed to be ubuntu with XFCE and there is also another project for low-end hardware... I forget the name...

You would get everyting you need on the cd...

---

### Post by cutOff on 2005-06-03
[QUOTE=azz]There are at least two projects similar to Kubuntu that are in the works for Breezy.  In the same way that Kubuntu is ubuntu with KDE, Xubuntu is aimed to be ubuntu with XFCE and there is also another project for low-end hardware... I forget the name...

You would get everyting you need on the cd...[/QUOTE]
Maybe E17buntu??

As Mark said at [Slashdot](http://interviews.slashdot.org/article.pl?sid=05/04/04/1859255&tid=90&tid=163&tid=160&tid=11) 

> I'm keen to see an XFCE-buntu too, so come along to #ubuntu-devel or #kubuntu on irc.freenode.net if you'd like to work on that. I'm also keen to see flavours of Ubuntu that are tuned for LTSP or embedded environments. And some folks were talking about Enlightenment E17 on Ubuntu too, so we may see a bunch of these flavours emerge for our next release, its up to the Ubuntu community. Ubuntu is, and always will be, entirely FREE in every sense, so it's a perfect playground for people to build on and innovate with.

---

### Post by psychicdragon on 2005-06-03
[QUOTE=azz]There are at least two projects similar to Kubuntu that are in the works for Breezy.  In the same way that Kubuntu is ubuntu with KDE, Xubuntu is aimed to be ubuntu with XFCE and there is also another project for low-end hardware... I forget the name...[/QUOTE]
This is news to my ears. After using Xfce for a while now I can see no reason to go back to Gnome. Sure the panel is slightly harder to configure, but once you have it looking the way you want it's a joy to use and _alot_ lighter than Gnome. The only thing I really miss is the menu bar.

---

### Post by bored2k on 2005-06-03
[QUOTE=psychicdragon]This is news to my ears. After using Xfce for a while now I can see no reason to go back to Gnome. Sure the panel is slightly harder to configure, but once you have it looking the way you want it's a joy to use and _alot_ lighter than Gnome. The only thing I really miss is the menu bar.[/QUOTE]
 Well you can have those by running gnome-panel.

---

### Post by psychicdragon on 2005-06-03
[QUOTE=bored2k]Well you can have those by running gnome-panel.[/QUOTE]
That is the last thing I would want to do right now. The Gnome panel is so slow to load and is generally unresponsive when compared to the Xfce panel. There are a lot of nice applets though.

---

### Post by Kyral on 2005-06-03
Try gDesklets if you want a new Menu Bar. It has a quite nice one, but the Applications thingy doesn't work yet

---

### Post by benplaut on 2005-06-03
[QUOTE=psychicdragon]That is the last thing I would want to do right now. The Gnome panel is so slow to load and is generally unresponsive when compared to the Xfce panel. There are a lot of nice applets though.[/QUOTE]

PyPanel is comming to mind... never tried it, but it looks cool

---

