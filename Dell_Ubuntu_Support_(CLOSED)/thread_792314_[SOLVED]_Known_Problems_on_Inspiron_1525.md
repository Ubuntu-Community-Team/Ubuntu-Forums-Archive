---
title: "[SOLVED] Known Problems on Inspiron 1525"
date: 2008-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Living2007 on 2008-05-12
Im out to buy a Dell Insprion 1525, and want to know before installing 8.04 or above (even through it is not released), are there any current problems with this OS version on this model?

---

### Post by NineKnuckles on 2008-05-18
Dell's [wiki page]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04") has listed three known problems that affect the 1525, with solutions.

---

### Post by Muflon on 2008-05-18
I am typing this on a Dell 1525 and I have no issues with the standard 8.04 release.

See my previous thread on this subject:

[http://ubuntuforums.org/showthread.php?t=758505](http://ubuntuforums.org/showthread.php?t=758505)

Muflon

---

### Post by notwen on 2008-05-18
The link provided by NineKnuckles will eventually also provide custom images of Ubuntu released by Dell for specific machines, including the Inspiron 1525.  You may wish to look at [http://dell.com/open](http://dell.com/open) and compare hardware from the N-Series model to the regular model(that ships w/ Vista) and ensure you have the same hardware to make sure you have hardware Dell covers in their custom images.  =]

---

### Post by shoreline on 2008-05-18
It works great. I bought the exact same laptop last week (in Dubai; without any OS). My only issue was with wireless, but I got it working using this thread:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Everything else, including bluetooth & webcam, worked out of the box. But I have yet to test the performance of the dvd and card-reader, etc.

---

### Post by Ichido on 2008-05-22
I'm very happy with my 1525n.
There was one simple fix for the Wifi LED issue.
Here's where I got my answers:
[http://ubuntuforums.org/showthread.php?t=762770](http://ubuntuforums.org/showthread.php?t=762770)

---

### Post by modena on 2008-05-22
I recently bought a 1525 with similar specs to Muflon (T5750, 2048MB memory, 160GB hard drive, X3100 graphics, Wireless 4965).
Mine has the 1400x900 screen which I think is the perfect res for a 15 inch laptop. I'm from Oz and Dell are the only people I know of that sell us 15" screens with that res.  Mine is 1525 not 1525n.

Mine came with Vista basic.  I removed all the dell partitions (recover / media direct).  I am currently dual booting XP and Ubuntu 8.04.  For what it's worth, I reckon XP works better than Vista on this laptop.

But as for Ubuntu and your question, I had *no* trouble installing 8.04 from the Live CD.  Everything that I normally use worked without a problem - but I have not tried the 1394 and SD/MMC ports.  And I did not even notice that the things on the dell wiki page weren't working.

Just a warning though, the only thing I dislike about the 1525 is the touchpad heat.  It gets so hot that it's extremely uncomfortable to use.  I reckon if there's going to be a hotspot on a laptop, don't put it in the place you touch frequently with your fingertip.  

If possible I would strongly suggest you find a dell demo store and use this laptop model for a while to see if you feel the same.  I got so annoyed I was going to send it back and cop the 15% fee, but then I found that using one of those cheap 3 fan usb cooling pads underneath the laptop stopped the touchpad from getting too hot. 

Oh yeah, forgot to mention, the touchpad gets noticably hotter using Ubuntu (and linux in general) than XP.  I've seen people talk about this on other linux forums and basically get disregarded as crazy folk because the linux people don't think it sounds right - but it's true.  I've also tried fedora 8 on this laptop and it worked *great* except it made the touchpad even hotter than Ubuntu, so I couldn't keep using it.

I have also noticed that java 'seems' much more sluggish on Ubuntu, but only with UI intensive apps.  If I run a java number crunching app on the laptop it goes faster in ubuntu than xp.  I don't know if that's a driver issue or what.  I mention this because I also have a desktop with xp / mandriva and java on mandriva leaves xp for dead, so I was really suprised at Ubuntu's java performance.

BTW 
- I am using the i386 Ubuntu and 
- I also noticed that the sound is much lower than with xp.

---

### Post by LeoSolaris on 2008-05-23
The sound can easily be upped by going to terminal and typing ```
alsamixer
``` then using the up key to turn up the volume. (select the different items with left/right keys)

I have a 1520, which is nearly the same, just with a lower "top end" specs from Dell. I had them put XP on, and installed 7.10 myself. I did an upgrade to 8.04 and to tell you the truth, the fresh install of 8.04 worked better than the fresh install of 7.10. 

PulseAudio allows for finer control over your volume, and the wireless works out of the box. The light still has to be added with the backports from the repo, but tha'ts not a major deal.

The MS card read works in both 7.10 and 8.04, and I have not tried the firewire slot yet because i do not have anything that works with it. 

Everything does work quite well in Ubuntu 8.04 with the 1520, and should be just fine with the 1525, since they are nearly the same.

---

### Post by NineKnuckles on 2008-05-26
> Mine has the 1400x900 screen which I think is the perfect res for a 15 inch laptop. I'm from Oz and Dell are the only people I know of that sell us 15" screens with that res.  Actually I got quite lucky, as I ordered mine from Dell UK earlier in the year and had the 1400x900 option, so I took it.  When I checked back about a week later it was gone.  I've just checked the site now and it's back.  Have to agree though, that res looks amazing on a 15" screen.

> I removed all the dell partitions (recover / media direct).  How did you go about that?  I'm looking to remove the Media partition with Ubuntu 8.10, and have heard alot of people say that their harddrive was wiped when they only had a Linux partition or something.

---

### Post by Living2007 on 2008-05-26
> **NineKnuckles said:**
> Actually I got quite lucky, as I ordered mine from Dell UK earlier in the year and had the 1400x900 option, so I took it.  When I checked back about a week later it was gone.  I've just checked the site now and it's back.  Have to agree though, that res looks amazing on a 15" screen.

  How did you go about that?  I'm looking to remove the Media partition with Ubuntu 8.10, and have heard alot of people say that their harddrive was wiped when they only had a Linux partition or something.
I may not actully get the 1525, but currently, this is my best option.
Thnx 2 all those who replied.

---

### Post by modena on 2008-05-27
Hi NineKnuckles,

Re the partitioning I did on 1525.

I used a liveCD called PartedMagic (running from RAM) and just used the GParted program. I tried partitioning from the Ubuntu LiveCD while I was installing but it didn't work (kept throwing errors).

I decided to repartition the entire disk because I am not familiar with the unusual partition that Dell do (I think it was two primary paritions and one invisible partition on my laptop when it was new).  

So I backed up my data (there wasn't much because the computer was pretty new), and just partitioned the 160G drive into five drives of around 30G FAT32.  First was primary, the rest were extended.

So just to make it clear YES I DID LOSE EXISTING DATA.

1) I installed XP on the first partition.  

2) Initially I installed Ubuntu on the 2nd partition using wubi.  I hope it's not a stoning offence to say this here, but ubuntu actually worked really well with wubi.  The only reason why I decided to reinstall ubuntu on a linux file system was that I was unhappy with the java performance and thought it may be caused by file system.  

3) So I uninstalled wubi, used gparted again to create a SWAP and EXT3(?) file system in one of the FAT32 partitions and installed ubuntu on it.  Easy installation, worked fine as dual xp boot, still wasn't happy with java performance (but I'm not clever enough with java config or ubuntu config to figure out why). I personally can't say I notice an improvement over the wubi installation.

One interesting thing, now when I accidentally press the (left) media direct button instead of the on / off button it just works like the on / off button.  Previously when I had the media direct partition but a non-standard (vista) installation, that button would cause massive problems.

Hope that answers your question.  Take is as experience rather than advice because in case you can't tell, I'm no authority on partitioning.

---

### Post by NineKnuckles on 2008-05-28
Thanks modena that's very helpful, but I'm still unsure on one thing (if you or anyone else knows an answer to this I'd be made-up).  In my situation, I have Ubuntu and Dell's 2 partitions - restore and media direct, plus a 6 GB swap partiton that Dell put on, even though I only have 2 GB of RAM :confused:.  So I'm basically saying that I don't dual-boot, and I want to keep it that way.  I'm sure I read somewhere (it could very well be ubuntuforums) that when the media direct button is pressed (from an off state), and it only finds a linux filesystem, your harddrive gets trashed!  So if your method wipes Dell's 'hidden' partion thing, I persume the same method could work for me.  Thanks again though, as I have plenty of time until October to research this whole situation and see if Gparted can help with my specific situation.

---

### Post by Sand Lee on 2008-06-23
> **modena said:**
> 
Just a warning though, the only thing I dislike about the 1525 is the touchpad heat.  It gets so hot that it's extremely uncomfortable to use.  I reckon if there's going to be a hotspot on a laptop, don't put it in the place you touch frequently with your fingertip.  

Oh yeah, forgot to mention, the touchpad gets noticably hotter using Ubuntu (and linux in general) than XP.  I've seen people talk about this on other linux forums and basically get disregarded as crazy folk because the linux people don't think it sounds right - but it's true.  I've also tried fedora 8 on this laptop and it worked *great* except it made the touchpad even hotter than Ubuntu, so I couldn't keep using it.

BTW 
- I am using the i386 Ubuntu and 
- I also noticed that the sound is much lower than with xp.

I had this problem when running 32-bit hardy. When I installed the 64-bit version, my 1525 runs just as cool as it does in Vista.

---

### Post by Karpah on 2008-09-29
> **NineKnuckles said:**
> In my situation, I have Ubuntu and Dell's 2 partitions - restore and media direct, plus a 6 GB swap partiton that Dell put on, even though I only have 2 GB of RAM :confused:.  So I'm basically saying that I don't dual-boot, and I want to keep it that way.  I'm sure I read somewhere (it could very well be ubuntuforums) that when the media direct button is pressed (from an off state), and it only finds a linux filesystem, your harddrive gets trashed! 

This isn't exactly the same as my situation, but I dual-boot Vista and Ubuntu, but I deleted the MediaDirect and the Recovery partitions (taking up too much space on my puny 120GB hard drive!) I did leave the tiny DellUtility partition, though. Now, when I press the MediaDirect button, it just shows the MediaDirect loading screen, then goes a bit quirky, showing the grub menu over the top of the loading screen, but then booting normally.

I can't imagine why it would trash the hard drive - but then again I can't say 100% certain that it won't.

---

