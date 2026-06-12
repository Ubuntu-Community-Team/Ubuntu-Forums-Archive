---
title: "Xubuntu - Terminal doesn't work after reboot"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Trojan1313 on 2005-10-16
This is a Xubuntu related question. Since there isn't a forum for Xubuntu I figured the most logical place to put it was in Ubuntu, since it's based on Ubuntu. Was this the right way to do it? If not then please tell me what to do with Xubuntu related questions in the future.

Okay, now to the problem itself. I will first tell you how I installed xubuntu.
[Server install of Hoary]
sudo aptitude install lynx
lynx [www.ubuntuguide.org](www.ubuntuguide.org)
wget [http://www.ubuntuguide.org/sample/sources.list_upgradehoarytobreezy](http://www.ubuntuguide.org/sample/sources.list_upgradehoarytobreezy)
sudo mv sources.list_upgradehoarytobreezy /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install xubuntu-desktop
sudo aptitude install xdm
startx

When I started X i was directly thrown in to xubuntu, as planned. I installed the nvidia drivers with:
sudo aptitude install nvidia-glx
sudo aptitude install nivida-config (don't remember the name of this one exactly, it's the config tool for nvidia anyway)

and I installed leafpad using "sudo aptitude install leafpad", I think that's the only three programs I installed

Then I rebooted.

When the computer started the splash screen showed up, so that part worked. Then when I figured it would start xdm it just showed the nvidia logo (the one it show when you start x), and then I was thrown into the login prompt in bash.

When I had logged in using bash I used the lovely startx command again to get in to XFCE. It worked fine, or so it seemed. When I was going to open a terminal the [kaminix@xubuntu~] thing didn't show up, there's just a black unusable box with a white marker in it.

What should I do?

---

### Post by jimcooncat on 2005-10-21
Sorry I didn't notice your post before! I installed gdm and it worked well for me.  Setting up an old Compaq with 64 MB for a friend, it's slow but usable. Now I like hers so well I'm thinking of switching my own computer to Xfce!

---

