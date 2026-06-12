---
title: "how to unistall kubuntu from laptop's 2nd HDD W.O/windows CD"
date: 2009-02-21
forum: General Help
---

### Post by SMG_07 on 2009-02-21
hi guys

u see i have this proplem with kubuntu (ubuntu , kubuntu ,zubuntu .. tried them all :( ) .. can't install 8.10 before i install 8.04 and activate the ATI 3650 HD card then i upgrade to 8.10 via internet ... 

this is the 8.10 without the ati card
[ATTACH]104147[/ATTACH]
and this is what my kubuntu looks like now :(

everything is working in it but the screen isn't showing me anything except that :(

now i have a 500 GB HDD that i can't use and i need it back 

my question is this : how do i remove kubuntu from my 2nd HDD without the windows cd ( cos its a laptop and the windows is already installed )

this is my laptop specs:
ASUS M70SA
INTEL CENTRINO CORE 2 DUO 2.5 GHz 
2x 500 GB DRIVES
ATI RADEON 3650 HD 1GB
4 GB RAM

PLZ guys im a desperate i don't know what to do i'm a beginner

---

### Post by ajgreeny on 2009-02-21
Do you want to keep (*)ubuntu 8.04 or go back to windows alone?  If you want a ubuntu which works, and I think you meant that 8.04 does work OK, then simply reinstall 8.04 over your non-working 8.10.

 If you want to get back to windows only you need to restore the windows MBR, which you can do even without a windows install CD from the ubuntu live CD.

Boot the live CD to a desktop and then use terminal to install lilo.
```
sudo apt-get install lilo
```then
```
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

---

### Post by SMG_07 on 2009-02-21
Ok i wanted to have windows alone now so i did what u said but the 2nd HDD is not showing in windows ... what to do man ??

i want to use the 2nd HDD for windows to as a free space but i guess it still have kubuntu in it.. what's next??  :popcorn:

---

### Post by ajgreeny on 2009-02-21
OK, boot to the live CD again and go to System > Administration > Partition editor and delete the partition(s) with kubuntu on them.  They will probably be /dev/sdb# partitions.  Now with the unallocated space make a new partition and format it to ntfs.  Wait for that to finish, then boot into windows again and the disk should be available as drive D: or whatever the next available drive letter might be.

This is all as a result of the inability of windows to see any ext3 partitions, unless you install third party drivers to see them.

---

### Post by SMG_07 on 2009-02-21
yeeeeeeeeees it worked :guitar:

u r THE man :lolflag:

thank you very very much ;)

but just a little Q .. 
this is a pic after i did the whole thing ... what do these two 11.31 gigs do ???
[ATTACH]104213[/ATTACH]

---

### Post by ajgreeny on 2009-02-22
They are the swap partition for your now deleted ubuntu system so you can delete those as well and and use the space as another ntfs partition, or add it to the first one you made.  It shows twice because sdb2 is an extended partition, ie just a wrapper that can contain other partitions, and sdb5 is the actual swap partition contained within it, that you need for a linux system.  It was huge, however, and I don't think I've seen one as big ever before; with 4GB of ram, you would probably manage without swap, though ubuntu will allocate some automatically if you let the system install by default.

---

