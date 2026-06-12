---
title: "Dual boot Windows/Linux"
date: 2006-02-15
forum: Desktop Environments
---

### Post by SuperMightyMo on 2006-02-15
Hey

I am new around here so i don't know if i posted this thread on the right place.

I have installed windows first, and after that i installed Windows on my machine. When the question came if i wanted to install grub in the MBR i said no, and put it in my second partition on my harddisk. Now when i try to open windows, it says that i have a dammaged disk, (i get a blue screen). so i hoped you can help me. I don't know to much about linux, so please take it on ease. 

Thanx, supermightymo

---

### Post by Robgould on 2006-02-15
The blue screen is not good.  Does windows try to boot at all?  Do you get a grub boot menu?  Is it after you choose windows that you get the blue screen?

---

### Post by Bartender on 2006-02-15
[QUOTE=SuperMightyMo]I have installed windows first, and after that i installed Windows on my machine. When the question came if i wanted to install grub in the MBR i said no[/QUOTE]
  
You mean "after that I installed Ubuntu", right?  I'm a neophyte myself, but I think the way you did it was wrong.  Take a good look at this website 

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If some of the smarter guys kick in to your thread they can probly tell you ways to repair.  In your case, what the heck, you may just want to get the practice & re-install Windows, then follow the steps at hermanzone.  If you can get your machine set up next to a connected computer and follow the steps one-by-one, that's the way to go

Good luck

---

### Post by Michael Steinberg on 2006-02-15
Though most people prefer using GRUB, which if put in the MBR will automatically find Windows & add it as an option, you can pretty easily use the NT bootloader on Windows. An inability to boot Windows might be caused by improper partitioning. What did you do with the Windows partition to make room for Ubuntu? (Or did you use Windows' own partitioner?)

---

### Post by SuperMightyMo on 2006-02-16
Hey

I first installed windows, on my 160 gig sata hard disk, i made a 60 gig ntfs partition and installed windows, i left the rest of the disk space open. In Linux i made the following partitions:
90 gig ext3 (made the label /root and i made it active ( did it automatticly)
8.2 gig swap memory

That was it. 

I got the grub menu and choose Windows from it. Wheb you see Windows home edition whit the loader underneath it, it starts loading, than it hangs and than i get the blue screen saying that my hard disk may contain virusis or my hard disk is damaged.

Thanx SuperMightyMo

---

### Post by silverash on 2006-02-16
When making windows partitions use windows apps when making linux partitions use linux apps.

My advice:

Format HD

Get copy of windows 98/ME stiffy disk. XP 2000 and so forth don't have fdisk on there boot disks
Partion HD using fdisk. Make only windows Partition.

If you don't what to Format windows. Get PowerQuest PartitionMagic. Use this program to resize you HD but do not make linux partition just leave it unused.

Install Windows on windows partition.
once complete test to see if it works.
If you get blue screen of death, Get a new HD.

Next boot using linux boot disk and select free space and let it make all the partitions for you.

Install Grub. The windows boot loader sometimes does not find linux OS yet Grub or lilo always finds windows.

This is something I have done many times and has always worked. Just remeber to use the OS tools to make the OS partition.

---

### Post by SuperMightyMo on 2006-02-16
Hey

Thanx for your post, but i really don't want to by a new harddisk. I just bought a new computer. I didn't metion it before but i have a sata harddisk. On other thing i only used the setup from windows and linux, so i didn't used something like partition magic or gparted. I hope you can help me

thanx supermightymo

---

### Post by silverash on 2006-02-16
Ignore my last post That is a pure IDE HD setup. Sorry..

Sata Hard Drive don't go well with linux. I googled a bit a found that most linux distros have issues with them. I came across a few post that talked about it. 

[http://kerneltrap.org/node/2173](http://kerneltrap.org/node/2173) 
this one seems to have the only solution on it. 


Sorry I can help you more but I haven't got a SATA HD to play with.

---

### Post by Michael Steinberg on 2006-02-16
It sounds like you did what you were supposed to do, and I'm not sure what caused your problem. There really shouldn't be any problem with SATA drives.

I'm a Mac-and-Linux person, not a Windows person, but here's my guess: Does the Windows blue screen ask if you want to check your disk? If it's the two-tone model--darker blue at top & bottom--it's mainly upset that the partition table has changed. Windows doesn't like stuff like that going on behind its back! Try using Windows fsck (No, I mean CHKDSK...) to repair the installation. (Boot into safe mode-command prompt.)

BTW, does Ubuntu boot properly?

---

### Post by SuperMightyMo on 2006-02-16
Hey

Yes, ubuntu boots properly, in the screen it doesn't checks my drive but says  it may contain a virus or my disk is broken. How can i do this fdisk??

Thanx, SuperMightyMo

---

### Post by Michael Steinberg on 2006-02-16
When you first boot into Windows, press the F8 key and you should be delivered into a black-and-white text screen. Use the arrows on the keyboard to choose safe mode with command prompt. Run CHKDSK (you can find more info on it on the web at [url]http://www.microsoft.com/resources/
documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx[/url])--I was mistaken when I said fdisk. That's supposed to check your drive and fix things up. Then see if Windows will boot.

It sometimes takes a few tries before you press F8 at the right moment--don't give up!

---

### Post by SuperMightyMo on 2006-02-17
Hey

When i run chkdsk i get an anwser back saying, my hardisk has unsolvable problems. That's all. the point is i can use only linux ore only windows but i can't dual boot, so i guess it's not my harddisk what's the problem.

Thanx, SuperMightyMo

---

### Post by Michael Steinberg on 2006-02-17
As they used to say, bummer. If you don't have any personal data on the machine, I'd wipe the drive & start again. Let Windows format one chuck of the drive (not the fast option) and install it. Then test it. Then start up from the Ubuntu disk & let Ubuntu divide up the free space when it installs. It will put in an appropriate swap space--8.5 gigs is unnecesarily large. Let GRUB get installed as it wishes, in the first sector of the main drive. That should do the trick.

HOWEVER--since you already have a working Ubuntu setup you might check the forum & Wiki for ways to reinstall GRUB. Once Windows is working within its partition all you really need to do is install a bootloader. (There are also ways to add Ubuntu to the Windows bootloader but you'd have to install GRUB on the Ubuntu partition, etc.)

---

### Post by SuperMightyMo on 2006-02-17
Hey 

Everybody thanx, thanx for your support. But i have to say (to my regret),that i am going back to windows. The only reason for my windows chooce is the fact that i like computer games, and my mp3 player. When computergames work without cedega on linux i will defentaly be back, on my other computer i will keep ubuntu. Don't get me wrong, i don't like windows and i love linux. 

Thanx, SuperMightyMo

---

