---
title: "Problems with Infinality and Ubuntu GNOME 14.04"
date: 2014-04-22
forum: Desktop Environments
---

### Post by plazman30 on 2014-04-22
I am on my 4th re-install of Ubuntu GNOME 14.04.  I've narrowed down my problem to Infinality.  I enable the Infinality repo from:

[https://launchpad.net/~no1wantdthisname/+archive/ppa](https://launchpad.net/~no1wantdthisname/+archive/ppa)

I install their updated freetype and config utility.

I then reboot and the machine hangs with the monitor off.  I put the machine to sleep, wake it up and get a low graphics mode error.  I can't get the machine to even boot to a terminal.

Anyone else seen this?

---

### Post by Pureness on 2014-04-26
Yeah, same here with 14.04 gnome too
I have to hardware reboot
On grub, go to Advance boot option
Choose the entry with recovery mode
Mount your partition as rw: 'mount / -o readwrite,rw'
and purge infinality: 'apt-get purge fontconfig-infinality'
then 'reboot now'

I'm gonna try to build infinality from sources, and check if it will work

---

### Post by buzzingrobot on 2014-04-26
Infinality itself has seen little or no activity for at least several months.  The code at the site was, I believe, last patched for freetype 2.4.12.  Freetype in 14.04  is at 2.5.2. Meanwhile, the PPA uses a patched freetype from the Arch user repository. (That, in my experience, works very well on Arch.)

Meanwhile, some elements of the Infinality patches have been incorporated into freetype.

You might take at look at what the Arch dev says on on his Github page: [https://github.com/bohoomil/fontconfig-ultimate](https://github.com/bohoomil/fontconfig-ultimate).  There is also a long thread on the Arch forum:  [https://bbs.archlinux.org/viewtopic.php?id=162098](https://bbs.archlinux.org/viewtopic.php?id=162098).

As I recall, Infinality puts "infinality-settings.sh" in /etc/profile.d where it executes on each restart.  Config files are in /etc/fonts/infinality. However, one of the selling points of that Arch variation is that no user config is required.

---

### Post by Pureness on 2014-04-28
Try building the sources, but doesn't work either.

---

### Post by jmkowske on 2014-05-19
I installed infinality a few days ago from the repo above and I am currently upgrading from 13.10 to 14.10 ( packages are installing as I write this ) -- should I expect to encounter this issue when the machine reboots? I have rebooted since the install and haven't had a problem yet... 

Should I remove the package while the installer is running? That okay to do?

edit: I should add I'm not using the Gnome environment, jsut straight up 13.10 Ubuntu -- maybe I should start a new thread.

---

### Post by jmkowske on 2014-05-19
Fyi, the 13.10 -> 14.04 upgrade provided no problems for infinality. I re-enabled the ppa after upgrade.

---

### Post by Kamyar on 2014-05-26
Just edit the file /etc/profile.d/infinality-settings.sh and change "SET_XFT_SETTINGS=true" to "SET_XFT_SETTINGS=false" . This is at line 49 for me. reboot and everything should work now.
BTW despite many of the patches being pushed upstream, infinality still provides a noticible difference and if properly configured, the best linux font experience.

---

