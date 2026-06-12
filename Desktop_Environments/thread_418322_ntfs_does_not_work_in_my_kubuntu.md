---
title: "ntfs does not work in my kubuntu"
date: 2007-04-22
forum: Desktop Environments
---

### Post by bro on 2007-04-22
Hi, 
I have kubuntu feisty installed on my laptop. It has a ntfs partition which it does recognize and which I can read and write. But the external ones don't work. Only gparted notices that it is there and can't tell me anything about the drive. It's an external usb harddrive. Gparted also says it can't find the mountpoint for the drive that does work. 

I installed 
> 
sudo aptitude install ntfs-3g
sudo aptitude install ntfs-config


both are installed, laptop has rebooted, but it doesn't work, after enabeling the write support it just doesn't mount my hd (not even after reboot). 
gparted tells me: 'unable to find mount point'.

Anybody has a solution?

---

### Post by rich.bradshaw on 2007-04-22
Did you hibernate Windows? If you did then you can't read the partitions.

Reboot into Windows, shut it down, then into Ubuntu and I bet you 300 pizzas it will work!

---

### Post by bro on 2007-04-22
300 pizza's.. that's great, it means I won't have to cook for a year.. 

I didn't hibernate windows, it did ask for a reboot before, so I rebooted into windows. Problems there are none. 
My internal hd has a ntfs partition which is recognized. Gparted says it cannot find the mount point though, but it's actually mounted at /media/sda1. 
My external hd gets only the ext3 & fat32 partitions recognized. The others Gparted asks me if I 'installed the correct plugin for this filesystem' and that's it. 

anybody has clue? There's data on that partitions i'd like to work with under ubuntu... I can give you about 298 pizza's for the solution ;)

---

