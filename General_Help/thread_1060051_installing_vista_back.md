---
title: "installing vista back"
date: 2009-02-04
forum: General Help
---

### Post by kallum on 2009-02-04
Hi,sorry if I havent posted this in the right place but I want to install  windows vista back since I cant get used to Ubuntu. So i restart my pc put windows vista disc in and get to where i want to install it, then i get this message 
"windows must be installed to a partition formatted to ntfs"
how can i install vista back? thanks;)

---

### Post by Regnulify on 2009-02-04
You'll need to at least delete the partition with the Partition Editor (or fdisk). The Vista install should be able to format to ntfs from there.

NOTE: This will delete everything so backup first.

---

### Post by bba1973 on 2009-02-04
I've been in the same boat as you, but I'm giving ubuntu another shot. Anyway, as Regnulify said, the file systems are different. You'll lose all your data since it has to reformat, so make you you've got everything backed up. If all you want on your computer is vista, then you might as well just delete everything off your hard drive and start fresh. Worked fine for me. Good luck.

---

### Post by kallum on 2009-02-04
ok so what i do is just format the partition ubuntu is installed on when im trying to install vista and i will be able to install it there?

---

### Post by RedSingularity on 2009-02-04
> **Regnulify said:**
> You'll need to at least delete the partition with the Partition Editor (or fdisk). The Vista install should be able to format to ntfs from there.

NOTE: This will delete everything so backup first.


I think that Partition Editor can even install the NTFS file system after the current one is removed.

---

### Post by kallum on 2009-02-04
I have downloaded "GParted" is this the right thing to delete the partition? How do i delete it?

---

### Post by RedSingularity on 2009-02-04
Yes thats it.  Now what you do is type in terminal "Sudo gparted" which will start the editor.  Once your in you will see at the upper right hand of the editor screen something to the extent of "/dev/sda".  If you have only one hard drive you dont need to change it.  Otherwise this is where you pick the HD you want to format.  Select the one you want.  From there just right click the ext3 file system and click delete.

---

### Post by kallum on 2009-02-04
ok i right click the ext3 file system but delete isnt highlighted so i cant go on it?? :o

---

### Post by RedSingularity on 2009-02-04
You will need to unmount the Drive first.  Once you do that it will be highlighted.  Problem is you cant unmount your current OS drive.  Do you have the live cd?

---

### Post by kallum on 2009-02-04
do i have what live cd? Ubuntu?

---

### Post by RedSingularity on 2009-02-04
Yeah you need to boot the Ubuntu live CD and access Partition Manager on that.  This way the computer is running off the CD and not the HDD.  Then with the HDD un-mounted you can delete whatever you want.

---

### Post by kallum on 2009-02-05
> **Shadow121 said:**
> Yeah you need to boot the Ubuntu live CD and access Partition Manager on that.  This way the computer is running off the CD and not the HDD.  Then with the HDD un-mounted you can delete whatever you want.

Ok i got a few questions, I have the live cd but how do i access the Partition Manger? What will happen when i delete the partition and what would i do after that? thanks:popcorn:

---

### Post by RedSingularity on 2009-02-05
Partition editor should be under System>Administration once you boot the Live CD.  If it is not then you just install it by typing in terminal "gparted".  Of course you will need Internet set up on that computer.  Once you delete it everything will be erased on that Hard drive.  After you delete it then exit Ubuntu Live CD and insert your Windows Disk.  You can format the Drive to NTFS within the Windows Setup.

---

### Post by kallum on 2009-02-05
so i should go on " try ubuntu without any change to your computer" when i click that it just comes up with an error:o

---

### Post by RedSingularity on 2009-02-05
OK, then we can boot directly into Gparted with a bootable CD.

1)  Download ISO file with this [Link]("http://downloads.sourceforge.net/gparted/gparted-live-0.4.1-2.iso?modtime=1230460364&big_mirror=0")
2) Burn ISO to Disk
3) Boot disk.  (It will go strait into Partition Editor)


If you want you can check the Ubuntu boot disk for errors.  Sounds like there is something missing on the disk.

---

### Post by kallum on 2009-02-06
ok i got vista back :p thanks for helping me:popcorn:

---

### Post by RedSingularity on 2009-02-06
No problem man.  :)

---

