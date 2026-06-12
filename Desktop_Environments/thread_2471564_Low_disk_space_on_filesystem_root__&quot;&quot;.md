---
title: "Low disk space on filesystem root  &quot;/&quot;"
date: 2022-02-03
forum: Desktop Environments
---

### Post by sgxnew54 on 2022-02-03
Hello evrybody,


I have Ubuntu 20.04.3 LTS in dual boot with Windows 10 on HP Prodesk 400 G, with 250 GiB SSD and 8 of RAM, and for some time when I open the PC I get a message like "Low disk space on root filesystem". the root partition is 16.75 GiB. I then uninstalled some packages that [/COLOR][/SIZE][COLOR=#000000][SIZE=4]I didn't use frequently, gaining something by bringing the free space back to 2.24 GiB. I would like to increase the root partition "/" with GPARTED anyway so I shrunk the windows partition (I have dual boot) gaining 3 GiB of space (unlocated) which I would like to add to the root partition which is adjacent, it comes just after so as to bring it to about 20 GiB but GPARTED does not allow me I have tried in all ways.

Please can you help me .

Thanks in advance
Sandro

---

### Post by yancek on 2022-02-03
You need to use GParted from a 'live' system like a USB.  If you try using GParted on the installed system, it will fail because mounted partitions can't be modified/  If you move the / (root filesystem partition) to the left, you will be moving the boot files and you will get a warning message about that from GParted.  I would think it would be easier to delete the swap partition and add some of that space to the / partition and create another smaller swap partition.  Ubuntu by default uses a swap file so you don't really need a swap partition.

---

### Post by oldfred on 2022-02-03
+1 on yancek's suggestions.

I would totally delete swap, but you have to comment out  ( # ) swap line/entry in fstab first.
And have to use live installer. 
Somewhat difficult to create file, but relatively easy to just shrink /home &  add new 4GB swap partition. 
Then after rebooting add new UUID of new swap back into fstab & uncomment swap line.

---

### Post by sgxnew54 on 2022-02-04
[COLOR=#202124]Hello ,[/COLOR]
[COLOR=#202124]from USB Live with Gparted I deleted the swap partition and increased the root partition with the space freed up. While processing almost at the end gparted gave an unidentified error message, undo was not allowed, so I closed gparted and updated the / etc / fstab file by commenting (#) the deleted swap partition and logged out from live usb ubuntu.[/COLOR]
[COLOR=#202124]Then login from ubuntu system on PC, ubuntu booted normally but checking with gparted the new partitions the root / one did not increase the available space (unused 2.15 GiB). I don't understand what happened, you have some ideas.[/COLOR]

[COLOR=#202124]I attach the situation of the partitions after the modification.[/COLOR]

---

### Post by oldfred on 2022-02-04
See this, I have never needed it, & thought gparted ran it as part of a partition resize.
man resize2fs

Again run from live installer.
sudo resize2fs /dev/nvme0n1p5

---

### Post by sgxnew54 on 2022-02-05
Hello,
thanks , now I resized the root partition as I wanted , but  I can't create the swap partition with gparted live is there another way ? I would like to use the 3.14 GiB unallocated for the swap. look the attached.

---

### Post by yancek on 2022-02-05
Check the Ubuntu documentation at the site below.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by sgxnew54 on 2022-02-05
Hello,
ok all done . swap partition created, thanks for your support.

---

