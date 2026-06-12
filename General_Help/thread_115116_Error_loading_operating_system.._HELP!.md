---
title: "Error loading operating system.. HELP!"
date: 2006-01-09
forum: General Help
---

### Post by kane_666 on 2006-01-09
hey, i've got ubuntu as my only operating system on my computer. when i ran fdisk in the terminal and viewed the partition table, there was my main partition (with ubuntu) and 2 others. 1 being the partition i made when i was using windows (forgot to delete it) and the other being something i didn't know about (it said something like linux swap :S) so i deleted my old partition and that deleted the swap thing. so then i was left with my 1 partition and some unallocated space. then i wanted to install a second operating system (windows 2000) so i stuck the cd in and restarted. when it asked me which partition i wanted to install it on, i picked the unpartition space (the unallocated space one) which it partitioned and called it c: but it was too small to install windows 2000 so i was going to exit the setup and go back into ubuntu and create a bigger partition. but when i restarted i an error! something like: error loading operating system! so i then i went into my bios to see what operating system it was trying to load and it had win2000 selected. my other 2 choices where win98 and other. so i selected other and then rebooted. i got the same error. does annyone know how to fix this?

thanks!

---

### Post by Protex on 2006-01-09
Erm, not sure about the other things but I can tell you that Linux Swap is a neccessary part of your Linux installation. Similar to the Windows Pagefile if I'm not mistaken.

---

### Post by southernman on 2006-01-09
You wiped out the boot record when you tried to install M$.

In order to get a proper dual boot system up and running, you'd need to install your microsloppy OS first. After that you would be able to install ubuntu (or your *nix flavor of choice).

You'll need a live cd of some sort (ubuntu, knoppix...) and a more seasoned techy than myself to save your system. If it can be done at this point, which I feel pretty sure can be done.

Good luck!

---

### Post by kane_666 on 2006-01-09
im more than happy to format my computer and begin all over its just at this point.. i dont know how. can i just boot of the windows2000 cd and format ? (does it have that option)

---

### Post by southernman on 2006-01-09
[QUOTE=kane_666]im more than happy to format my computer and begin all over its just at this point.. i dont know how. can i just boot of the windows2000 cd and format ? (does it have that option)[/QUOTE]

Good Man! ;)

Yes, you can delete and setup partitions in winders. I suggest when doing so that you make this partition only as big as you need for your OS and other programs. 5 - 10 gigs should do you just fine unless your a big gamer.

---

### Post by kane_666 on 2006-01-09
:) so all i have to do is boot up using the win2000 setup cd. then delete all my partitions, then create a new one (as big as needed) and then install windows onto that ? if thats works then thanks :D

---

### Post by southernman on 2006-01-09
That's enough to get your box up and running... ready to take ubuntu again.

When you do install ubuntu be sure to let grub be installed to your MBR. From here you'll be able to boot into ubuntu or windows.

---

### Post by kane_666 on 2006-01-09
right, i started the win2000 setup, this is what my partition table looks like (roughly)

9768 MB Disc
------------------------------------------------
--Unknown                  9335MB      (i have the option to delete this one)
   Unpartitioned Space     433MB     (i have the option to create a partition from the space)


What am i suppose to do? i dont want to delete the unknow because i dont know if that will stuff it up more.. and the unpartitioned space isn't big enough to install windows. any ideas?

---

### Post by southernman on 2006-01-09
Can you plug this drive into anther machine and see what's on it?

I think you'd be safe to wipe out, but don't take my word for it if you there could be valuable files on this drive.

Is this only a 10 gig hdd?

---

### Post by kane_666 on 2006-01-10
no i cant plug it into another computer :(
theres nothing on it (i didn't get a chance to install anything) lol
yeh its only 10 gig.

should i delete the Unknown Partition ? if i do, would all that memory be transferd to the unpartitoned space? giving me a 10gig unpartitioned space? or would it give me 9335mb's of unallocated space..?

---

### Post by southernman on 2006-01-10
[QUOTE=kane_666]
should i delete the Unknown Partition ? if i do, would all that memory be transferd to the unpartitoned space? giving me a 10gig unpartitioned space? or would it give me 9335mb's of unallocated space..?[/QUOTE]

Yes

Yes

Yes

No, it'll give you the full 9768MB of space. You'll need a minimum of 2 gigs for ubuntu... the more the better though. Only setup one partition in winders and leave the rest unpartitioned.

Happy formatting!!! ;)

---

### Post by kane_666 on 2006-01-10
sorry for all the questions but i wont to get this right and not stuff it more lol so i delete the Unknown partition, and that should transfer all the memory to the unpartitioned space... giving me a 10gig unpartitioned space? so then i can just install windows2000 lol that **should** be the last of the questions :P

---

### Post by kane_666 on 2006-01-10
yay it worked... but now i have to format :D to i format an ntfs filesystem or fat?

---

### Post by southernman on 2006-01-10
ntfs is generally the prefered file system for windows.

As I understand it... *nix can read from a ntfs but it can't write to them.

---

### Post by kane_666 on 2006-01-10
thanks! you've been a great deal of help. :D if i run into trouble, ill reply ;)

---

### Post by southernman on 2006-01-10
Your welcome Kane - and Thank you too.  :)

---

### Post by kane_666 on 2006-01-10
well it all seems to be going well. i just have a few questions... :) 
1) when i install windows and partition for a new OS (ubuntu) can they read eachothers drives? like if im in ubuntu can i listen to music thats on the ubuntu partition?
2)Can i create a 3rd partition, so i have 2 for each OS (just big enough to fix them) and then have the rest of my hard drive space on a new partition so they can both access to read and write. is that possible?

thanks :D

---

### Post by kane_666 on 2006-01-10
i found this article on [http://www.hackthissite.org](http://www.hackthissite.org) a while ago (about dual booting) and was wondering if it looks ok. does the information look correct?

> I wrote this article a while ago and never got around to putting it up here...enjoy


Installing a new operating system can be quite daunting if you've never done it before, we've all heard stories of people losing all their data, however I've done it quite a good few times and have never had any problems, so you shouldn't either. I'm assumming that you've already read the other articles about choosing your new operating system and have already downloaded the ISO's that you need(check out DistroWatch if you haven't). Before we start, just to clear up that there is no need to format your computer to install a new OS. If you have enough free space(at least 5gigs) it is totally possible to keep your current hard disk with windows and all your other files untouched and still install another OS. Before you start you should check that you can boot your computer from cd. Restart your computer and enter your computer's bios set-up (usually done by pressing F2 and your computer first starts), in there you will see a boot order, change it so your computer tries to boot from cd before the hard disk.

If you've bought installation cd's or have already burned the ISOs to cd you can skip this paragraph. Firstly download a copy of nero cd burning suite here. Once its installed click start > programs > nero > nero 6 demo > nero burning rom. In the tool bar, if it says "image recorder" change it to point to your CD drive. Then at the top click recorder > burn image. When the dialog box opens change file type to *.* and double click the ISO file you want to burn. Tick the "finalize CD" box and change "write method" to "disk-at-once" click burn and it'll burn the ISO. Do this for all the ISO files that come with your new OS.

If you have two hard drives with enough free space it is a better idea to have on OS on each drive rather than putting them both on one, if you have two hard drives you can skip this and the next paragraph. Most people however don't have this option, so they must partition their hard disk. This basically means your computer is going to act as though you have two hard disks. There is a slight danger that you will lose all your data when you partition your hard disk so you may want to back up your data (this means writing everything on your hard disk to CD ...there are programs out there to do this if you want to, if you've got something really important on your disk do this, if not the chances of losing your data is small). Click start > programs > accessories > system tools > disk defragmenter > defragment. This will move all related data on your hard disk together, and moving all of the data to the front of your disk. Next you need partitioning software. The best partitioning software available is partition magic, the only downside is that its not free. If you can, I strongly advise you to purchase this software as it really is very good, however if you can't you should try to acquire it from a friend. 

Open up partition magic and click "Install another operating system" on the left of the screen. Unless you're installing another version of windows select linux. Create it as primary after C: and its usually ok to accept the recommended size given by partition magic, it should be at least 5gb and if months later its not enough you can come back and increase the size then. Now right click the NTFS partition (most likely C:) in the partition magic window, select advanced and click "unhide". Then click apply and your computer should restart and begin partitioning.

Once its finished partitioning (takes about an hour usually) put in the first installation cd and reboot your computer. Installation depends on the particular distribution you have, however its usually pretty straight foward, you want to install it onto an already existing partition. If you get asked about bootloaders (just something that is going to let you select what OS to load when your computer starts) you want to install the bootloader into the mbr (master boot record). If you can't figure out how to install look online, there are tons of guides for each specific distro. Once its finished installing just restart your computer and you'll see a screen that asks you which OS you want to boot. From here its up to you to set up linux on your own. If you run into any problems search google first, almost all problems are very common and there are already tons of solutions to them out there. If you can't solve your problem go to LinuxQuestions.org and you'll get much better help there than you would on HTS.

If you run into any problems at any time and want to go back to windows just pop in your windows 2000/XP CD, restart your computer and press R to go into the recovery console, then type "fixmbr" and press enter. This will allow you to boot into windows only when your computer starts.


If you've any comments or suggestions feel free to PM me.

HopperG. 

---

