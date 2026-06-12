---
title: "how do I install kde, xfce, and icewm and the other environments on ubuntu 5.10 Bree"
date: 2005-10-14
forum: Desktop Environments
---

### Post by kazuya on 2005-10-14
how do I install kde, xfce, and icewm and the other environments on ubuntu 5.10 Breezy. I have the development version not the newly released one, does doing an upgrade help in getting everything like the newly released version?

I was told one could have like boot up option to be like kde, gnome, icewm, or xfce?

How do this install?

Do I apt-get xfce, kde, and icewm at the same time. Is there a howto for this installations as well as a how to setup such that upon bootup or login, you have the option to select which environment, you desire to be in?

---

### Post by jasper_m on 2005-10-14
Upgrading will make your system exactly like the release (That's what I've heard...)

Yes, you can get them appear as startup options in Session menu in the login screen.

You'll probably have to uncomment some lines from your /etc/apt/sources.list. and run "sudo apt-get update"

then you'll just apt-get them and they apper magically in the Session menu:

sudo apt-get install kde-base  
or "sudo apt-get kde" if you want every single part of KDE that you'll never use anyway, ~450MB

sudo apt-get install xfce4

its probably

sudo apt-get install icewm

not sure about the name. try searching apt with "apt-cache search icewm"

Jasper Mattsson

---

### Post by Wolki on 2005-10-14
[QUOTE=jasper_m]
sudo apt-get install kde-base  
or "sudo apt-get kde" if you want every single part of KDE that you'll never use anyway, ~450MB [/quote]

You can also install "kubuntu-desktop". which will install KDE like it is after a default installation of Kubuntu.

If you don't want to install from the command line with "apt-get", you can also use synaptic, a graphical program to install software.

---

### Post by ygarl on 2005-10-14
That said - upgrading to Breezy with a NVidia card does trash the X server if you update to a new kernel, but that's a Linux and NVidia kernel issue, not a Breezy one. Just don't update the Kernel unless you're comfy fighting through the Nvidia driver/Kernel issue fun.

Still haven't gotten my new kernel working on my machine with a Gforce card (just booting to the old kernel). Ironically, the ATI (read: less compatable card apparently) machine runs quite perkily on the new kernel because the video driver doesn't tie itself into the kernel directly.

Isn't it ironic?

---

### Post by Wolki on 2005-10-14
[QUOTE=ygarl]That said - upgrading to Breezy with a NVidia card does trash the X server if you update to a new kernel, but that's a Linux and NVidia kernel issue, not a Breezy one. Just don't update the Kernel unless you're comfy fighting through the Nvidia driver/Kernel issue fun.[/quote]

Usually the update should take care of that. It can't, of course, for people who installed the drivers with the official nvidia method instead of synaptic. Switching to nv for the time it takes to reinstall the codec should work.

There were a few times during the Breezy development cycle when this happened, because a new kernel was available but the retricted modules not yet. this was usually fixed within a few hours. It should not exist on the stable release.

---

### Post by kazuya on 2005-10-27
what is the minimum hard drive requirement or size for installing ubuntu's gnome, kde, and xfce?

Is enlightenment an environment of its own as is gdesklets or could they be integrated in ubuntu's gnome environment?

---

### Post by taurus on 2005-10-27
I believe "xubuntu-desktop" will install xfce4 and all it plugins...  And enlightenment is just another window manager like xfce, fluxbox/blackbox, iceWM, etc.

---

### Post by kazuya on 2005-10-31
My bootup is incredibly slow. Does having xfce, kde, and gnome installed warrant such slowness in opening applications and system bootup?

Even when I had other linux distros, it was not close to this slow?

---

### Post by andlinux21 on 2005-10-31
I installed xfce4 on a fresh Breezy system and everytime I try to use it (xfce4) it crashes GNOME runs excellent on my system however

---

### Post by flipkick on 2005-12-01
[QUOTE=Wolki]You can also install "kubuntu-desktop". which will install KDE like it is after a default installation of Kubuntu.
[/QUOTE]

This is not quite what I had to discover.

I deleted /.kde in my home folder

But I still can't get a clean DEFAULT installation of KDE on my ubuntu system. Languages are mixed, Desktop Setting are weird, it's really not like DEFAULT. So does anyone know how I would do a very CLEAN KDE installation on my existing Ubuntu 5.10 Install ?

Start off with "locate kde" an delete everything manually ?

...

---

### Post by GeneralZod on 2005-12-01
[QUOTE=kazuya]My bootup is incredibly slow. Does having xfce, kde, and gnome installed warrant such slowness in opening applications and system bootup?

Even when I had other linux distros, it was not close to this slow?[/QUOTE]

Having XFCE, KDE and GNOME *should* make practically no difference to boot-up speed.  I've always found Ubuntu slow to boot, full stop.

---

