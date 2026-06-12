---
title: "Reformatting an external hard drive?"
date: 2009-05-30
forum: General Help
---

### Post by Sentience on 2009-05-30
I have a western digital passport external hard drive, but the format that its using only allows files up to 4gb. Is there a way to reformat it, using Ubuntu, to another linux/windows compatible format that is faster and allows for bigger files?

---

### Post by lindsay7 on 2009-05-30
Download Gparted from Synaptic. The newer versions of Ubuntu will read NTFS file so format it that way. Remember to right click the drive you want to work on and unmount so that you can work on it.

---

### Post by Mirages on 2009-05-30
[quote=lindsay7]The newer versions of Ubuntu will read NTFS file so format it that way.[/quote]

note NTFS is not compatible with all systems,.

I have a 120g Maxtor external drive that I have formatted into a few partitions of FAT32 because it is compatible with everything, it will work with all versions of windows, mac os, and linux. so if I am using a computer that is not my own and running something that isnt NTFS compaitble I can still read/write backup files to the external drive.

---

### Post by HermanAB on 2009-05-30
OK, here is how:

Install ntfs-3g and ntfsprogs.

Plug drive in, run dmesg to see the device name, e.g. sdc:
$ dmesg

Use fdisk to partition it:
$ sudo fdisk /dev/sdc
p
d
n
p
1
enter
enter
w

And format it:
$ sudo mkntfs -L volumename -Q /dev/sdc1

---

### Post by Sentience on 2009-06-03
I tried downloading Gparted. It said it downloaded successfully but the program does not show up on my list of programs. Is there a command line way of using it?

I also tried the command lines from the poster above me, but they didnt work for me at all.

---

### Post by Sentience on 2009-06-12
These instructions probably make sense to most of you, but Im a noob and the commands are not working for me. Can anyone walk me though this with idiot proof instructions?


btw, I figured out how to reformat it on windows, but now my device is missing 30gb of HD space. There must be a partition in there that I need to delete. I dont know how to do it though.

Isnt there a neat little apt with a user friendly GUI that I could easily install and run?

---

### Post by Cuba71 on 2009-06-12
You have to delete de existing partition(s) in your Passport before reformating it to NTFS.
You'll find step by step instructions at WD site

[Western Digital]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=207&p_created=1008908212&p_sid=C37L1aAj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzcsMzcmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXJlZm9ybWF0&p_li=&p_topview=1")

---

### Post by Cheesemill on 2009-06-12
> **Sentience said:**
> I tried downloading Gparted. It said it downloaded successfully but the program does not show up on my list of programs. Is there a command line way of using it?

You will find it at System > Administration > Partition Editor

Cheesemill

---

### Post by Sentience on 2009-06-12
Thank you. That was easy. I just didnt know where to look for it.

---

