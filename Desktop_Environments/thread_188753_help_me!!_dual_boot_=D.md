---
title: "help me!! dual boot =D"
date: 2006-06-04
forum: Desktop Environments
---

### Post by doughnut on 2006-06-04
hey everyone.

im a bit of a newbie when it comes to linux so all help would be appreciated!

im currently about to create a dual boot with XP and Ubuntu 5.10 on my Dell (:-? ) 510m.

my main question is....what partitions do i need to do this??

ive have been told by a few people that i only need the two partitions (one for XP and one for Ubuntu) BUT others have said i will need ONE for XP, ONE for ubuntu, and another for shared space. 

Will all of this be sorted automatically by my Ubuntu install or not?

currently my partition looks like this.....
NTFS - 52.8GB - The main partition with xp etc

FAT32 - 3GB - which i think is the dell system restore which they have rather than sending an OS disk (which i do own a copy of anyway)

the last one is a FAT - 78MB - EISA config

apparently i need to shrink my NTFS partition? is this true? and what is the best way???

---

### Post by mscman on 2006-06-04
Technically all you need for a dual boot setup is two partitions, one with XP installed already and a free partition for the linux install.  However, since NTFS write support is still only experimental, it is recommended that you create a FAT32 partition for data storage that is accessible between the two partitions.  Alternatively you can use a program such as ext2ifs to read/write to your linux partition from Windows.

EDIT: I missed the last part of your post about resizing NTFS.  A very popular (yet commercial) program for this is [Symantec's Norton PartitionMagic 8.0]("http://www.amazon.com/gp/product/B00025O87E/103-9458912-6707043?n=229534").  There are also some free tools that will do this, although I'm not sure about the stability of these programs.  Whatever you do, make sure that you defragment your hard drive before attempting to resize.

---

### Post by jones_jj on 2006-06-04
doughnut, firstly welcome to the forums.  Second, there are some questions you should ask yourself first.  Do you want to share files between Windows and Ubuntu?  Next of the 60 GBs that you have how much do you want to for Windows and how much for Ubuntu, and if you do want to share files between both OSes how much for shared files?

Personally I would backup everything on your laptop and start from fresh.  I personally have had bad experience with partition magic and other partitioning tools in the past.  Plus it is Windows when was the last time you did a fresh install?  You will want to first install Windows.  You can create 2 or 3 partitions using your install CD for Windows. Then install windows on the first partition.  MS likes to think it's the only OS for you.  Go through the install process like normal.  Then you will install Ubuntu and from there you can use gparted to partition out the rest of your partitions how you like.  Since you new to Linux I would just have everything under one partition for Linux and let gparted take care of it for you.  From there you will go about installing Ubuntu, and then install Grub to the MBR and make sure it sees your Windows install.  Reboot and make sure Grub is working with both Windows and Ubuntu and you're ready to go.

---

### Post by doughnut on 2006-06-05
cheers for the help guys.

as of the moment ive got my dual boot working nicely. - although i think soon enough i will be formatting the whole drive and starting again as linux is now on a v small partition (3.2GB) due to me erasing a sill dell sys restore and using the space left. (don't panic! ive got my xp install disk handy:wink: )

how ever i have now encountered two other 'issues'. again any help would be incredibly useful! (appologies if im about to sound like a goose!)

my first and main problem is that i am trying to share an internet connection from an XPmachine with this, my now dual ubuntu xp machine. ICS is working fine on XP but on ubuntu it recognises theres a network cable but the connection is 'idle' and i am unable to access any web pages etc. ive tried getting firefox to auto assign proxy's etc and also tried manually(correctly may be another question) but this doesnt seem to work.
so in conclusion i guess what i want to know is how do i use my broadband connection to my XP machine with my networked ubuntu one.

my network looks like this:
<XP with Broadband conn>-----------Crossover Cable------------<Ubuntu>


my second (and at the moment least important issue is that i can see my XPartition as a seperate hdd (hda2 to give it its apparent name) in ubuntu but it is unreadable and connot be accessed. i get a message saying something like i am not the owner and cant access it. is it because it is a NTFS partition?? i thought that it should be readable anyway??

once again any help would be appreciated. :grin:

---

### Post by kb3hkg on 2006-06-05
sounds like your dual boot went well, congrats! Out of curiosity since it wasn't mentioned did u setup swap space? and as for the connection sharing the first thing that comes to mind is what services the xp box is performing. I do the same but make sure you have DHCP running, that is a very common issue.

---

### Post by doughnut on 2006-06-05
cheers kb. ive got my connection sharing perfectly now! (im writing this in ubuntu if it wasnt proof enough!)

as for swap space i don't remember setting any up:???:  is this going to prove a problem for me?

also any thoughts on why i can't view my NTFS partition in ubuntu??

---

### Post by doughnut on 2006-06-05
cheers kb. ive got my connection sharing perfectly now! (im writing this in ubuntu if it wasnt proof enough!)

as for swap space i don't remember setting any up:???:  is this going to prove a problem for me?

also any thoughts on why i can't view my NTFS partition in ubuntu??

---

### Post by kb3hkg on 2006-06-05
how are you trying to view the ntfs partition? is it mounted? And if you are up and running without swap then I guess it is fine.

---

