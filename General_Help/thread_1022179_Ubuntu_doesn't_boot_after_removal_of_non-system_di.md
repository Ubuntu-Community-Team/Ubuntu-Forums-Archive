---
title: "Ubuntu doesn't boot after removal of non-system disk"
date: 2008-12-26
forum: General Help
---

### Post by ha2ooh on 2008-12-26
This problem has kept me busy all day and I have run out of ideas.

**The situation**
When I installed Ubuntu I had two 500 GB Seagate 7200.11 in my system. I only used one to install the system on. Made three partitions Swap, / and /home.
Over a month later I formatted the other drive, but I never used it so I decided to take it out of the system.
But then:
1. I could no longer boot. I would get a message like "insert boot device"
2. I found out that when I plug disc 2 back in, I can boot without a problem.
3. When I put in a Windows disc, it booted windows and not Ubuntu.
4. I ran Super Grub cd and I managed to get Grub to boot.
5. Ever since that time I get Error 21: Can't find system disc.
6. I switched the system disc with the empty disc and that had no effect (to see if it was an interface issue). which had no effect.
7. I tried using live swap from the Super Grub disc with both discs in on their original socket.

I have read more and more of the Grub manual, but I feel I am not getting any closer to solving this. Also the manual is huge and I have no clue where to begin... I suspect some kind of configuration error. And I think it is Grub, but I am not even sure of that.

I hope someone has an idea of what this could be and perhaps even how to resolve it.

Grub version 0.97-29ubuntu21
Ubuntu version 8.04 AMD64

---

### Post by Herman on 2008-12-26
Hello ha2ooh,

GRUB, like most other boot loaders, comes in three parts.
The first part of GRUB is really small, less than 446 bytes, because it has to fit in the MBR, which is only 512 bytes, and still leave other important code in the MBR untouched, such as the Disc identifier and the partition table. The first part of GRUB is called 'stage1'.

There's another intermediate stage of GRUB which is optional, called 'stage1_5', which fits in the next 21 sectors after the MBR.
If stage1_5 is installed, then stage1 in the MBR points to stage1_5 and stage1_5 helps to locate the third stage of GRUB, called stage2.

GRUB's 'stage2 file will be located in your /boot/grub/ directory inside Ubuntu. It's the stage2 file that brings up your GRUB menu and actually does the hard work of booting your operating system.

The problem that sometimes occurs is that the stage1 and stage1_5 files can be installed on the wrong hard disk.
That's what I think has happened to you.
Your computer's BIOS will normally always look at the MBR in your first hard disk (number 0), and boot the MBR in the first sector, (sector 0), there.
Apparently there is some confusion or disagreement between your BIOS and Ubuntu and GRUB over which of your hard disks should be first, (number 0), and second, (number 1).
You originally had Ubuntu with the stage2 part of GRUB in one hard disk, and an empty hard disk with GRUB's stage1 and stge1_5 files in the other.
So when you put the other hard disk in, you could boot, when you removed it you couldn't boot.

Then, you used Super GRUB disc, (good), and you did a few things to try to fix it.
I think that you did make some progress in the right direction, because now at least you are getting GRUB, even if you still only have an error message.
I think probably you have used Super Grub Disc to install GRUB's stage1 and stage1_5 to MBR in your Ubuntu hard disk.
Your stage2 file is now able to be found, and that then brings up your GRUB menu, is that correct?

The problem now is, your GRUB menu, as a result of the earlier confusion, has been misconfigured to point to the other hard disk.
Please click on this link and see if you agree, [Grub error 21]("http://users.bigpond.net.au/hermanzone/p15.htm#21"). [http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

All you need to do is boot Ubuntu with your Super Grub Disk, and open up your /boot/grub/menu.lst file and change the hard drive number from (hd1) to (hd0), or vice-versa.
If you aren't sure how to find /boot/grub/menu.lst and edit it, here's a link that might help you, [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) 
...and click on '[Orientation]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation").', and '[Customizing Your GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst")'.

If you need more help, please don't hesitate to ask, there are no stupid questions, only stupid answers. :)

---

### Post by ha2ooh on 2008-12-29
Thanks a bundle Herman :)

You were spot on. Thanks for explaining exactly how this works and linking the site with even more information. It is very helpful in my understanding of this problem.

It seemed I was very close. I followed your advice except only I didn't use the super grub disc to change the drive number in menu.lst. I opened the the file in Ubuntu with root privileges. I searched and replaced all the hd1 instances with hd0 and that did the trick.

Now I have found that the system disk is called sdb, when I had the second drive installed and now that the second drive is out it is called sda.

Is there any way to prevent this? 
Because it is a bit inconvenient if I have to edit my menu.lst file every time I put in a second hard drive?

---

### Post by Herman on 2008-12-29
> Is there any way to prevent this? 
Because it is a bit inconvenient if I have to edit my menu.lst file every time I put in a second hard drive?     > Grub version 0.97-29ubuntu21
Ubuntu version **8.04** AMD64:) Sure, this problem has already been solved by developers in Intrepid Ibex, but you're still using Hardy Heron. 
(Not that there's anything wrong with Hardy Heron, it's a very good 'long term support' release, very stable).

I'm typing to you from a Hardy Heron installation right now. but here's what one of my Hardy Heron boot entries looks like,
```
title        Ubuntu 8.04.1, kernel 2.6.24-22-generic
**root        (hd2,0)**
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=6178d387-9ab5-4f23-a56d-8e0cba0addc3 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet
```One of my other operating systems in this computer is Intrepid Ibex, here'e what an Intrepid Ibex boot entry looks like,
```
title        Ubuntu 8.10, kernel 2.6.27-9-generic
**uuid        4d4939f2-de30-438a-896f-af6a77406eea**
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=4d4939f2-de30-438a-896f-af6a77406eea ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet
```With an Intrepid Ibex style boot entry, you can even boot a USB thumb drive from among a whole bunch of other thumb drives attached to USB hubs, the boot loader will look for the right disk and the right partition by the file system UUID number and boot the right one.

I think probably you'll just need to upgrade your /boot/grub/stage2 file to an Intrepid Ibex version of the same, and re-install GRUB. I'm pretty sure I did that recently in one of my other computers here and it worked fine, (better actually).

Maybe you should wait while I test the idea once again just to make certain I'm giving you the right advice before you do anything though. :)

---

### Post by Herman on 2008-12-29
:D I rebooted first and tried the uuid command in CLI mode GRUB in my Dedicated GRUB partition, then in my Interpid's GRUB, (both of those supported the UUID command), then Hardy Heron. I got Error 27: Unrecognized Command, from Hardy's GRUB.

I boot Hardy and copied the /boot/grub/stage2 file from my Intrepid Ibex installation to my /boot/grub/ in Hardy to overwrite Hardy's stage2 file for GRUB.

Then I rebooted without re-installing GRUB , (just for fun), and sure enough, I got 'Starting up . . . 
GRUB_
,with a blinking cursor that just sat there....
(I knew that would happen), LOL!

So, I rebooted and this time I re-installed GRUB first from the command line and booted.

I opened /boot/grub/menu.lst and changed my old Hardy style [boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#title_") to an Intrepid Ibex type boot entry (uuid  4d4939f2-de30-438a-896f-af6a77406eea).
And I also edited the line that says '[# groot]("http://users.bigpond.net.au/hermanzone/p15.htm#groot")[=]("http://users.bigpond.net.au/hermanzone/p15.htm#groot")', to make the changes persistent over any kernel updates.


Then I rebooted again and got Error 15: File not found.

I booted by a different kernel and ran 'sudo update-grub and that seems to have fixed it. I have rebooted a couple of times more just to be sure and everything's working the same as far as GRUB is concerned. But If I add or remove hard disks now it won't affect my booting anymore. :D

Now we just need to think about how you can get yourself an Intrepid Ibex stage2 file for GRUB. I could probably send you one, or would you prefer to get one from a repository?, or do you know someone who can give you one?

EDIT: okay, I have attached a compressed (.tar.gz) copy of mine. You can download it if you want, (it's up to you, but it's there if you want it).

---

### Post by Herman on 2008-12-29
:) To make that simpler, because I know my story was a bit convoluted and confusing,  you just download the stage2.tar.gz and move it into your /home/username directory, (home folder).

You right-click on it and click 'extract here', and you should have a file named 'stage2'.

Next, you can open a terminal and copy it to your /boot/grub directory.
If you want to be cautious, you can make a backup of your old one first,
```
sudo cp /boot/grub/stage2 /boot/grub/stage2.backup
```Now you can copy your new GRUB to your /boot/grub directory```
sudo cp stage2 /boot/grub/
``` That should do it.

Now your computer will be temporarily unbootable, (at least by the normal way), until you re-install GRUB, so it's probably best to do that right away.
```
sudo grub
``````
find /boot/grub/stage2
``````
root (hdx,y)
```Where: You replace the letters 'x,y' with your hard drive and partition numbers according to GRUB's numbering scheme, for your particular partition arrangement as determined by the 'find /boot/grub/stage2 command you just ran previously.
```
setup (hd0)
``````
quit
```You can now edit your menu.lst file by opening it with your favorite text editor, I use gedit, ```
gksudo gedit /boot/grub/menu.lst
```Change the 'root (hdx,y)' number to 'uuid  (followed-by-the-string-of-characters)', which in most cases can be simply copied from the line immediately below the line you're editing, (unless you have a separate /boot partition).
Also replace the (hdx,y) numbers further up the file, after the '# groot' command,[ like this]("http://users.bigpond.net.au/hermanzone/p15.htm#groot"), that's to make the changes persistent, otherwise it will revert to the old style after each kernel upgrade, (every time update-grub is run). Double and triple check for any mistakes, and when you're sure it looks okay, save and close the file.

Run update-grub
```
sudo update-grub
```Done! That's it. You should be able to reboot now and you'll have an upgraded GRUB that can now accept UUID numbers. 

If you ever run 'sudo grub-install /dev/sdx,y' though, that will replace your updated stage2 file with the old one again, so just make sure you don't do that, unless you deliberately want to have your old GRUB back. You also have the backup of your older GRUB's stage2 file. You'd need to re-edit your menu.lst file and undo the changes we just made if you did decide to do that. (I don't think you will want to revert to the older software, but I'm just letting you know your options).

I hope those are easy enough instructions for anyone to follow.

Regards, Herman :)

---

### Post by Herman on 2008-12-29
:D Hello, it's me *AGAIN!*
I just thought of an alternative to that whole idea, you could instead use GRUB's 'fallback' command, like this, here's a link about that,  [fallback]("http://users.bigpond.net.au/hermanzone/p15.htm#fallback_1").

To do it that way you would make some extra boot entries with different hard drive numbers, and GRUB will try to boot each one in turn until it finds the one that boots.

That's another way to solve the same problem. :D

---

### Post by ha2ooh on 2008-12-29
Oh my, I think I you just made me blush.

Thank you for making it simple. I thought posts 4 and 5 were very clear. I have 8.10 on a virtual machine so I was able to use my own file.

I simply followed your steps and...

It is working now. I plugged the old disc back in to check and it still booted my good ol' hardy heron ;-)

I only read your last post after that, that is nice too. I am not letting that idea go to waste as I like it... I will set it up that way on my girlfriends computer.

---

### Post by Herman on 2008-12-30
:D Okay, well done! Obviously you're a *power user*!

---

