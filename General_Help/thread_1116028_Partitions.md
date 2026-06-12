---
title: "Partitions"
date: 2009-04-04
forum: General Help
---

### Post by XWolf on 2009-04-04
Alright I'm trying to install kubuntu I'm still a newbie to ubuntu and the lot, but I have had it on my computer before. However when I put it on my computer before I didn't do manual partitions. I am confused on how to do this the right way.

The only reason I'm doing manual is because I'm going from Vista to kubuntu entirely. However I have an ntfs partition with things like music, documents, etc I want to be able to still have.

I've looked around and within doing so I've managed to confuse myself even more lol. I've heard things being mentioned about root partitions and swap areas and /home partitions and the regular (k)ubuntu partition, etc. 

If somebody could tell me what the following partitions do and how to set up ubuntu so that it is a primary os, where as I don't plan on keeping windows for dual boot I just want to be able to save that one ntfs partition once (k)ubuntu is installed so I can still access it once (k)ubuntu is installed, It would be appreciated.

Thanks
XWolf

---

### Post by SuperSonic4 on 2009-04-04
/ is the root partition and it's where installed programs, grub and system files go (like xorg.conf)

/home is the user's home folder which contains any users and all their program settings, scripts and personal documents like music

swap is what the system uses like extra ram for your pc to keep it faster.

The arch wiki explains it better (it still applies to kubuntu): [http://wiki.archlinux.org/index.php/Beginners_Guide#Swap_Partition](http://wiki.archlinux.org/index.php/Beginners_Guide#Swap_Partition)

---

### Post by eruptionjoojo on 2009-04-04
Hello ,
    

            If i'm not wrong you have a Kubuntu Live CD(8.10) ............ like you said you wanna keep that Vista partition so for trying Kubuntu you do not need to format anything ............ You could if you want directly install the Kubuntu OS into Vista like a normal program ........... and may uninstall it via the control panel ........ just like any other program ............
You just need to follow the Following steps :-
(1).While the Vista OS is Running just put the Kubuntu Cd into the CD/DVD Drive.
(2).then you would get the option to try Kubuntu in windows .....
(3).follow the general steps for the install like selecting the drive, partition size etc. 
(4).kubuntu would create a boot entry and provide you with the options as to wish OS you wanna Boot to ............
(5).there you have it Kubuntu and Windows Vista on the Same System without having to do any partition etc...........

---

### Post by Zimmer on 2009-04-04
So, you want to keep all the data you have in the NTFS partition? But you are wiping Windows and JUST installing Kubuntu ?

How much 'data' do you have on this NTFS partition?  Normally it would be good practice to backup ANY data you have before considering partitioning. So, if you have space somewhere to copy it to (DVD disks, an external HDD etc) then now is the time...
check the backup ,  then install Kubuntu how you want and you can copy as much of the data back onto your system as you wish.

If you try and  'save' the partition and install Kubuntu 'around' it you may encounter problems and limitations.
Have a read of these links..
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#Preparation_For_The_Install_](http://www.users.bigpond.net.au/hermanzone/p17.htm#Preparation_For_The_Install_)

Many people will post you many different replies regarding how to organise partitions but the Basics for a fresh install are:

Create two partitions , one will be the majority of the drive and hold the complete system and storage space (Primary partition), the other will be a small (one gig) SWAP partition.

Make the PRIMARY partition bootable.

Everything else is a variation on the theme within the limitations of the number of partitions possible. (plenty of literature out there to explain it better than I).

If I were installing Linux on a fresh machine I would create at least 3 partitions.
One PRIMARY (bootable) around 12gb to install the Linux on, second PRIMARY formatted ext3 to use to store my data on. SWAP partition of 1gb.

If your NTFS data is safely backed up you can afford to experiment... but do read more on partitioning, and I will try and look for a nicer link to clear up any issues.

EDIT:[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
wealth of info here, of course

---

### Post by XWolf on 2009-04-04
Zimmer you have my idea down, I can't actually boot up windows atm, which is why I'm reformatting and I figured now is a good time to switch to linux like I had planned to rather than installing vista again and then installing linux later. 

I just was hoping I could keep the partition with my music on it where it is separate from the majority of the HDD. The partition containing my music and documents is 65368 MB according to the kubuntu partition set up screen. The main partition where vista is installed at the moment is 184687 MB. 

I was hoping to use that partition to install kubuntu and completely get rid of vista, with the exception of that other ntfs partition I have that contains music and documents.

Where I can't boot up vista I can't necessarily back anything up securely, nothing on the partition is really extremely important just makes things easier if I can keep it.

I don't really understand the partitioning set up of linux I read a bit from the link SuperSonic4 posted. But am still a bit confused. (not used to kubuntu or linux for that matter.) Windows doesn't have a root partition and then primary and a swap. When I'd enter partition set up in windows install it showed only the two partitions I had and I only needed one to properly install windows. So forgive me for my stupidity when it comes to setting up partitions on kubuntu, I'm sure it's a rather easy task and I'm not getting the hang of it lol.

So swap partition would only need to be around 1 GB? From reading around I've found several places saying for anybody higher than 1 GB of RAM they only need 1 GB swap partition. I think this would apply to me as I have 6 GB of RAM in the computer I'm trying to install kubuntu on.

So what should the other drives be? I'm the only person on this computer so I'm only going to have one user name. Just trying to think of general sizes of what the partitions should be for the other two. If I'm to keep the ntfs partition (65368 MB) and the swap would be 1000 MB then that would leave me with 183687 MB for the root and primary. But how much space does the root partition need?

Also I've read about a /usr partition, is it necessary or helpful in any way or is the /usr partition the same as the "primary" partition?

---

### Post by 3Miro on 2009-04-04
Just one thing: before you mess with partitions BACK UP ALL YOUR IMPORTANT DATA FROM ALL PARTITIONS. If your power for example goes off during partitioning, you may loose everything on your HD.

---

### Post by CyberMando on 2009-04-04
You want to partition as ximmer said but leave your NTFS partition alone and devide the remaining disk as he said.
So you will have
/dev/sda1     NTFS existing partition DO NOT format
/dev/sda2     12 GB        mount on /
/dev/sda3     1 GB         swap
then logical partitions
/dev/sda5     rest of disk mount on /home

---

### Post by XWolf on 2009-04-04
Alright, got it thank you all.

---

