---
title: "Dell 530N: linux n00b impressions"
date: 2008-01-27
forum: Dell  Ubuntu Support
---

### Post by narcissist on 2008-01-27
There seems to be some interest on people&#8217;s impressions on the Dells with Ubuntu preinstalled. My experience with linux is almost zero so a preinstalled option was very attractive when the time came to upgrade so anyone in the same boat may find this interesting. I did not want a PC with vista and seeing &#8220;linux is ready for the masses&#8221; all over the net I though I&#8217;d try.

I went for 530N with 2.66GHz, 1Gb RAM, 320Gb disk. I bought extra RAM elsewhere for *much* less and upped it to 3.5Gb since Ubuntu only uses up to 3.2Gb anyway.
[B]
Initial observations:[/B]

1. Price: The price is the same as a similar PC with Vista on it! This is not good regardless if linux is a niche market or not.

2. Graphics card: No other options and it&#8217;s not exactly a high spec card but I guess it works out of the box.

3. Just 4 SATA connectors. With DVD/CD drives now SATA, this isn&#8217;t really enough imo.


**Up and running:**

After putting in the extra RAM I booted it, set the language etc. a quick warning that it was using a proprietary graphics driver and that was it. I put in an extra SATA disk and DVD drive from my other PC with no issues. Very quiet.

There is an ISO for recovery which I figured it would be a good idea to burn for if/when I messed it up! Unfortunately the ISO is 5,026Mb and so obviously refused to burn onto a normal 4.9Gb DVD. I downloaded another from the Dell wiki ([http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)) which appeared to be the same but 4.2Gb? No idea what the difference is but this worked fine (see later).

A hard wired connection into my router gave an instant internet connection and I picked up my email and downloaded for software using the package manager easily. Very nice!

The Ubuntu DVD that came with it was the stock Ubuntu not the Dell recovery.


**Dual Boot:**

I still wanted XP for Photoshop and possibly other software and wanted to duel boot. I also wanted both OSs on the same drive so that my files could be held on a different physical disk (fully NTFS) now 7.10 can read and write to NTFS. Both OSs can then access my files no problem. Ideally windows should have gone on first but I ploughed ahead anyway with a guide from the net. 

Due to the utilities, recovery partition and ones needed for ubuntu creating another partition was not possible due to the limit being 4 for windows. 

After deleting the 2 FAT recovery partitions, shrinking the linux partition and making an NTFS one, windows would not install into it when it rebooted after copying setup files from the CD no matter what I did in the boot menu or partition boot settings.

Having made a mess I formatted the drive, installed XP, set up the partitions manually using the livecd and then installed ubuntu again from the ISO off the Dell wiki. The new Ubuntu install had everything the old install had with no drama &#8211; nice one Dell.


**Wireless**

This appears to be the achilles heel of desktop linux. I didn&#8217;t even bother with my linksys USB adapter given what I had read. 

The problem is made worse given that manufactures frequently change chipsets so there is no way of knowing which driver to use and even then there is messing around with ndiswrapper and other voodoo. USB seems like a non starter too.

Almost everyone I know uses wireless and it is a very serious problem getting drivers to work. DELL, WHY NOT PUT A WIRELESS CARD IN THESE PCS????? Everything else works out of the box which is great but with no internet a PC is almost useless these days and hard connections are not a solution. People will not buy a PC which requires all manner of knowledge and messing around just to use their home wireless network.

On further research it appeared anything with the Atheros chipset seems to be the thing to have given it has native support. I got a TP-Link card off ebay for £2.50 based on this chipset. 


**Dual monitors**

I have used dual  monitors for a few years now and apparently 7.10 had some neat tool making setting this up really easy&#8230;.yeah right! 

1. I checked that it could use each screen individually first and then tried the tool. With both screens connected it only ever saw 1 screen no matter what I did. Reading stuff online made me think that getting this to work properly was a step too far.

2. A bit of google revealed nvidia twinview setting. I could not find how to get into the nvidia settings tool other than:
```

sudo nividia-settings
```

Some messing around in it enabled twinview to work correctly on reboot after some scary looking colours the first time. There is a known bug that always sees the vga connected screen as primary which means the logon screen comes up on my secondary screen but I can drag the task bars onto the primary. Other than this it works flawlessly with dragging windows over working fine and no programs appearing in the middle of both.

**Overall:**

Pretty impressed. I did not expect this to be trouble free given I wanted dual boot and 2 screens. No wireless is a real letdown however and this needs to be addressed since although a total noob to linux, I consider myself pretty computer literate and I can't see many people going through the messing around with the wireless issue. No idea what the 5Gb ISO is about - I assume a dual layer DVD is needed to burn it to but this is a small issue.

Linux for the masses then? Well it is much much closer given my experience with my new Dell, almost all the software most people will ever need it easily available pre-installed. The digital cameras, scanners, PDAs, webcams that most people have these days may keep people away if these are driver problems.

---

### Post by ghost_ryder35 on 2008-01-27
glad to hear your expierence was pretty good.  Hope to keep hearing great things in the future

---

### Post by MJN on 2008-01-28
Yes, thanks for the write-up - useful info for prospective buyers.

A quick question regarding wireless, I thought Dell offers Belkin wireless adapters (USB) with these machines? One can only assume they would work 'out of the box' with the customised install.

Mathew

---

### Post by narcissist on 2008-01-29
I only noticed wireless routers as options when I bought it from [www.dell.co.uk](www.dell.co.uk), perhaps I missed them. I have also had terrible experience with belkin in the past.

An update on the wireless then:

The card arrived today. I put it in, booted, was prompted for the WEP key and was online! Internet in under 5 minutes - pretty impressive. Native support for the card's chipset means no driver install.

The model of the card is TP-LINK TL-WN550G (got it for £2.50 new off ebay) in case anyone is having wireless headaches or is looking for a card for their new PC. It's not an old or slow card either.

---

### Post by RedRat on 2008-01-30
Well your experience was similar to mine. I got the 530N and it started up out of the box with no problem. Hooked it up to my older Samsung 191T monitor and no problems.

The only problems I had were of my own making. I attempted to download Ubuntu-Studio and ran into an Xserver problem. Ubuntu would not start unless I hit the esc button or f12 and got into the grub menu. Then it allowed a generic version to come up but this allowed the retention of any files I had created or downloaded. After fooling around with this, I basically gave up and re-installed Ubuntu. 

Now Dell shipped a Ubuntu disk with my machine, which I believe is nothing more than the standard Ubuntu you download online. The iso-image that sits on the Dell desktop i found to be too big also, about 5Gb. The Dell ubuntu from the wiki site I also found to be about 4.2Gb. But I installed the one from the Ubuntu disk that Dell shipped. When I re-installed the system, it did appear to have the nvidia restricted drivers on board and running so this disk must have Dell drivers included. After I re-installed Ubuntu from this disk I did not attempt to download Ubuntu-Studio again. .

So far I have not had any problems. I have since downloaded a raft of programs and multimedia from various repositories and my machine is doing very well. I am still trying to find programs in Linux that are the equivalent to Windows programs and have found that most are close  enough to not present any serious problems. There are couple of programs on the Windows side that I wish would be ported over to Linux, but I will survive without them.

I have to admit that I am quite satisfied with the Dell Ubuntu. This is now becoming my main machine. My conclusion is that Linux Ubuntu just plain works! From my standpoint, Dell has a winner here.

---

### Post by MJN on 2008-01-30
A quick question for those of you with the 530N - how do you find the noise level? I appreciate it can be quite subjective, particularly with differing environments, but how would you rate this aspect?

I am considering buying one soon and whilst it's not a show-stopper I am curious as to how these 'new' machines fare in the noise stakes - it will be replacing a 5yr old Dell PIII acting as a home server which runs virtually silently given its relatively low power and low-noise temperature-controlled fans - the noise factor was a major factor in that system but it's less critical now that it doesn't live in a bedroom!.

Mathew

---

### Post by Onesimus on 2008-01-30
Narcissist,

I too had similar problems trying to get two screens working side by side.  I installed sysinfo available from Add/Remove Programs.  This detects the graphics card and then has a NVidia menu where it is relatively easy to set up two screens.

---

### Post by RedRat on 2008-01-30
> **MJN said:**
> A quick question for those of you with the 530N - how do you find the noise level? I appreciate it can be quite subjective, particularly with differing environments, but how would you rate this aspect?


Mathew

OK this machine if very quiet. In fact I sometimes wonder about it. When it first starts, there is a whoosh! then it immediately quiets down so that I hear very little if any fan noise. In fact, I worried that something might be wrong with the machine. Noise level if very low. As I said, I am very happy with the machine and Ubuntu on it.

---

### Post by MJN on 2008-01-31
Great - thanks for that. Given the 'whoosh' it sounds like the fans must be temperature controlled and hence run at the minimum speed required - running full pelt only when first switched on (or, potentially, if the machine was running at full whack continuously).

Mathew

---

### Post by tgrimley on 2008-05-30
> **RedRat said:**
> OK this machine if very quiet. In fact I sometimes wonder about it. When it first starts, there is a whoosh! then it immediately quiets down so that I hear very little if any fan noise. In fact, I worried that something might be wrong with the machine. Noise level if very low. As I said, I am very happy with the machine and Ubuntu on it.

I have three of these (they make good cluster nodes) in my office and they're very very quiet.  I typically have them running full tilt and they are just as quiet--they never get as loud as it is when it starts up (which startled me the first time I booted!!).

---

