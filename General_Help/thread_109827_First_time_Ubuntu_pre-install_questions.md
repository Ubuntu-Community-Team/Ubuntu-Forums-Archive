---
title: "First time Ubuntu pre-install questions"
date: 2005-12-29
forum: General Help
---

### Post by 30otsix on 2005-12-29
I’m not that new to Linux but I am new to Ubuntu. Up until recently I’ve been using Debian Sarge on older hardware for Linux only machines. A few months ago I was given a new Windows XP Pro box (64 bit), but after playing around with it for awhile I’m ready to get back to Linux. I’d like to try Ubuntu, because its Debian based and I have heard great things about it. In fact I tried it before but the older hardware couldn’t really handle it. Now that I have Windows, I would like to keep an NTFS windows partition around “just in case” but I don’t have any XP install CDs (though I think I could make some). This being the case I have several questions:

1.	Ubuntu vs. Kubuntu – I’ve heard conflicting reports this with comparison. I have heard that Ubuntu is far more stable, and on the other hand that there is no real difference except for the DE. Personally I’m partial to Fluxbox as a second WM so would normally go with Kubuntu. Is there stability difference? 

2.	Install grub to MBR vs. Windows Boot Loader for dual boot - It seems that several tutorials have suggested that I NOT install Grub to the MBR and that I add Linux choice to the windows boot loader via the Boot.ini file. This seems a little backwards to me, but I thought there must be a reason. Is there? 

3.	64 vs. 32 – Never having had an opportunity before, I have never played around with a 64 bit OS, but now I’m thinking why not. I realize this is more of a Linux question than Ubuntu specific, but at this time is there any real advantage to using the 64 version? I’ve heard there are Flash and Java issues, which while not huge, I would like to have. Anything else I should know before going 64 bit?

4.	Ubuntu install for partitioning vs. Qtparted – Is there any reason I shouldn’t let the Ubuntu install do the partitioning? I’ve read many folks suggest using qtparted prior to installation, why? Below are the partitions I would like:

	50 gig NTFS (XP)
	30 gig ext3 (Linux)
	50 gig Fat32 (os share)
	2 gig swap 
	40 gig free (for whatever)
	8 gig (hidden xp recovery)

The part that concerns me is that last 8 gig of the HD that HP used to store the XP recovery instead of providing CDs. Any issues with that set up using Ubuntu install to do my partitioning?

I apologize for the long post but thought I’d get it all out at once (I hope its in the right place). Thanks in advance.

---

### Post by Bachstelze on 2005-12-29
1) It's a matter of tastes, the only difference is the DE.

2) I install GRUB on MBR and it works just fine.

3) 64 will have a little performance gain but there is much less software available for it than for i366 at the moment.

4) Once again, the Ubuntu install partitioner works fine. But I recommend manual partitioning instead of letting the installer do it. Automatic partitioning is highly unpredictable.

---

### Post by Luke771 on 2005-12-29
You dont need such big partitions for the OSes, 10Gig each will do fine, but of course why not to make them bigger, if you dont have disk space problems. My OS partitions are even smaller than that (small hdd), they are about 6GB, plus a 2gig page-file-only WIN partition, I have only the OSes and the installed software on them and I store all my files on the FAT32.
I partitioned the drive with Partition Magic, I think the installer partitioner does fine but it's easier with PM, it is for me, anyway.
I installed Windows first, on the first partition, then Linux on the second partition, the next partition is swap and last is  fat32 , Grub is on hd0,1.
It works great and I am happy with it.
(I tried Linux for the first time less than two months ago and I cant believe what I've been missing all these years)

---

### Post by tlc on 2005-12-29
1. "Personally I&#8217;m partial to Fluxbox as a second WM so would normally go with Kubuntu." - Why? You can install fluxbox in addition to any other WM you're using, KDE, Gnome, Xfce, etc.

2. Grub. Always. 

3. Ubuntu 64 was my first 64bit linux. Too much fannying around to get everything working. Got bored and installed Ubuntu 32 instead. Everything works perfectly, no fannying around. You can also then use arnieboy's automatix script to install a host of other essentials (flash + mplayer plugins, codecs, libdvdcss etc.) with zero effort. It doesn't work with a 64bit setup.

4. For what you want I'd use qtparted off a live cd first. The Ubuntu partitioner is not particularly brilliant or user friendly IMO.

---

### Post by 30otsix on 2005-12-29
Thanks all for the quick responses! So in summary:
1.	No truth the rumor that Kubuntu is more unstable.
2.	GRUB on MBR is the way to go.
3.	Stick with 32 bit…for now.
4.	Pre-partition with live CD (Knoppix)
>  You dont need such big partition for Windows and Linux, 10Gig each will do.You are probably right, never had such a big hard drive before, my last box was 10 gig.

>  1. "Personally I’m partial to Fluxbox as a second WM so would normally go with Kubuntu." - Why? You can install fluxbox in addition to any other WM you're using, KDE, Gnome, Xfce, etc.Its my experience that Fluxbox has better support for KDE tools. Perhaps just an opinion though, never been a huge fan of Gnome.

Any ideas on that last 8 gig of “hidden” recovery space? Should I just burn a few recovery disks and delete it, try to leave it alone, or both? 

Thanks again.

---

### Post by ren wins on 2005-12-29
the guy that got me hooked on linux just got a 64 bit machine and installed debian on it
the only complaint he really has is open office hasnt been ported to 64 yet, neither has flash
and he's been having issues getting 32 bit debian installed

i dont know how ubuntu would be different, but i'd like to know what your results are, so i can share them w/ him

---

### Post by tlc on 2005-12-29
[QUOTE=30otsix]Its my experience that Fluxbox has better support for KDE tools. Perhaps just an opinion though, never been a huge fan of Gnome.

Any ideas on that last 8 gig of “hidden” recovery space? Should I just burn a few recovery disks and delete it, try to leave it alone, or both? 

Thanks again.[/QUOTE]

Fluxbox is just the WM - it will run anything as long as you have the requisite libs installed. I always preferred KDE too, and was intending to install it over gnome, but I've found gnome much improved these days so I haven't bothered yet and probably wont, although I happily run quite a few KDE apps.

If you don't urgently need the space, the 8GB partition wont get in your way - I'd back it up anyway and delete it as and when you need to, if ever.

---

### Post by Lord Illidan on 2005-12-29
Kubuntu hasn't crashed yet for me.. so I think it's a no brainer.

I prefer to install to MBR, it is less problematic.

RE : 64 vs 32 bit, I recommend going 32 bit for now. It has less issues with flash and multimedia codecs, anyway.

---

### Post by rcerreto on 2005-12-29
I found Kubuntu Hoary (5.04) a little rough on the edges.
I read that it has been improved in Breezy so it comes down to a matter of taste now.

Grub in MBR is  OK

To get a real value from 64bits you need to have more than 4GB of RAM and/or be running specific applications (large RDBMS for instance).
What I'm saying is that 64 bits are mainly for servers.
On the other hand several 32 bits applications are tough to run.
Bottom line: I've an AMD64 CPU but I still run it 32 bits.

I never liked authomatic partitioning but you don't really need to partition your disk in advance. If I'm not wrong you can get control of partitioning during the install process.

---

### Post by sciurus on 2005-12-29
[QUOTE=30otsix]
1.	Ubuntu vs. Kubuntu – I’ve heard conflicting reports this with comparison. I have heard that Ubuntu is far more stable, and on the other hand that there is no real difference except for the DE. Personally I’m partial to Fluxbox as a second WM so would normally go with Kubuntu. Is there stability difference? 

In my experience, parts of KDE do crash more frequently than parts of Gnome. However, KDE is a bit snappier. I stick with Gnome on my main desktop because I like the art better and because I mainly use applications written with GTK. Why waste memory on QT libaries when I'm mostly running Firefox, Thunderbird, OpenOffice, GIMP, etc.

[/QUOTE]

[QUOTE=30otsix]
4.	Ubuntu install for partitioning vs. Qtparted – Is there any reason I shouldn’t let the Ubuntu install do the partitioning? I’ve read many folks suggest using qtparted prior to installation, why? Below are the partitions I would like:

	50 gig NTFS (XP)
	30 gig ext3 (Linux)
	50 gig Fat32 (os share)
	2 gig swap 
	40 gig free (for whatever)
	8 gig (hidden xp recovery)[/QUOTE]

The Ubuntu partitioner works fine as long as you do it manually. You certainly don't need that much space for the Linux partition, and probably don't need it for Windows either unless you plan on instaling **lots** of games. Right now the used space on my root aprtition is under 4GB, and I've had Windows in a 10GB partition for years. What I would highly recommend is that you creat a seperate partition for /home so you can wipe out / without losing your program settings.

---

### Post by seashell11 on 2005-12-29
I just bought a new compaq computer and install ubuntu dual boot. When I installed it I used ubuntu's partition manager to resize my partition and make all my other partitions for me. After that the Ubuntu worked, but I couldn't access my ntfs partition, nor could I boot into windows. I then ran my windows restore cd's which reformated the hard drive to its originall state and windows ran fine. Then I started up with Ubuntu Live CD and partitioned the hard drive with Gparted, rebooted and installed Ubuntu and everything worked fine.

---

### Post by Substance on 2005-12-30
[QUOTE=seashell11]I just bought a new compaq computer and install ubuntu dual boot. When I installed it I used ubuntu's partition manager to resize my partition and make all my other partitions for me. After that the Ubuntu worked, but I couldn't access my ntfs partition, nor could I boot into windows. I then ran my windows restore cd's which reformated the hard drive to its originall state and windows ran fine. Then I started up with Ubuntu Live CD and partitioned the hard drive with Gparted, rebooted and installed Ubuntu and everything worked fine.[/QUOTE]


Good to hear, im going to try installing Ubuntu dualboot tomorrow (super early Super Early) because the ubuntu setup goes uber slow (for some reason)

---

### Post by 30otsix on 2006-01-04
Just an update: 

Resized NTFS partiiton and set up several linux partions  as weel as a fat32 and swap with qtparted from Knoppix with no problems at all. Installed Ubuntu, Kubuntu64 and Elive on seperate partions allowing each to intall GRUB to the MBR. Only issue here was that once I installed Elive, GRUB lost my Ubuntu and Kubuntu boot options. Fixed that by re-installing GRUB from Ubuntu install disk (there is probably a better way to do this but at the time it seemed easiest). After that no issues, all OSs working fine. 

Thanks for all the help!

---

