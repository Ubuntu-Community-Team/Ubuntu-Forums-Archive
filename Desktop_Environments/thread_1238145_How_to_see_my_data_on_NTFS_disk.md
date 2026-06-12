---
title: "How to see my data on NTFS disk?"
date: 2009-08-12
forum: Desktop Environments
---

### Post by alain_sat on 2009-08-12
Hi,

I'm using Ubuntu 9.04 and started with 8.04 more than a year ago.
I became familiar with the gnome environment but are for sure no Linux guru.

I'm trying to setup a so called HTPC (more than 1 year).
I had results under Windows but don't want it for many reasons.

The howto I'm trying to follow is starting from Xubuntu.
I tried allready with a few versions of Ubuntu but at a certain point allways get stuck.

I have 1 partition NTFS called Data (just imagine why).
Another with Ubuntu 8.10 with another trial and made a fresh one with Xubuntu9.04 under ext3.

My first problem is that I nedd to see my data partition and also my 8.10 partition. Under Ubuntu I never had problems (neither on this Triple-eee with Easy Peasy updated 8.10) I just once have to key in the sudo pass for that partition and say remember it and find the data folder under places.

But in Xubuntu I don't find this partition neither the other Ubuntu.

The other problem I had was that my HDMI output didn't work anymore untill I rebooted under another partition.
Having 2 screens give me also problems as they only clone and that is not what I want.

I'm sure someone out there will tell me how to do and maybe just by creating a symlink on the command line.

Thanks 

Alain (want to get rid of Windows but it is difficult)

---

### Post by alain_sat on 2009-08-12
I found [THIS]("http://ubuntuforums.org/showthread.php?t=966174&highlight=acces+ntfs") and also someone who's going to change my /etc/fstab so it's mounted at startup.

---

### Post by oldfred on 2009-08-12
This is the info on fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

This was my entry in fstab to read my c: drive .  I had to make the directory first as a mount point. I hand edited from sda1 to use the UUID.

# before uuid  /dev/sda1 /media/cdrive ntfs-3g defaults,locale=en_US.UTF-8 0 0
UUID=04B05B70B05B6768 /media/cdrive ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

