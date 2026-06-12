---
title: "URGENT HELP NEEDED! Can't get to dual boot!"
date: 2009-05-11
forum: General Help
---

### Post by isa.k on 2009-05-11
[CENTER][COLOR=Red]**[FONT=Arial][SIZE=6]! ! ! URGENT HELP NEEDED ! ! ![/SIZE][/FONT]**[/COLOR][/CENTER]

I know absolutely minimal information regarding Ubuntu/Linux OSs...

I have already posted here regarding the problem, but got no results, so I have started this thread.

As I stated, I know absolutely minimal info about Ubuntu/Linux... other than it is safe, and very tweakable.

I need to run Adobe CS4 Master Collection on my box, so I thought I would run VirtualBox, or something similar on Ubuntu and run Vista off it, so I could use the Adobe suite.

VirtualBox gave me a really small screen, which does no justice to any graphic designer. Anyway, I could not allocate more than 128MB of my 1GB gc to VirtualBox anyway... As for ram issues, that is another thing... I could successfully only allocate just under half my 8GB ram to the virtual box (or was that maximum _upto_ half?).

[SIZE=4][COLOR=Red]**Ok, my conundrum...**[/COLOR][/SIZE]

I have installed Ubuntu a couple of days ago, not realising I would need to dual-boot in the future.

After my problem of not getting the desired results with VirtualBox, I decided to do a dual-boot and run everything on Ubuntu, and use Vista (on the dual) solely for graphic/multimedia design purposes.

So far I have tried Googling for dual-booting, with Ubuntu installed first, and came across these links:

```
http://users.bigpond.net.au/hermanzone/

http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot

http://burace17.wordpress.com/2008/05/28/how-to-dual-boot-windows-vista-and-ubuntu-ubuntu-installed-first/
```I have followed the last link's instructions, as it seemed the most straightforward.

I get stuck on Step #7

I get the error that I can't use that partition to install Vista on...

So, I then added my spare HDD to see if I could install it on that... Same problem!

Mind you, I now have two HDDs in my box. One 320GB SATA with Ubuntu installed onto it. Following the instructions in the above link, I gave my Ubuntu 30GB and the rest was formatted while trying to setup Vista on it.

The second is a 200GB IDE, partitioned (previously) to 150GB/50GB with the jumper set to Cable Select.

**When I select the partition, it says:**
 This computer hardware may not support booting to this disk. Ensure that the disk's controller is enabled in the computer's BIOS menu.
 
 **When I click the Install (or was it the 'Next') button:**
 Windows is unable to find a system volume that meets its criteria for installation.
 
 Now, in light of the first message, I tried looking at the BIOS settings to see if I could get the HDD to be detected manually, and I failed.

I know, you are probably going to say, "Go ask a Microsoft forum!", but I somehow trust the folk here more, than I could any MS forum...

Now, I would like to ask the geeks and/or nerds here at UbuntuForums, if they could please help me resolve my predicament... (btw, I am surprised there are no emotes for "geek" or "nerd" here.. I may have to design one once I get the Vista part running, and run it past Admin here :smile:

I really need to get Vista running on the computer, as I am losing out on time, with graphic design work I am doing at the moment... Or should I have said, on graphic design I am _**unable**_ to do at the moment?

---

### Post by Yvan300 on 2009-05-11
First of all, you won't get a lot of help by disrespecting the guys on the forums, so i suggest to cut it out. When vista said that the disk did not meet the criteria meeant that the first partition is not free for it to use. Most likely you installed ubuntu on that first partition. So what you should do is boot up your live cd, go into gnome partition editor, resize the ubuntu partition so that their is free space in front of it. Then create a primary partition within that free spcae and lets see what happens. 

Cheers

---

### Post by cholericfun on 2009-05-11
this is the first page that comes up searching for dual boot/ ubuntu
why is that one not on your list?

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by isa.k on 2009-05-11
> **Yvan300 said:**
> First of all, you won't get a lot of help by disrespecting the guys on the forums, so i suggest to cut it out. When vista said that the disk did not meet the criteria meeant that the first partition is not free for it to use. Most likely you installed ubuntu on that first partition. So what you should do is boot up your live cd, go into gnome partition editor, resize the ubuntu partition so that their is free space in front of it. Then create a primary partition within that free spcae and lets see what happens. 

Cheers
First of all thank you for your help.

Second of all, I never meant ot disrespect anyone...

If by me referring to members here that know Ubuntu inside out, and Windows as well, as geeks, or nerds, it was honestly meant in an endearing way.

Otherwise, why should I shoot myself in the foot before I even start???

LoL!

Again, thank you for your solution, I will try it now, and let you know if it works... However, do not expect anything soon... the last partition took quite some time...

---

### Post by isa.k on 2009-05-11
> **cholericfun said:**
> this is the first page that comes up searching for dual boot/ ubuntu
why is that one not on your list?

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
I don't know?

I must have been searching specifically for "Windows after Ubuntu Dual Boot" in the title I guess?

Thanks for that link...

It says:

> Installing Windows After Ubuntu

Normally when Windows is installed after Ubuntu the master boot record will be overwritten. This means that you would have to boot off a LiveCD and re-install grub. However, here is an alternative method:[LIST=1]
[*]Create an NTFS partition for windows (using fdisk or whatever tool you are familiar with)
[*]Backup the boot sector e.g. [FONT="Courier New"]dd if=/dev/hda of=/mbr.bin bs=512 count=1[/FONT]
[*]Install windows
[*]Boot into a LiveCD
[*]Mount your root partition in the LiveCD
[*]Restore the boot sector e.g. [FONT="Courier New"]dd if=/media/hda/mbr.bin of=/dev/hda bs=512 count=1[/FONT]
[*]Restart and Ubuntu will boot
[*]Setup grub to boot windows
[/LIST]
Could someone be as kind to translate that for me please?

1. Is creating an NTFS partition for Windows able to be accomplished when installing a fresh copy of Vista (I know, this is potentially not the best of places to ask, but maybe someone out there knows)?

2. With regards to backing up the boot sector... I gather I will do this after I create an NTFS partition.

2b. If I have created an NTFS partition via Vista setup, then I could do that command now, and it should work?

Did I get those bits correct?

**[COLOR="Red"]EDIT:[/COLOR]** I am downloading [**Parted Magic LiveCD 3**]("http://download.cnet.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html") (43.77MB) and the download speed is laboriously slow. It's going to take around 1 hour to download the file! Being 3:23AM here, I think I will head off to bed, and continue this tomorrow morning...

I am looking warmly at **Yvan300**'s solution though... let's see

---

### Post by sTpny on 2009-05-11
Why not just start fresh..? back up your personal files, Install Windows, Install Ubuntu. Thats probably the easiest solution.

---

### Post by cholericfun on 2009-05-11
> **isa.k said:**
> I don't know?

Could someone be as kind to translate that for me please?

1. Is creating an NTFS partition for Windows able to be accomplished when installing a fresh copy of Vista (I know, this is potentially not the best of places to ask, but maybe someone out there knows)?

2. With regards to backing up the boot sector... I gather I will do this after I create an NTFS partition.

2b. If I have created an NTFS partition via Vista setup, then I could do that command now, and it should work?

Did I get those bits correct?

**[COLOR="Red"]EDIT:[/COLOR]** I am downloading [**Parted Magic LiveCD 3**]("http://download.cnet.com/Parted-Magic-LiveCD/3000-2094_4-10663999.html") (43.77MB) and the download speed is laboriously slow. It's going to take around 1 hour to download the file! Being 3:23AM here, I think I will head off to bed, and continue this tomorrow morning...

I am looking warmly at **Yvan300**'s solution though... let's see



ok,
well
1. yes, but use gparted from ubuntu (if youre not in a liveCD go to synaptic and search/ download - it should take 2 minutes)

2. this is not so easy i think... well/ i've never done it
theres a step by step guide what you can do with grub on that webpage which should work like a charm.
(its like 3 commands to type in....)

3. what command?
just install your vista
put the Ubuntu cd in and boot up from there (try ubuntu without any changes to the system OPTION)

then go through the motions with grub ... see webpage

---

### Post by Yvan300 on 2009-05-11
I agree with the start everything all over plan. So what you got to do if you want to back up your information, just create an empty partition using gparted and just transfer all your information there. Then just use the first partiion for vista and when it's installed copy everything from that spare partition or you could just use that partition as your home folder when using ubuntu.

---

### Post by isa.k on 2009-05-11
Oookaaayyy...

Now let me get this straight...

I should start from scratch?

I have painstakingly installed the non-deb drivers to get my graphics card working, alongside other things... I am very reluctant to do a clean install of everything...

Another reason is that my net usage this month shot through the roof, and I am on 96% usage of my 40GB service, and the speed cap won't reset till June 1st. I also downloaded so many packages via Applications>Add/Remove that I just got light-headed from thinking about it...

And finally, on the link provided for dual booting Ubuntu and Windows, it makes it look like it is better to dal boot with Ubuntu installed first...

Anyone out there that got Ubuntu and Vista (or any Windows OS) working after a bit if hiccups, please relay your experiences here so  that we may all learn from them.


Kind Regards,

**isa**

---

### Post by sir_nasty on 2009-05-12
so do it this way.... use a live cd, partion the drive using partion manager, move the ubuntu partition so that the first 30+gb of the hdd are free, then try to install vista on the first partion(leave it unformatted)

if you don't want to do this then boot into ubuntu, use the partion manager and erase the partion information from your spare/second hdd so it's TOTALLY wiped of all info, then install onto that...

are you booting off the vista cd then doing the install?

---

### Post by isa.k on 2009-05-12
That sounds great!

So, once live cd has created the extra partition, it will not format it or anything?

Ok, I will try this one I believe... Will be back

---

### Post by sir_nasty on 2009-05-12
boot off the live cd and use partition manager to move/resize the partion....

---

### Post by isa.k on 2009-05-12
> **sir_nasty said:**
> boot off the live cd and use partition manager to move/resize the partion....

I just tried that to no avail.

I go to the bit where I could chop and change partitions, and was up against the following:
```

---------------------------------------------------
|DEVICE            | Type | Size      | Used      |
|------------------|------|-----------|-----------|
|     /dev/sda     | ext3 |           |           |
|------------------|------|-----------|-----------|
|        /dev/sda1 | ntfs | 32185 MB  | 13169 MB  |
|------------------|------|-----------|-----------|
|        /dev/sda2 | swap | 274880 MB | 3221 MB   |
|------------------|------|-----------|-----------|
|        /dev/sda5 |      | 13004 MB  | 0 MB      |
|------------------|------|-----------|-----------|
|     /dev/sdb     |      |           |           |
|------------------|------|-----------|-----------|
|        /dev/sdb1 | ntfs | 20974 MB  | Unknown   |
|------------------|------|-----------|-----------|
|        /dev/sdb5 | ntfs | 166161 MB | 3221 MB   |
|------------------|------|-----------|-----------|
|        freespace |      | 16779 MB  |           |
|------------------|------|-----------|-----------|
|     /dev/sdg     |      |           |           |
|------------------|------|-----------|-----------|
|        /dev/sdg1 | ntfs | 500105 MB | Unknown   |
---------------------------------------------------

```

So, I wonder what to do?

Whenever I tried changing the partition, so that /dev/sda1 moveds to after /dev/sda2, it ticks the format box, and I want my partition intact.

Whenever I try changing the /dev/sda2 to go before /dev/sda1, I fail... miserably, I may add.

I am gonna go bonkers!

---

### Post by sir_nasty on 2009-05-12
can you post the exact error you get when you try to install to the second hdd?

or if you want I know a neat way to image/backup your ubuntu install to usb sticks using a live cd on usb....  You could backup your system in tact and then wipe the hdd, put xp on there, then re-image ubuntu back over....

---

### Post by sir_nasty on 2009-05-12
Here's how I backed up my system....

[http://ubuntuforums.org/showthread.php?t=1156356](http://ubuntuforums.org/showthread.php?t=1156356)

---

### Post by isa.k on 2009-05-12
> **sir_nasty said:**
> can you post the exact error you get when you try to install to the second hdd?

or if you want I know a neat way to image/backup your ubuntu install to usb sticks using a live cd on usb....  You could backup your system in tact and then wipe the hdd, put xp on there, then re-image ubuntu back over....
Not anymore I can't...

A dear friend of mine, on another forum coaxed me into installing a fresh copy of Vista on one partition, and Ubuntu on another... Like many people here have been asking me to do...

When I told him of my low DL limit left, he told me to grab all the deb files I DL'ed, from the root>var>cache>apt>archives folder, and to back it up, and to use them again once I re-installed Ubuntu...

[COLOR="Red"]Word of advice to anyone else wishing to do this... You must only copy over the deb files to the backup folder you will use. As there is a file called LOCK in there, and if you _*select all*_ and try to copy that into your backup folder, it won't let you.[/COLOR]

I am nearly done finishing my Vista setup, and will move onto installing Jaunty64 when I am done... Actually, I may do a i386 install, as a lot more programs seem to be written for that architecture.

If anyone else has any more advice, please let it come rolling in, as I am sure there would be many others out there that could do with the help.

---

### Post by Bigneil on 2009-05-12
> **sTpny said:**
> Why not just start fresh..? back up your personal files, Install Windows, Install Ubuntu. Thats probably the easiest solution.

I agree.   When i first started experimenting with ubuntu i discovered that a dual boot was much easier if you start out with a fresh install of windows. then install ubuntu from the cd. The cd has all the partitioning tools you need, with easy to follow instructions.  I initially ran into a little bit of difficulty setting up windows as my default OS, But it is very simple when you know how, and if you are unsure what to do, then one us who have done it before can talk you through it.

---

### Post by sir_nasty on 2009-05-12
Ironically enough I just had a random thought and was coming to post when I saw your reply....

What we should have had you do is remove the main hdd with ubuntu, plug in your secondary as the primary.  Then install vista on to that.  Then put your vista drive onto the secondary controller and put your ubuntu back onto the primary.  Then edit grub to boot vista and that would have done it...

---

### Post by isa.k on 2009-05-12
I'm loving it!

Such helpful people :)

Thank you all for your advice.

Even if it is late for me, maybe some other poor fellow may be able to glean something beneficial to them from here. That is enough for me :)

Having had said that, I just booted back into Vista after trying to install Jaunty...

When I came to the partitioning section, I came across this (when I selected it to have Ubuntu installed on):
> **No root file system.**

[I]No root file system is defined.

Please correct this from the partitioning menu.[/I]

So, now I wonder... how do I correct it?


[COLOR="Blue"]**EDIT:**

I wonder, if I use the live cd from Windows... It gives me the option to:[/COLOR]

[[IMG]http://img11.imageshack.us/img11/6946/ubuntuinstall.jpg[/IMG]](http://img11.imageshack.us/my.php?image=ubuntuinstall.jpg)

[COLOR="Blue"]And I am thinking, maybe I should "Install inside Windows"? As the "Demo and full installation" option is what gave me the hiccup...

Could I later do a full install without any hiccups if I take the "Install inside Windows" option?[/COLOR]

---

### Post by isa.k on 2009-05-12
Slowly but surely, I am getting places...

I have installed Ubuntu... but as I have been made aware of, the problem of not being able to boot up has smacked me smack bang, square in the face!

Now I have the error:> GRUB loading, please wait


Error 22And then it hangs!

Hmmm... will I figure this one out by myself again... or will there be faster help this time :P

---

### Post by Yvan300 on 2009-05-12
Concerning your internet usage, you don't have to reinstall all your packages, just back them all up by follwoing the directions stated in this thread [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by sir_nasty on 2009-05-12
try this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by isa.k on 2009-05-13
As I've mentioned before, I did a fresh install of Vista and then Ubuntu...

As per the warning bells rung by everyone, Ubuntu would not start... Actually, neither would Vista!

I started looking for solutions, and followed the link provided by **sir_nasty**, and still non results...

Now I am at my wit's end, and frantically looking for solutions, as work is piling up, and I can't do anything about it!

A friend who happens to be a SysAd, quite well versed with Linux and Windows, helps me over MSN till he has to go to bed...

I dunno how I managed, I promise I only followed instructions from  the link, but I somehow ended up showing the system I had two SATA HDDs! When I had one SATA, and one IDE... Dunno if that impacted on the greater scheme of things  though.

Nearing the end of our session, he asks me to just chuck in the Vista disc, and to fix the (some four or five lettered acronym), and then I would be able to use Vista at least...

I chucked the disc in, and then selected the repair option, and the computer says something along the line of the disc not being the same thing the computer wanted? I was like "WHA....???"

Geez... I got severely agitated, and decided to redo everything all over again!

I deleted all the partitions off the 200GB IDE and 320GB SATA HDDs... and only put a second partition back onto the SATA, giving 240GB to Vista, because it is such a hog!

I created an NTFS partition on the SATA's Vista partition, and all of the 200GB IDE.

As for the Ubuntu portion I am saving to install Jaunty on... Using the Vista setup disk, I just deleted the partition prior to creating Vista's NTFS, and left the Ubuntu partition untouched/blank.

I am strongly leaning towards using the second option from the following menu:

[[IMG]http://img11.imageshack.us/img11/6946/ubuntuinstall.jpg[/IMG]](http://img11.imageshack.us/my.php?image=ubuntuinstall.jpg)

Originally, when I installed a fresh copy of Ubuntu a couple of days ago, I selected the first option. I'm just worried, what problems will disk performance being slightly reduced, have upon my Ubuntu use?

Hoping to get a working Ubuntu install soon.

I really appreciate everyone that took the time and effort to read and (at least try to) understand my conundrum.


**isa**

---

### Post by johnlvs2run on 2009-05-13
> **sir_nasty said:**
> What we should have had you do is remove the main hdd with ubuntu, plug in your secondary as the primary.  Then install vista on to that.  Then put your vista drive onto the secondary controller and put your ubuntu back onto the primary.  Then edit grub to boot vista and that would have done it...

I'm in a similar situation and would like to do this.  
My primary hd with linux is sata, and all my old hd's are pata.  
Can I use a pata hd for xp, or is it better to get another sata hd?  
I'd rather not put xp on the same hd as linux.  Thanks.

Hope this is ok with isa.k for me to ask on this thread.  Maybe it will help.

---

### Post by Yvan300 on 2009-05-13
Hey since your having so many problems with windows and ubuntu, why don't you use easy bcd. It is a program that allows you too easily modify windows boot loader to add ubuntu to the list. But to use this effectively, when installing ubuntu at the last option before pressing the install button, click advanced and install grub to the partition that ubuntu is on and not on the hard drive itself.

eg. hd0 (this is the hard drive itself)
    hd0,2( this is a partition that ubuntu may be installed on)

Try your luck, maybe it might work, worked for me at least :)

See ya

---

