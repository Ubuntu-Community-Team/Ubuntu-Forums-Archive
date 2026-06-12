---
title: "Intrepid: Need help with dependency"
date: 2009-02-01
forum: General Help
---

### Post by Nukinfuts on 2009-02-01
Hello all! First time posting here, been using Ubuntu for almost a year now, and i love it. Thank you to everyone who contiues to develop and support it everyday.

So my issue. I did a search on this and only found one thread that referred to the issue. I am, for the first time, dual booting vista and ubuntu for various reasons. Anyway i installed wubi because i dont have any cdr's or anything.

I am now trying to install lvpm so migrate wubi to its own partition and go full install with it. The error is "dependency not satisfied: os-prober". After some google work i found the following link:

[http://packages.ubuntu.com/source/intrepid/debian-installer/os-prober](http://packages.ubuntu.com/source/intrepid/debian-installer/os-prober)

Now i downloaded the last two files to my flash drive, because the linux side of my computer has no internet. All i have is my blackberry and linux doesnt like my blackberry. And i havent got around to airhack yet. 

So i need to install this manually, and i have absolutely no idea how. I cant seem to find a how to anywhere, can someone give me a hand?

Thanks in advance!

---

### Post by p_quarles on 2009-02-01
Well, I'm not familiar with this package or with the procedure you're attempting, so my answer is limited to one aspect of this: how to download and install dependencies without the target computer being connected to the internet. 

First of all, the link you gave is to the source code for that package. It would be easier to get the pre-built binary: 
[http://packages.ubuntu.com/search?keywords=os-prober&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=os-prober&searchon=names&suite=all&section=all)

Select your Ubuntu version (8.04, 8.10, etc) and architecture (if you aren't sure, go with i386) and download the package. You will then need to transfer it to your home directory on the current Ubuntu installation. Once you have done that, you can install it by running:
```
sudo dpkg -i packagename.deb
```
Obviously, the "packagename" part should be replaced with the exact name of the file you downloaded, which will vary depending on the version and architecture you have. 

After that, you may still find that lvpm has further dependencies, but you should be able to get them following the same procedure. Just remember to search packages.ubuntu.com, rather than Google.

---

### Post by Nukinfuts on 2009-02-01
thanks i will give that a try now

---

### Post by Nukinfuts on 2009-02-01
Ok that worked perfect. It's a deb so i just ran it and everything installed fine. Now i have a new issue....

LVPM moved ubuntu from sda1 (primary, contains vista, ntfs) to sda2 (ext). I have sda3 setup as a swap. It installed the grub loader, and told me to boot and choose ubuntu.

When i rebooted and chose ubuntu from grub, it said "Could not mount partition" and took me back to grub. None of the options work except for vista. Ubuntu either says failed to mount or file not found.

When i choose vista the windows boot manager comes up and shows vista and ubuntu, which i assume is normal because it did that before. I just have to set that not to show up.

But how do i fix the mount issue with grub?

---

### Post by p_quarles on 2009-02-01
I would first try reinstalling GRUB, using a tool such as this:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You can also reinstall GRUB using the Ubuntu live disk, but this disk makes it a bit easier and smoother. 

If reinstalling GRUB doesn't work, it's likely the problem is actually with filesystem on the sda2 partition, but hopefully that won't happen.

---

### Post by Nukinfuts on 2009-02-02
Is there a way to boot supergrub from a flash drive? i dont have any cdr's and the less money i spend the less my other half will yell at me :x

I have a livecd, but its shot and doesnt work right.

---

### Post by Nukinfuts on 2009-02-05
Just an update i found the instructions to load SGD to usb, worked like a charm.

Thanks!

---

