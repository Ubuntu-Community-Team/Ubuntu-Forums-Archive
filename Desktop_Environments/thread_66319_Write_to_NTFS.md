---
title: "Write to NTFS?"
date: 2005-09-16
forum: Desktop Environments
---

### Post by umdzig on 2005-09-16
Is there anyway I can write to NTFS? I want to transfer a file from Ubuntu to Windows XP. I can read NTFS but I do not know how to write.

---

### Post by Leif on 2005-09-16
no, at least not safely. if you really want to pursue this look into "captive ntfs", but afaik it comes with a healthy probability of trashing your filesystem.

---

### Post by sethmahoney on 2005-09-16
The alternative to actually writing to an NTFS partition is to have a small FAT partition (which both Linux and Windows can read *and* write to) and use that to transfer files (by copying the file to the FAT partiton from Linux, rebooting, and opening it in Windows).

---

### Post by taxus on 2005-09-16
I installed Ubuntu about 2 weeks ago on a dual-boot system. I used to have 3 NTFS partitions: one for Windows, a small one (5 GB) for my documents and the rest for download. I never liked the idea of having my documents in the same partition as Windows under C:\Documents and Settings so I've always configured it that way. 

I repartitioned (and reinstalled Windows XP) so I could add two for linux (one ext3 and one swap). The Windows partition is NTFS, but the other two are FAT32. I figured it was the best solution.

Incredibly I could not partition 2 FAT32 partitions from Windows, the menu only let me choose NTFS for the second one, so I did it from the partition utility in the Ubuntu setup program.

I mount both FAT32 partitions (D: and E: in Windows) in linux under /doc and /public (for lack of a better name) and can write to them from both OSes (I had to modify the /etc/fstab partition table though so I could write to them in Linux). I have a "Documents" folder in my /doc partition to which I made a symbolic link in my ~/home folder in Linux, and to which I point the "My documents" icon in Windows (I don't care about file security since I'm the sole user of the computer). Since it's named Documents, it appears automatically in the Places menu in the GNOME taskbar - I mean panel.

I don't use my home folder much, prefering my FAT32 partitions, so I'm keeping /home on the same partition as /.

---

### Post by patrick295767 on 2005-09-28
Maybe ...

Is there another Linux (like mandrake or suse ...) that could be mounting read/ WRITE the ntfs partitions ??

Thanks 

pat'

---

### Post by KingBahamut on 2005-09-28
Patrick thats experiemental on the Kernel level, so it would matter little which Dist you used to try to do it.  

From my experiences, I really would advise against it, unless you have valid backups of that drive itself. You run the risk , if not careful, of corrupting the drive itself. Recovering from just the maintenance partition isnt fun.....ill impart that bit of knowledge to you right now.

---

### Post by DancingSun on 2005-09-28
[QUOTE=umdzig]Is there anyway I can write to NTFS? I want to transfer a file from Ubuntu to Windows XP. I can read NTFS but I do not know how to write.[/QUOTE]
With a free file system driver, you can read *and* write to EXT2/3 from Windows XP:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

So, you can just boot into Windows, and copy the files from your Ubuntu partitions to the XP partitions.  No need for the unreliable FAT32.

---

### Post by YourSurrogateGod on 2005-09-28
Or just use a USB jump-drive.

---

### Post by spencer on 2005-09-28
I use explore2fs in XP and it works great. I've never had a problem with it. You may want to have a look at the following link.
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
-spencer

---

### Post by YourSurrogateGod on 2005-09-28
[QUOTE=spencer]I use explore2fs in XP and it works great. I've never had a problem with it. You may want to have a look at the following link.
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
-spencer[/QUOTE]
Doesn't that open up your ubuntu partition as an ext2 file system, without journaling? Imo, if something goes wrong, you can potentially hose your entire Ubuntu partition. If so, I'd suggest either making a small FAT partition or having a usb jump drive. If you blow up your FAT partition then it's a small loss that can be easily replaced, but if it's the entire Ubuntu partition, well... :?

---

### Post by patrick295767 on 2005-09-28
Sooo many posts concern the fact of mounting read AND WRITE ntfs partitions !! So much, ...
[QUOTE=spencer]I use explore2fs in XP and it works great. I've never had a problem with it. You may want to have a look at the following link.
[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
-spencer[/QUOTE]
Since actually, I passed now all my PC (100%) from Windows to Linux (home).
Anyhow, ntfs partitions are still present.  
Is there some improvements since the release of 'Captive' in terms of Writing in NTFS. I guess the fact that sooooo much people are needing this possibility of writing into NTFS, some release and programs are therefore gonna come for Linux.
The Idea of Linux, that was given the own name of the creator, was to be not lucrative operating system... the time for changes and improvements are therefore slower ... cos less money if we compare the Microsoft windows :
More money, more pressure, more results ... 
But on the other hand, tooo fast doesn't give really total satisfaction !!
Slower = better, more reliable, more stable, .... like the old linux (maybe) ? 
To sum up, 
I wish to see kind of programs like 'Captive' working for having more possibility in Linux Operating System :
Just matter of time then ... 
Pat'
___________
Linux

---

### Post by Leif on 2005-09-28
[QUOTE=patrick295767]
The Idea of Linux, that was given the own name of the creator, was to be not lucrative operating system... the time for changes and improvements are therefore slower ... cos less money if we compare the Microsoft windows :
More money, more pressure, more results ... 
But on the other hand, tooo fast doesn't give really total satisfaction !!
Slower = better, more reliable, more stable, .... like the old linux (maybe) ? 
To sum up, 
I wish to see kind of programs like 'Captive' working for having more possibility in Linux Operating System :
Just matter of time then ... 
Pat'[/QUOTE]

The reason NTFS works on windows is because it is their own format, and they keep the details hidden. The people working on getting it to work on linux have to reverse-engineer the whole thing, which is very tricky.

As for changes and improvement, linux changes far far faster than windows does.

And finally, if you want to see linux work better, then help out. If you can program, help out there. If you can't, you can help test out programs, file bug reports, help people out at forums, and you can even donate money to your favourite projects to make life easier for them.

---

### Post by patrick295767 on 2005-09-28
[QUOTE=Leif]The reason NTFS works on windows is because it is their own format, and they keep the details hidden. The people working on getting it to work on linux have to reverse-engineer the whole thing, which is very tricky.
As for changes and improvement, linux changes far far faster than windows does.
And finally, if you want to see linux work better, then help out. If you can program, help out there. If you can't, you can help test out programs, file bug reports, help people out at forums, and you can even donate money to your favourite projects to make life easier for them.[/QUOTE]


No return to Windows ... nope ! 
I'll do my best ... my best, linux community - Promise !
   
Ntfs in Linux is thus sthg that won't be solved in few days.
I'll therefore have to reformat my harddisks and copy my data to ext2/3 partitions...

Thank you for your information !!

Pat'

---

### Post by DancingSun on 2005-09-28
[QUOTE=patrick295767]Sooo many posts concern the fact of mounting read AND WRITE ntfs partitions !! So much, ...
Since actually, I passed now all my PC (100%) from Windows to Linux (home).
Anyhow, ntfs partitions are still present.  
Is there some improvements since the release of 'Captive' in terms of Writing in NTFS. I guess the fact that sooooo much people are needing this possibility of writing into NTFS, some release and programs are therefore gonna come for Linux.
The Idea of Linux, that was given the own name of the creator, was to be not lucrative operating system... the time for changes and improvements are therefore slower ... cos less money if we compare the Microsoft windows :
More money, more pressure, more results ... 
But on the other hand, tooo fast doesn't give really total satisfaction !!
Slower = better, more reliable, more stable, .... like the old linux (maybe) ? 
To sum up, 
I wish to see kind of programs like 'Captive' working for having more possibility in Linux Operating System :
Just matter of time then ... 
Pat'
___________
Linux[/QUOTE]
Well, one thing that needs to be understood is the fact that NTFS is an IP of Microsoft.  It's not likely that they'll release the specs and documentation of the technology.  While Captive's approach is technically feasible, they tread even closer to Copyright violation than a reverse-engineered pure Linux NTFS driver.  Would Linux ever be able to perfectly write to NTFS partitions?  Not likely.  And when it does, WinFS would probably be the main Windows file system.

---

### Post by darkmatter on 2005-09-28
[QUOTE=DancingSun]Would Linux ever be able to perfectly write to NTFS partitions?  Not likely.  And when it does, WinFS would probably be the main Windows file system.[/QUOTE]
Thankfully that will never happen, as [WinFS](http://en.wikipedia.org/wiki/WinFS) isn't a filing system.;)

---

### Post by DancingSun on 2005-09-28
[QUOTE=darkmatter]Thankfully that will never happen, as [WinFS](http://en.wikipedia.org/wiki/WinFS) isn't a filing system.;)[/QUOTE]
Gah! You caught me red-handed! :oops: 

In anycase, unless MS feels generous, copyright and patent issues still remain.

---

### Post by patrick295767 on 2005-09-28
Most terrible thing is that to convert data ntfs ==> ext3 is only backup and reformating ... 

Reading/writing  ntfs in linux is rather not possible

Reading/writing  ext2/3 in windows is possible (but windows is not originally made for it)

thus, the "Dual boot" generates some troubles !

The only way is to choose your best friend, i.e. your operating system at 100% : Linux or Windows !

Let's choose Ubuntu, no ?

---

### Post by s.s.davis on 2005-09-29
I also needed to transfer Linux files to XP;  the jump drive proved to be the easiest solution - although it meant shelling out $20 for a 128mb jump drive.  (You can often find 256mb jump drives on sale for $20, but I was not so lucky to find such a sale the day I needed to buy my jump drive.) 

I am building a new computer this week, and intend to format the HD to include a FAT32 partition which I will use specifically for accessing certain files in both linux and XP.  

By using Linux, I am able to use an older HP scanner, for which XP drivers are unavailable - so the $20 investment in a flash drive saved me from a new scanner purchase.  The jump drive also proved to be a useful investment when I started college last month.  

Good Luck!

P.S. - I am a relative newbie, so if my plan to format a FAT32 partition for dual access by both Linux (Ubuntu, of course) and XP is unrealistic - please let me know.  I am actually, in fact, considering installing Windows2000 instead of XP for the windows portion of my dual-boot.  

Unfortunately, I need Windows for software I need to run for my college classes.  Fortunately, I can get virtually all MS software for free through a licensing agreement at my school.  So, for the foreseeable future, I'll need a dual-boot system.

---

### Post by patrick295767 on 2005-09-29
Someone knows Paragon Ntfs to linux ?? :-)
(   [http://www.ntfs-linux.com/](http://www.ntfs-linux.com/)    )
or
[http://bisqwit.iki.fi/story/howto/ntfs/](http://bisqwit.iki.fi/story/howto/ntfs/)
(softwares for writing in ntfs )
... 
Pat'

---

### Post by ashrack on 2005-12-18
How did PARAGON succedd in creating a good driver for writting NTFS in LINUX?

---

### Post by DancingSun on 2005-12-19
[QUOTE=ashrack]How did PARAGON succedd in creating a good driver for writting NTFS in LINUX?[/QUOTE]
A few guesses:
[LIST=1]
[*]Experimentation, reverse engineering.
[*]Obtain a license from Microsoft that allowed them to get the specs to NTFS and write a driver for it.
[/LIST]

---

### Post by ashrack on 2005-12-19
I too thing they got a license. Since they're selling it for lots of $$$

---

