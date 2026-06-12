---
title: "grub error 18 HELP!!"
date: 2009-03-20
forum: General Help
---

### Post by astonerose on 2009-03-20
Hi, after the power tripped last night my laptop hasnt booted. 
On the grub if i chose either generic or recov it displays "error 18 selected cylinders exceeds maximum supported by bios" if i chose last known it says "error 15 file not found" 

If i boot off live USB into linux mint i can see my HD in gparted 

unallocated (87.90GB)
/dev/sda4 ntfs MY FILES (68.75GB)
/dev/sda1 ntfs VIRTUALS (41.78GB)
/dev/sda3 reiserfs (32.59GB)
unallocated (1.86GB)

/dev/sda3 is my original installation that i cannot access
/dev/sda1 has no data it is used to virtual hard drives only
/dev/sda4 has alot of my personal data on from my old vista installation that i removed.

None of the above can me mounted or edited, it displays a read/write error or an input/output error depending on what i try to do.

Seeing as i cant boot into my original linux instalation on /dev/sda3 i tried to install a new linux mint onto the 87.90GB unallocated at the begining of my drive. 

During installation it fails to make file system (doesnt matter which fs i choose)
And i cannot mount either partition in nautilus or terminal.

All i can think is the cylinders are wrong but i dont know how to set them back. This system has been running perfect for months and now i am lost as to what to do. 

I migrated from windows 4 months ago and i have picked up lots of information and have fallen inlove with linux and will never go back!!

Unfortunatly i havnt picked up the right info to solve this problem so i am hoping someone can help me learn this and fix my problem.

All i have available to me is a linux mint live usb 
a ubuntu intrepid live cd (doesnt seem to work on install or live boot)
a super grub disk (when booting says operating system not detected)
an xp machine connnected to internet.<--- not my machine

Thanks in advance!!
Phil

---

### Post by cariboo on 2009-03-20
I would suggest booting from a LiveCD and running reiserfsck on your partition. I'm sure that Mint includes reiserprogs.

Jim

---

### Post by astonerose on 2009-03-20
Thanks Jim i ran suggested and it prints:

###########
Replaying journal..
Reiserfs journal '/dev/sda3' in blocks [18..8211]: 0 transactions replayed
bread: Cannot read the block (294912): (Input/output error).
Aborted (core dumped)
###########

As i said though i dont think its partition related as i cant mount any of my other partitions and out of the 3 distros ive tried to install on my 90GB unallocated half have failed in creating file system (about 5% through the install)


I have checked the commands and they are all set to /dev/sda3 on the GRUB.
I still get: Error 18: Selected cylinders exceeds maximum supported by BIOS

The disk isnt currupt because it can see everything just cant access it so its something to do with the comunication between the system and the hard drive surely.

How do i see the cylinder setting or whatever they are (youl have to excuse me here as im not entirely sure what cylinders are) i think its supposed to be set at 1024 form what ive read, how do i check this?

Thanks

---

### Post by miegiel on 2009-03-20
At your disks manufacturers site you can download a "live CD" like image to test your disk.

edit on cilinders : [http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

---

### Post by 123456789123456789123456 on 2009-03-20
ok, weired error to say the least.  the boot partition could be damaged, the MBR could also be damaged.  From the sounds of it, looks that way to me.  Have you tried entering BIOS, and see what it reads the disk as?  I'm interesting if it will agree with grub on the error 18

if not.  attempt repair on MBR.
that should repair damage to Master Boot Record and reset the boot partiton, so that it can boot again.

if the disk physically checks out, with a disk test utility, several are available, including the ultimate boot test disk, available for download from torrents.  If the BIOS for some reason actually agreas with grub.  Then you may need to download a BIOS repair program from the BIOS manucacture.  Flash the BIOS.  to get it back to working normally, that should fix the problem.

If none of that works.  Use a live cd, attempt to recover as much data you can, and reformat/partiton the disk, and do a clean install.
that last part is a last ditch effort of course.

---

### Post by astonerose on 2009-03-21
my BIOS is rubish the only info i can get about the drive is its manufacturer and model number i cant change its mode or anything only which one to boot off and SATA controller. I cant actually mount any partition to access data off it i can only see the partitions. If i try to mount it i get read/write error on dev/sda#. 
Hitachis website doesnt have much support for this model as far as live repair cds go.
I will try the suggested MBR repair disks i did go out to look for a 2.5 hdd to sata connector to see if my desktop would read it but they only had IDE in.
I'l let you know how the boot repair goes. Thanks

---

