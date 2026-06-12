---
title: "How do I modify this script for 9.04?"
date: 2009-05-09
forum: General Help
---

### Post by theozzlives on 2009-05-09
```
#!/bin/sh

# Copyright 2008 - Created by Lance of http://www.pendrivelinux.com
echo "############# USB INSTALLER SCRIPT #############"
echo
echo "This script can be used to create a Ubuntu 8.10"
echo "Persistent USB flashdrive from a 2GB+ USB drive."
echo 
echo "================================================"
echo "================= WARNING! ====================="
echo "================================================"
echo
echo "This USB installer script is being offered AS-IS"
echo "for FREE and comes with absolutely no warranty."
echo "Proceed at your own risk."
echo
echo "If you agree, press Enter to continue..."
read p 
clear
echo "================================================"
sudo fdisk -l
echo
echo "=========== Locate your flash drive ============"
echo
echo "Please locate your flash drive from the list of"
echo "devices displayed above and enter it's letter."
echo
echo "For example, if your flash drive is /dev/sdx,"
echo "you would type x and then press Enter"
echo
echo "What is your drive letter?:"
read X
Y="1" 
Z="2"
sleep 1
clear
echo "=========== Creating the partitions ==========="
echo
if sudo [ -b /dev/sd$X$Y ]; then
sudo umount -f /dev/sd$X$Y
else
echo "dev/sd$X$Y is ready"
fi
sleep 1
if sudo [ -b /dev/sd$X$Z ]; then
sudo umount -f /dev/sd$X$Z
else
echo "dev/sd$X$Z is ready"
fi
sleep 1
sudo parted -s /dev/sd$X rm 1
sudo parted -s /dev/sd$X rm 2
sleep 1
sudo parted -s /dev/sd$X mkpart primary fat32 0 50%
sleep 1
sudo parted -s /dev/sd$X mkpart primary ext2 50% 100%
sleep 1
sudo parted -s /dev/sd$X set 1 boot on
clear
echo "============ Creating filesystem ============"
echo
sudo umount -f /dev/sd$X$Y
sleep 2
sudo mkfs.vfat -F 32 -n ubuntu8 /dev/sd$X$Y
sleep 2
sudo umount -f /dev/sd$X$Z
sleep 2
sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sd$X$Z
clear
echo "============ Stage 1 completed =============="
echo
echo "Please remove and reinsert your flash drive." 
echo "Wait for the mounted partitions to appear on" 
echo "your desktop, and then press Enter to continue"
read p
clear
echo "===== Stage 2: creating the portable USB ===="
echo
echo "Moving on to create the portable system."
echo
# if sudo [ -d /media/casper-rw ]; then
# echo "Directory casper-rw is ready"
# else
# sudo mkdir /media/casper-rw
# sudo mount /dev/sd$X$Z /media/casper-rw
# fi
# sleep 1
# if sudo [ -d /media/ubuntu8 ]; then
# echo "Directory ubuntu8 is ready"
# else
# sudo mkdir /media/ubuntu8
# sudo mount /dev/sd$X$Y /media/ubuntu8
# fi
sudo apt-get install syslinux -y
sleep 3
sudo syslinux -f /dev/sd$X$Y
sleep 2
cd /cdrom
echo
echo "Now copying files to your flash drive." 
echo "Please wait..."
echo
cp -rf casper dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines install/mt86plus /media/ubuntu8
sleep 1
cd /media/ubuntu8
sleep 1
sudo cp isolinux.cfg syslinux.cfg
sleep 1
sudo rm text.cfg
sudo wget pendrivelinux.com/downloads/u810/text.cfg
sleep 1
clear
echo "=========== Stage 2 completed ============="
echo
echo "All finished, your flash drive is now ready"
echo "Press Enter to close this window..."
read p
```

---

### Post by StOoZ on 2009-05-09
what errors do you get when you run it on 9.04?

---

### Post by -kg- on 2009-05-09
> **StOoZ said:**
> what errors do you get when you run it on 9.04?

You shouldn't get any errors; it's just that the bash script is written to deal with Intrepid only.

I am no programming expert, so I went to the site.  Do you have Windows on your computer?  If so, then [this page]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/") has instructions in setting up a persistent Flash install for Jaunty.

Otherwise, I'm guessing that no one has written such a bash script for Jaunty yet.  Perhaps someone more familiar with programming a bash script will come along and assist you, but if you have Windows on your computer, that would get you going now.

---

### Post by theozzlives on 2009-05-09
> **-kg- said:**
> You shouldn't get any errors; it's just that the bash script is written to deal with Intrepid only.

I am no programming expert, so I went to the site.  Do you have Windows on your computer?  If so, then [this page]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/") has instructions in setting up a persistent Flash install for Jaunty.

Otherwise, I'm guessing that no one has written such a bash script for Jaunty yet.  Perhaps someone more familiar with programming a bash script will come along and assist you, but if you have Windows on your computer, that would get you going now.

I get a couple errors at the end, no I have Windows in a VirtualBox, but not on a partition.

---

### Post by Rhubarb on 2009-05-09
I'm sure Ubuntu 8.10 has a menu item that'll do this all for you without having to use a script.
System --> Administration --> Create USB Start Up Disk (or something similar).

In Ubuntu 9.04, it can be found here:-
System --> Administration --> USB Startup Disk Creator

Both 8.10 and 9.04 allows you to make persistent live USB install from an Ubuntu ISO of either 8.10 or 9.04

Or you can run the app with this command in a terminal:
```
usb-creator
```

---

### Post by theozzlives on 2009-05-10
> **Rhubarb said:**
> I'm sure Ubuntu 8.10 has a menu item that'll do this all for you without having to use a script.
System --> Administration --> Create USB Start Up Disk (or something similar).

In Ubuntu 9.04, it can be found here:-
System --> Administration --> USB Startup Disk Creator

Both 8.10 and 9.04 allows you to make persistent live USB install from an Ubuntu ISO of either 8.10 or 9.04

Or you can run the app with this command in a terminal:
```
usb-creator
```

that way the casper is in a file, I want it in its own partition.

---

