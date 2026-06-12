---
title: "format USB memory"
date: 2006-01-19
forum: General Help
---

### Post by cborge on 2006-01-19
I want to format my USB memory, and make three user partitions on it...
(It's just for testing, and to learn how to do it)

But when I try to 
sudo fdformat /dev/sda
I get this error:
> Could not determine current format type:

---

### Post by frodon on 2006-01-19
You could try gparted, it's a graphical tool to manage partitions, it's in the repositoties. It might be easy to use than command lines.

---

### Post by pizpot on 2007-09-01
Yes! gparted works but it took many tries and I had to umount and mount my usb stick before it would format. Let me explain...

I have a 2GB kingston usb memory stick and winxp and ubuntu 7.04. It is formatted fat. I had a file on it that I did not own and could not delete so I wanted to format the thing and start fresh. In windows I tried right clicking on it and formatting it, but the format window would just die and do nothing. So I went back to linux and tried deleting the file. No go. I even tried commands like

cd /media/KINGSTON
sudo rm -r filename

but it would not delete. So I installed gparted (sudo apt-get install gparted) (becareful you can format your drives if not thinking)

Then in gparted I changed to this device and clicked on the partition and deleted it. That worked, but it would not create a new file system. I got an invalid device name error I think it was. So I unmounted the device by right-clicking it on the desktop, unplugged it and plugged it in. Then re-ran gparted and this time it said it needed to create a msdos device name. That happened but it gave an error when I tried creating the partition. Then I tried again and it suddenly worked. I was able to create a fat32 and now all is well. Whew.

I am experienced, but this would be a chore for a newbie.

---

