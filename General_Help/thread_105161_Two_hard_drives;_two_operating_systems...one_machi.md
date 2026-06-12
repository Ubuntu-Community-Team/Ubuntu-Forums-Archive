---
title: "Two hard drives; two operating systems...one machine"
date: 2005-12-17
forum: General Help
---

### Post by indigoshift on 2005-12-17
Hi,

I searched the forums and found a lot of information on dual-booting Ubuntu and another OS, but none of them seemed to match my situation exactly.  If I'm wrong, please point me to the right forum.  I may have just overlooked something.

The situation:  I was introduced to Ubuntu (and Linux) a week ago, and I absoultely love it.  Using it right now, in fact--installed on a spare HD in my WInXP box.  I would be tickled pink if I could use it as my primary OS from now on, but I have an addiction known as "Battlefield 2".  Well, and Half-Life 2.  And Doom 3.  And even some Counter-Strike...the list goes on and on.

What I'd like to do is this:  turn this machine into the 21st century counterpart of my old dual-boot Amiga 500+ (which is still in tip-top shape, thanks!), which had both the 1.3 and the 3.1 Kickroms installed in it.  That is:  I'd like to run my Ubuntu-installed HD for everyday stuff, but reboot and switch over to the XP HD when it's gaming time.  In short, I'd love to never have to work in XP again, unless it's to load up BF2 or something.  I need my BF2.  :rolleyes: :cool: 

As I've only been doing this for a week, I'm a little foggy on how to do this exactly.  I'm assuming I set the jumpers on my Ubuntu HD to Master; my XP HD to slave, then use GRUB to choose which I'm in the mood for at boot time.  Sounds terribly simple, but I'm not in a situation right now where I can fry a motherboard or hard drive or something and recover from it quickly.  So I'm being (probably over-) cautious.

Any assitance or words of advice would be greatly appreciated.

Note:  I know my way around Amiga operating systems, from 1.2 to 3.9, and I work with XP Pro (client-side) and Server 2003 (with AD) on a daily basis.  I also dabbled frequently in my university's Unix machines, about seven years ago.  So I don't mind a fix that's not "user friendly", but I'll tell you:  This is my very first Linux experience.  So I may be asking a lot of stupid questions. :D 

And I'll answer a question I'm sure is going to pop up quickly:  Why not put Ubuntu on the same HD as XP?

Answer:  Steam, for one.  Don't even ask how many gigs of HD space my CS:S folder is taking up right now.  Dear God Almighty.  Besides, if XP ever pukes, I don't want there to even be a smidgen of a chance that it'll take my Linux stuff down with it.  This way, XP's on it's own piece of hardware, which is a good place for it.

That's it, really.  Thanks!

---

### Post by prizrak on 2005-12-17
Umm sort of a vague description but lets work with that. I assume what you did was install grub into the /boot partition of your Ubuntu install. If that is the case you will not be able to use it to boot Windows w/o some modification to the GRUB. You should actually be able to modify your boot.ini file to have a string that will load Ubuntu. If you want to change which drive boots first just go into the BIOS of your computer it's usually <del>, on Dells its <F2>, some others it's <F3> on my Toshiba laptop it's <Esc>. It generally tells you at boot which key to press to enter the setup. 
This is the link to the GRUB manual [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
And here is how you do it with the NTLoader [http://www.astahost.com/using-ntloader-to-boot-linux-t1510.html](http://www.astahost.com/using-ntloader-to-boot-linux-t1510.html)

---

### Post by dave9191 on 2005-12-17
Hey, 

My suggestion to you is in that order:

[LIST]
[*]Install win xp on your primary hard disk (/dev/hda)
Windows likes to be the only OS on the computer, so rather then fiddeling with work arounds let it have its fun on the first disk
[*]Install Ubuntu on your seconda hard disk (/dev/hdb)
It will detect windows and add it for you to the grub boot loader and it will make Ubuntu your primary / first choice on the list :)
[/LIST]

This is the way the way I used to set up my dual boot machine to save on time and effort. But then I gave up my gaming addiction and now I just have ubuntu :) 

--
Dave

---

### Post by zoiks on 2005-12-17
I'm not sure exactly what you are asking for, because it sounds like you're already set up.  You don't need to bother with the jumper settings on the hard drives (master vs. slave) if grub is already set up to select which OS you want to boot.

AFAICT you just want to change the default OS to boot to be ubuntu instead of XP.

---

### Post by TrinitronX on 2005-12-17
I currently have a dual boot system with XP and Ubuntu running just fine.  I did not have to tweak anything with the hardware, no changing jumpers or anything.
All I did was install the new HDD, boot to the Ubuntu install disc, follow the installer, and when it asked to install grub on the master boot record, I just said ok.  I was a bit reluctant to do that, because I had heard of people having problems having ubuntu and xp on the same HDD, but different partitions.  However, with 2 HDD's, it seems XP is fine with grub being on the MBR.
So... just try a normal install to the second hard drive.

For the partition setup, you need at least a root drive, and a swap drive.  I also added another partition to my setup, which I use as an OS share drive (to easily transfer files from ubuntu->windows, since windows can't mount the ext3 filesystem, but ubuntu can mount windows' ntfs one :P)
Anyways... Either make 2 or 3 partitions (depending on your needs), and make one the ext3 filesystem.  Then make another one (usually anywhere from 1-2 times your amount of ram) the swap partition, selecting 'linux swap' as the type.  Then if you wish to have an OS share partition, use the FAT32 filesystem for it, that way both windows and ubuntu can mount it easily.
I'll leave the size selection up to you.

EDIT: I did this setup for the same reasons you are doing ;).  The only problem is that steam doesn't seem to be working with my account for some unrelated reason though... something to do with my account being bugged so I can't login (some invalid steam ticket messup).
BF2 and other games are still working fine though.  I only wish valve would hurry up and fix my account so steam doesn't think I'm still logged in on another computer.  I think the problem may have been when I copied my steam folder over to my linux drive, and then tried running it under wine.  Hehe.. the program worked... but it didn't actually let me login there either... so that may have caused it :P

---

### Post by indigoshift on 2005-12-17
Sorry, I was in such a hurry earlier that I didn't really specify what condition my machine is in right now, and what I want to do.  Oops.

At the moment, I have 2 hard drives in my machine, but I only hook one of them up at a time.  I did this as a quick fix earlier this week, because I just didn't have time to figure out how to run the machine with both hard drives connected to the mobo simultaneously.

So, I'm on the Ubuntu HD right now.  If I get a wild hair to play some BF2, I turn the machine off, reach inside, unplug the Ubuntu HD, plug in the XP HD, and restart.  Lame, but true.

Now that it's the weekend, I have a little more time, and would like to do this in a little more professional (and slightly less embarassing) manner.

See, this whole Ubuntu thing started out as a fluke:  I stuck it on a spare HD, fired it up, then said "hey, that's cool" and went to bed.  Got home from work the next day (using XP all day, mind you) and couldn't wait to fire up Linux.  In fact, the XP HD in my machine's been unused all week.  However, weekends == video gaming, so I should probably get them both set up.

I hope that makes more sense, and I hope everyone gets a chuckle out of my 1337 h4dw4r3 skillz.  :D 

Sounds like I need to read up on GRUB (thanks for the link)...I have a message at boot that indicates GRUB is running, but I didn't really know what it was until I searched the forums here for dual-booting.

Thanks to everyone for their suggestions so far!

---

### Post by prizrak on 2005-12-18
Can you give more info on how you installed it? Were both of the drives connected at the time? When it asked you where to install GRUB did you choose the MBR (master boot record) or the Linux /boot partition? When you ran the setup did you tell it to auto partition your drive?

---

### Post by fannymites on 2005-12-18
The way I see it.  You installed ubuntu on the spare drive and xp was already installed on the other drive so is untouched by grub or anything.  
Plugging one in then the other will work fine and they will boot as normal, ubuntu will use grub and xp will use it's own mbr.
When both are connected, you can use ubuntu as the primary drive and boot it up then add an entry in grub to point to windows then next time you reboot you will get the choice.
When ubuntu is booted open a terminal and do ```
sudo gedit /boot/grub/menu.lst
```
Then look for the section where the ubuntu entry is and add an entry for windows.  Assuming windows will be the second drive try - ```

title Windows XP
rootnoverify (hd1,0)
chainloader +1
```
Save and reboot.

If that doesn't work try - ```

title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

Sorry if I've misunderstood what you are asking.  This is based on the assumption that you did a default install of ubuntu and grub is installed on the mbr of the ubuntu drive.

---

### Post by indigoshift on 2005-12-18
The Ubuntu HD was originally in another computer, actually, but the ethernet port was bad (and not on a separate card, but rather part of the mobo), which is why it ended up in my XP machine in the first place.

So, neither HD knows the other one exists at the moment, which might make things difficult.

I may just connect both HDs at the same time, put in the Install CD, and reinstall Ubuntu.

---

### Post by exkalibur on 2005-12-18
My recommandation for you : install a removable caddy tray.... All you have to do is switch trays when you want to swap OS....(not hotswap). I've got 3 computers set this way and it makes it soooo easy to swap data drives or Os between machines...
 
Just my two bits
Regards

---

### Post by towsonu2003 on 2005-12-18
seeing that no one recommended this, may be it wont work, but-> plug ubuntu as master winxp as slave and take a look at this [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

I heard from somewhere that win xp likes to be in the first hdd, if so, well, put ubuntu to slave and give [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation) a try. 

But then again, this might make things worse... not sure....... let us know if it works (if you dare to try it that is)..

---

### Post by indigoshift on 2005-12-18
[QUOTE=fannymites]Sorry if I've misunderstood what you are asking.  This is based on the assumption that you did a default install of ubuntu and grub is installed on the mbr of the ubuntu drive.[/QUOTE]

Actually, that sounds like the very thing I was looking for.  I'll give it a try, and let everyone know how it worked out.

Thanks!

And thanks to everyone else, too.  Sorry my description was so spotty--I didn't realize the importance of some of my omissions.

Getting to know this OS has been an interesting experience.  There are times when I've had no doubt as to what needed to be done; other times, it's as if I've never seen a computer in my life.  :D :D

---

### Post by indigoshift on 2006-01-05
Minor update:  Ugh.  Apparently, neither of the hard drives nor the DVD burner want to be a slave.  Everyone wants to be master.

Oh well.  I might just stick Ubuntu on a partition of the Windows HD.

Thanks to everyone for the suggestions.

---

