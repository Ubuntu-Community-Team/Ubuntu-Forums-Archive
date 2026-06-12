---
title: "Want to try Kubuntu and Xubuntu."
date: 2009-09-03
forum: Desktop Environments
---

### Post by Slug71 on 2009-09-03
Ive been using Ubuntu for some time now and have a new Hard Drive  with some extra space on a spare system. Id like to try Kubuntu and Xubuntu and would like to know the best way to do this. 

I currently have Jaunty installed and was wondering if i should just install the other DE's from Synaptic and have the option to choose the DE at login or do seperate installs next to each other or if i could just set up separate /home partitions for the DEs.

If possible I'd prefer the last option?

---

### Post by ecmatter on 2009-09-03
> I currently have Jaunty installed and was wondering if i should just install the other DE's from Synaptic and have the option to choose the DE at login...Yeah, you can install the others via synaptic (or via terminal).

```

sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop

```Fair warning: the different desktops (kde especially) don't always play nice with one another.  It may take some tweaking to get them all to work (for instance, gmome-wm and gnome-panel both failed to load at startup on my system after adding gnome to xubuntu with kde already installed).

[re:/home]I don't think you can set up distinct /home partitions for each desktop.  If you mount a partition at /home, it'll be mounted at /home in all three environments.  You *could* set up three different user accounts on three different partiitions and use one exclusively for each desktop.  I don't know why you would want to do that, but it could be done.

---

### Post by XubuRoxMySox on 2009-09-03
You may install any or all of them you have room for. The trick is to select the Session you want when you log in.

Click the Options tab on the lower left corner of the Login screen and select either KDE or Xfce or Gnome (or any other wish to try - LXDE is available in the repositories and it's super-simple and very fast - even more lightweight than Xfce).

You can "mix and match" applications pretty freely regardless of which Session you choose. 

-Robin

---

### Post by Slug71 on 2009-09-03
> **ecmatter said:**
> Yeah, you can install the others via synaptic (or via terminal).

```

sudo apt-get install xubuntu-desktop
sudo apt-get install kubuntu-desktop

```Fair warning: the different desktops (kde especially) don't always play nice with one another.  It may take some tweaking to get them all to work (for instance, gmome-wm and gnome-panel both failed to load at startup on my system after adding gnome to xubuntu with kde already installed).

[re:/home]I don't think you can set up distinct /home partitions for each desktop.  If you mount a partition at /home, it'll be mounted at /home in all three environments.  You *could* set up three different user accounts on three different partiitions and use one exclusively for each desktop.  I don't know why you would want to do that, but it could be done.

How would i setup up different user accounts on separate partitions? Perhaps the best way to avoid conflicts as warned of earlier?

---

### Post by Slug71 on 2009-09-03
> **dixiedancer said:**
> You may install any or all of them you have room for. The trick is to select the Session you want when you log in.

Click the Options tab on the lower left corner of the Login screen and select either KDE or Xfce or Gnome (or any other wish to try - LXDE is available in the repositories and it's super-simple and very fast - even more lightweight than Xfce).

You can "mix and match" applications pretty freely regardless of which Session you choose. 

-Robin

Will try LXDE too, just a little worried about some of the sessions not playing nice with each other and possibly messing up my main Jaunty install. 

But if this is the best way then thats what i'll do.

---

### Post by ecmatter on 2009-09-03
> **Slug71 said:**
> How would i setup up different user accounts on separate partitions? Perhaps the best way to avoid conflicts as warned of earlier?

It won't help you to avoid conflicts.  All three (or four) desktops share the same root filesystem, and the root filesystem is where any conflicts will occur.  Unless you have a specific reason to add user accounts on separate pertitions, I wouldn't bother.  Purposeless clutter is never good.

---

### Post by XubuRoxMySox on 2009-09-04
> **Slug71 said:**
> Will try LXDE too, just a little worried about some of the sessions not playing nice with each other and possibly messing up my main Jaunty install. 

This is a lot simpler than you are making it! You can only log into one Session at a time. If a Gnome session, then you have the Gnome environment even if you are running KDE applications like the Konqueror web browser/file manager. There is no conflict! It's just that the KDE applications run *better* in the KDE environment than they do in Gnome.

Log out, choose another Session at login. Xfce uses a different file manager (Thunar) by default than Gnome or KDE or LXDE, etc. But you can still use any file manager you wish no matter what session you are logged in under. **It's only that some of the default applications of each environment are different.** Gnome's default file manager is Nautilis, KDE's is Dolphin, LXDE's is PCManFM, Xfce's default is Thunar. But if you wish to use PCManFM in Gnome, you still can! But it may not work as well as the default. It's better to use the environment's default applications. 

No need for separate drive partitions for each. But if you want to try them all on the same computer, just be sure you have room on your root partition.

-Robin

---

### Post by Slug71 on 2009-09-04
Cool, thanks guys.

---

### Post by Pianoman72 on 2009-09-04
Thanks for the tip on LXDE.

Versus XFCE on a p2 266mhz dell inspiron 3500 w/ 256 megs of ram, LXDE is a clear winner.  Much faster - love it.

---

### Post by XubuRoxMySox on 2009-09-04
> **Pianoman72 said:**
> Thanks for the tip on LXDE.

Versus XFCE on a p2 266mhz dell inspiron 3500 w/ 256 megs of ram, LXDE is a clear winner.  Much faster - love it.

That is what has made me such a rabid LXDE fanboy, lol. Its verrrrry small footprint and resource requirements and its super-simplicity. I've made mine "kid friendly" and it runs at near transwarp speed on an old low-end Dell!

Minimal Ubuntu+LXDE is awesome!

-Robin

---

### Post by mzzpxt on 2009-10-21
I believe the best way to "try out" any OS is what I have been doing - use Ubuntu 9.04 as base OS, keep it light, and use Virtual Box to create Virtual Machines of any OS you want to play with. Your virtual machines won't interfere with your Ubuntu installation and vice-versa. You would need lots of disk space, plus at least 2GB of RAM & a dual core CPU, but that's mainstream already and USB drives are pretty cheap now and VMs run fine off them, even 20GB - 40GB images.

---

### Post by raprap30 on 2009-10-21
May I know how to get some startup apps to only strat in a certain session e.g GNOME?

---

### Post by Paul41 on 2009-10-21
> **mzzpxt said:**
> i believe the best way to "try out" any os is what i have been doing - use ubuntu 9.04 as base os, keep it light, and use virtual box to create virtual machines of any os you want to play with. Your virtual machines won't interfere with your ubuntu installation and vice-versa. You would need lots of disk space, plus at least 2gb of ram & a dual core cpu, but that's mainstream already and usb drives are pretty cheap now and vms run fine off them, even 20gb - 40gb images.

+1

---

