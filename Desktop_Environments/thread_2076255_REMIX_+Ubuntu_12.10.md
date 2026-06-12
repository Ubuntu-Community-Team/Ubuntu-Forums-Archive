---
title: "REMIX +Ubuntu 12.10"
date: 2012-10-25
forum: Desktop Environments
---

### Post by cbennett926 on 2012-10-25
Hello, is there a way I can install the Ubuntu Remix alongside Ubuntu 12.10? Like another desktop environment?

---

### Post by kansasnoob on 2012-10-25
Do you mean this:

[http://ubuntuforums.org/showthread.php?t=2073181](http://ubuntuforums.org/showthread.php?t=2073181)

If so the default Ubuntu DE (Unity) and the standard Gnome DE's (Gnome shell and Classic - no effects) do NOT coexist peaceably :(

There are just too many differences between the two desktop environments to be able to boot a standard Gnome DE or Unity simply by choosing one or the other from the login menu.

It may be possible to convert from one to the other but I suspect the amount of time involved would be much greater than simply installing the desired flavor from scratch which will then provide the devs desired outcome.

In fact Jeremy mentions something about that in the release notes:

> [Upgrade]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10#Upgrade")

It is strongly recommended to do a fresh install however if you prefer to attempt an upgrade instead, first upgrade to Quantal Quetzal 12.10. Then run the following commands:

    sudo apt-get install ubuntu-gnome-desktop ubuntu-gnome-default-settings 

(make sure to select gdm as default display manager when prompted)

    sudo apt-get remove ubuntu-settings

    Note that this will remove 'ubuntu-desktop' 

I think it would be much better to use either a VM or a multi-boot so you can boot into the desired OS. Of the two I much prefer an actual multi-boot. Virtual machines have always just baffled me :redface:

---

### Post by cbennett926 on 2012-10-26
> **kansasnoob said:**
> 
I think it would be much better to use either a VM or a multi-boot so you can boot into the desired OS. Of the two I much prefer an actual multi-boot. Virtual machines have always just baffled me :redface:

So just to clarify, I would make a new partition and use an install disc(USB) and during installation use the new partition?

---

