---
title: "Creating Swap file on media"
date: 2009-01-31
forum: General Help
---

### Post by Asheboy on 2009-01-31
So I have a partition, 10gb for the OS and stuff and then 140gb for files such as movies. I want to make a swap file (since I didn't create a swap partition) but have it in my 140gb partition. Is this possible since I have only seen tutorials on making a swap file in the root file system?

---

### Post by taurus on 2009-01-31
Technically, you can boot your machine with either Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php), then shrink your 140GB partition, making room to create a new swap partition with it.  Once you have format it go swap, reboot your machine and edit /etc/fstab to add an entry for swap.

---

### Post by HermanAB on 2009-01-31
It is trivial to make a swap file and it is the same speed as a swap partition:
$ man swapon

Cheers,

Herman

---

