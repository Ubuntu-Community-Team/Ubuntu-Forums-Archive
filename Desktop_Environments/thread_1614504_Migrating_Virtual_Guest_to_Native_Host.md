---
title: "Migrating Virtual Guest to Native Host"
date: 2010-11-05
forum: Desktop Environments
---

### Post by Glencore on 2010-11-05
Migrating Virtual Guest to Native Host
Hello,

I have been using ubuntu server and desktop on virtual box for a while now. I have come to enjoy it more than being in Windows. I would like to install it natively. I am wondering. is there any way I can take my virtual machine and apply what I have done there to a new ubuntu install?

I have a ntfs hard disk, will ubuntu resize that for me at install?

Any good apps for backing up all my my firefox data and then applying that to my firefox in ubuntu?

I need to keep windows for some stuff for work, and for some games I like.

Any help much appreciated, thanks.

---

### Post by 3Miro on 2010-11-05
I once managed to get an entire Ubuntu installation from Virtual Box, zip it, move it over to an empty partition and extract it. Then I had to manually edit a whole bunch of settings files and it worked, but it was too much trouble. The easiest thing you can make is make a list of the software that you have installed in VB and then make a clean install of Ubuntu.

For partitioning, it is recommended that you use the windows partitioning tool to repartition/resize existing partitions to make room for Ubuntu. It is also recommended that you make two partitions, one with size between and two times the amount of RAM that you have that would be used for swap, and one partition for root /. During installation, when you get to the partition stage, select manual/advanced, then tell Ubuntu to use the swap partition as swap (and format it) and the other one as ext4, format and mount at / (that is slash).

Note that Ubuntu can also resize the NTFS partition, however, I think using the native windows tool is recommended.

Ubuntu should automatically setup the boot-loader for you, so that when you boot your computer, you will be given a choice between Ubuntu and Windows.

For Firefox, you can export your bookmarks as HTML and then import them under Ubuntu. Extensions for windows and Linux are usually different, so there very little else that you can move.

---

