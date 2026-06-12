---
title: "Question about storage and install locations."
date: 2009-04-26
forum: General Help
---

### Post by Roasted on 2009-04-26
I loooove having Ubuntu on split partitions. Root on one partition, home directory on another. That makes upgrading Ubuntu each time with a fresh install easy by just making sure you don't format your home directory.

What if Ubuntu was super loaded with file size hungry games like Vista? Like if I were to load up a bunch of games on Ubuntu that were Ubuntu-native, where would they get installed?

I've just gotten into the habit of 20gb = root, remainder = home directory, that I was thinking... if games get installed on the root directory, I'd have to adjust my sizing of partitions accordingly.

What do you guys think? Where's the stuff get installed at?

---

### Post by linuxuser21 on 2009-04-26
I keep 1gb for /boot, 20gb for root, and the rest of that hard drive is /home and the other hard drives are free.
3rd party software and such are installed to your /home directory & are hidden.

---

### Post by Roasted on 2009-04-26
What's the advantage of having /boot on a separate partition?

When you talk about 3rd party software and whatnot being stored in hidden folders in the home directory, would that include Quake if I were to install the linux native version of that?

---

### Post by linuxuser21 on 2009-04-27
In case of system failure, it's nice to have /boot as a seperate partition.  Some distros also almost require it to be seperate because of LVM partitions.  I am also using RAID drives and it is suggested a lot to have a seperate /boot partition.
I think you can choose where you install Quake at.  Try this: [http://www.blog.highub.com/linux/install-and-play-quake-4-on-ubuntu/](http://www.blog.highub.com/linux/install-and-play-quake-4-on-ubuntu/)

---

### Post by Roasted on 2009-04-27
I've just never even thought of it because I have Super Grub on CD, which allows me to boot with the CD if my boot loader goes down and the CD can also reinstall Grub for me. So I just never gave it a second thought.

---

