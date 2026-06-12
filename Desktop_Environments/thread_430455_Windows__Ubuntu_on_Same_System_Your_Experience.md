---
title: "Windows  Ubuntu on Same System Your Experience"
date: 2007-05-02
forum: Desktop Environments
---

### Post by victorash on 2007-05-02
Like to hear from people who are running Ubutu and Windows on the same computer. Had any problems, how hard was it to set up dual boot option ? 

Thanks
Alan

---

### Post by chedabob on 2007-05-02
Im having no problems. Got XP Sp2 on one drive, Ubuntu 6.10 Ultimate Gamers Edition on the other drive.

---

### Post by boxercbuk on 2007-05-02
Ubuntu 7.04 and windows xp sp2 both running fine windows is unaffected by anything ubuntu does :)

---

### Post by Rob Alderson on 2007-05-02
Up until about a week ago I was dual booting XP sp2 & Feisty with no problems at all, I'm now 100% Feisty though as a virus managed to get past my protection & killed Windows again, gave me the push I needed to remove Windows totally.

---

### Post by jimeez on 2007-05-02
Running Vista and Ubuntu on the same machine.  No problems whatsoever.  Using Ubuntu almost exclusively at this point.  In fact, if it weren't for World of Warcraft, I probably wouldn't use Windows at all.  ;)

---

### Post by ripleyscat on 2007-05-02
> **victorash said:**
> Like to hear from people who are running Ubutu and Windows on the same computer. Had any problems, how hard was it to set up dual boot option ? 

Thanks
Alan

Dual-booting is simple really, and the good thing is Ubuntu will do the partitioning for you, no need for proprietary partitioning programs! I have XP, Ubuntu 7.04, and SuSE 10.2 on this machine and they all work perfectly, when the system boots it's simple matter of selecting the OS you want for that session.

If you need to read more about partitioning there is a lot of info on the web, or, if your computer is a desktop, you could easily install another HDD and use that for Linux which means no partitioning at all!

---

### Post by defyingthenorm on 2007-05-02
I'm dual booting Vista and Ubuntu 7.04. Only problem was that Vista had to do the partitioning. 

It's been a smooth ride.

---

### Post by notwen on 2007-05-02
Dual booting on 2 separate machines.  Main PC is runnign Feisty + XP and my iBook is running Edgy + OSX.  As far as installation goes, it's very easy and straight forward, you'll just need to know what you're doing during the partitioning section of your install.  Although if you're planning on dual booting Vista and Ubuntu, I believe you'd hafta resize your Windows partition using the windows partitioner before installing Linux.

---

### Post by Steve H on 2007-05-02
I've been dual booting for a while now, and recently upgraded to Ubuntu Feisty from Edgy. As a relative noob to Ubuntu (but not linux) it is very easy to get a dual boot environment up and running. I have had no problems with GRUB, (LILO was a different matter!).

Once ntfs-3g was going as well, there was almost no reason to go in to XP anymore though.

But in general it is XP that messes up the Dual-Boot, not linux.

:)

---

### Post by gb7055 on 2007-05-02
I'm dual booting Ubuntu 7.04 and Windows XP on two of my systems and Ubuntu 6.06(soon to be 7.04) on another system I have. No problems here with dual booting.

---

### Post by kelvin spratt on 2007-05-02
non what so ever

---

### Post by neufelry on 2007-05-02
I only had one minor hiccup where windows would not let me install itself to my second sata drive formatted as ntfs by ubuntu. Even had windows reformat the 2nd drive itself and it would not install so I just unplugged the ubuntu drive for a boot and windows installed fine. Grub config was easy since I had found a howto on my configuration and dual booting and tried out two different grub listings for windows, tried one, didnt work, tried the other, bingo!

---

### Post by sandman55 on 2007-05-02
I started of with a dual boot of XP Pro SP2 and Ubuntu Dapper then upgraded to Edgy then Feisty its all running OK I have edited my Grub menu list to allow Windows to boot first to make it easy for my Wife :)

---

### Post by Calash on 2007-05-02
I have 2 partitions of XP and 1 of Ubuntu on my system.  Used Partition Magic to make the Ubuntu partition, then let it do the rest.  Grub points to the NT boot loader, and that handles the selection between XP partitions.

As far as performance Ubuntu is keeping pace or doing better in most areas.  WoW still runs better on XP, but I have to tweak it.  CoH actually runs better on Ubuntu if I load Fluxbox...lots of free memory :)

---

### Post by orange2k on 2007-05-02
Feisty 7.04 on one HD and windows xp sp1 on the other (bigger) HD.

GRUB manages what I boot - no problem here.

But I am thinking of totally switching to Ubuntu in the near future or at least replacing what is on each drive by installing Ubuntu on the bigger one...

---

### Post by kefir on 2007-05-02
I've been dualbooting on different machines with different distros and both lilo/grub back and forth for years and never had any problem whatsoever.

---

### Post by Shazaam on 2007-05-02
Two drive dual-boot. Xp on one (sda) and Mandriva, Mepis, and Ubuntu on the other (hda). Only problems were my own doing. Oh, and Mandriva likes to hide partitions if you let it.

---

### Post by IainT on 2007-05-02
I did initally dual boot, XP and 6.06.

The thing that I found, and I wonder if anyone else experienced the same, was that booting into XP after being Ubuntu took an age. Ubuntu-Ubuntu, XP-XP or XP-Ubuntu were fine.

---

### Post by jerrylamos on 2007-05-02
I squashed dual boot XP and Ubuntu onto a 20 gb laptop.  The problem was defrag of the XP since Windows uses the scatter to the winds file allocation method.  I did a defrag, then got a defrag from the internet, then finally set XP up to run with no paging since the swap file was allocated way high with lots of space below it.  Then I had to very carefully see how far I could resize XP down without tramping on any files.  Phew, it worked.  I prefer standalone CD Live Gparted for ticklish stuff like this.

Cheers, Jerry

---

### Post by e^(i*pi) on 2007-05-02
I'm dual booting xp pro and 6.06 on my laptop and xp home and 7.04 on my desktop.  Both are working great.

---

### Post by sv87411 on 2007-05-02
One good experience.. one not so good...

The good one. :) 

Wanting to get more exposure to Linux after being a Windows user for more years than I care to remember I decided to setup my laptop as a dual boot Windows XP / Ubuntu.

When I first put Ubuntu on I shrunk my original 120Gb XP SP2 partition to allow for it and installed Edgy. Windows got 80Gb, Ubuntu got 30Gb. Installation went smoothly and I was pleasantly surprised that Grub installed without a hitch and I could successfully dual boot my laptop to both. Also managed to access my Windows partition with a little research and very little pain using ntfs-3g.

Soon realised I was using Edgy more than Windows so as I had the luxury of an identical 120Gb drive for my laptop and it coincided with the Feisty release I decided to bite the bullet and go Linux only! I also wanted to split the partitions into separate ones for / and home so a fresh install of Feisty seemed the best bet.

Removed the old drive as a contingency and installed Feisty on a nice empty 120Gb drive... haven't looked back!


The bad one... :( 

Having moved entirely to Feisty on my laptop I decided to see if I could upgrade a rather chunky PC I use as a file storage server... currently running Windows 2003 using various drives with a large striped array of 2 x 400Gg disks on an motherboard based Highpoint RAID controller. Windows config has worked like this for months now.

Thought I'd dual boot it initially so shrunk main C: Windows partition to accommodate Ubuntu. Went fine. Loaded up CD, booted, kicked off install, partitioned up empty space... while it was installing I noticed that Ubuntu had recognised the 745Gb striped drive... I was curiously surprised, especially as I thought Ubuntu would need 3rd party drivers to see it/ access it....

So I clicked on it..... big mistake. :(     Got an IO error in Ubuntu, nothing more and ignored it. Let Ubuntu complete, restarted server... RAID array BIOS at bootup reports one drive dysfunctional in the array... oops. 4 hours later, still no recovery. Gave up and accepted that data was lost. I know striped arrays are always a risk, but it was shocking that a simple click on a drive from Linux can completely trash an array.

Lost approximately 370Gb of AVIs that I've ripped from my DVDs. No backup.

Oh, and the Ubuntu install didn't even work. No grub, nothing, simply failed to install any form of boot loader and Windows wasn't affected.

So.. the moral.

Dual boot works. It works well. But if you're attempting it on a system that has any data on it that you cherish, make sure you have a backup, or two, or three!  Don't be lulled into a false sense of security like me that just because one setup goes well, all will.

:rolleyes: ya live 'n learn!

---

### Post by orb9220 on 2007-05-02
Yep works great the reason for dual of course is for games and if I or updates breaks my ubuntu.

It is advisable to all to have a dual boot while learning linux and also having a separate /home is nice so when I do a clean install of latest distro I still have all my programs and settings.

winXP 10gb 
/ root 10gb
/home 50gb

second Hd is fat32 setup before ntfsg was widely available. And is home to my movies,pics,music,etc...

---

