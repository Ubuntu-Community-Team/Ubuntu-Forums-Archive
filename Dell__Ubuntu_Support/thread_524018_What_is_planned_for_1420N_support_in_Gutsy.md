---
title: "What is planned for 1420N support in Gutsy?"
date: 2007-08-12
forum: Dell  Ubuntu Support
---

### Post by soupwell on 2007-08-12
Will the final release of Gutsy Gibbon install and recognize all of the devices on a Dell Inspiron 1420N right out of the box?  

I've seen this question posted numerous times where people are trying to install Feisty from CD/DVD, and are running in to all sorts of issues.  I've never seen a concise, credible reply.

It would seem to make sense that the release would fully support this system.  The 1420N is intended to run Ubuntu, and is made by the manufacturer who has shown the greatest support for the community.  It seems like running perfectly on such a system ought to be a primary goal.

(That and I have one on the way, so I would personally like to see flawless support  :-\" [-o< )

---

### Post by jmnormand on 2007-08-13
i would have to assume the intel graphics and sound will be supported.  seeing as this i a completely new chip set support using feisty out of the box really was not an option.  however over the past month i have seen the intel drivers evolving to full support.  based on the past system i tend to question if the wireless will be supported however as broadcom and linux have traditionally been problematic...

---

### Post by sciurus on 2007-08-14
If you have a 1420, you should follow the tribe cd's for gutsy. For starters, it would be nice to see if the latest will boot.

[http://ubuntuforums.org/showthread.php?p=3169299](http://ubuntuforums.org/showthread.php?p=3169299)

---

### Post by soupwell on 2007-08-14
> **jmnormand said:**
>   based on the past system i tend to question if the wireless will be supported however as broadcom and linux have traditionally been problematic...

What wifi driver does Dell ship on their preconfigured 1420N? Why can it not be included in Gutsy? Is it proprietary?

I will burn a copy of the Gutsy live CD and see if that boots alright.  My estimated ship date is still over 2 weeks away...

---

### Post by aldenhg on 2007-08-14
The best advice I can give anyone is wait until someone more experienced than you muddles through the problems and then upgrade and follow their howto. Personally, I never upgrade to a new release until I've read the forums and I know it works on all the hardware that I use.
Besides, Dell has committed to supporting Ubuntu for at least as long as people have paid for, so they might as well support new releases. With any luck at all there will be some new deb or DKMS packages offered by Dell for Gutsy if there are any incompatibilities.

---

### Post by notwen on 2007-08-14
Feisty is currently running w/o any issues on my pre-loaded 1420n and I likely won't upgrade to Gutsy until I have the time to troubleshoot any issues that may come up.  If anything I can always upgrade from Feisty to Gutsy and if I run into issues restore to factory settings from the GRUB menu. =]

---

### Post by LMP900 on 2007-08-14
> **sciurus said:**
> If you have a 1420, you should follow the tribe cd's for gutsy. For starters, it would be nice to see if the latest will boot.

[http://ubuntuforums.org/showthread.php?p=3169299](http://ubuntuforums.org/showthread.php?p=3169299)

If I recall correctly, the latest Tribe still has problems with the 1420(n) - at least with the Desktop CD.

[Edit] Here's the post that confirms Tribe 4 Desktop CD does not work: [**Clicky**]("http://ubuntuforums.org/showpost.php?p=3162164&postcount=69")

---

### Post by carnagex420x on 2007-08-24
This is a post to confirm that tribe 4 DOES work on the 1420, with exeptions. Wireless doesnt work w/o the broadcom firmware, even then it will only support wifi b. And the Nvidia driver(to whom it may concern) doesnt support the 3d effects because of a kernel issue. Also speakes do not work.

---

### Post by deserthowler on 2007-08-24
I just saw the support for the Intel wireless in my Debain etch repository as new software. \\:D/ If Debian will use it, I see no reason why Ubuntu won't.  Debian doesn't often put new software in a stable repository.

Earl

---

### Post by rfruth on 2007-08-24
Rumor has it various screen sizes are in the works ...[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=11361]("http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=11361")

---

### Post by sebald on 2007-08-24
All I can tell you is that the Gutsy Tribe 5 alternate install works well for me on a straight 1420 in initial tests (just last night!). Feisty disks wouldn't even connect to the hardwired network. So I presume Gutsy is the one that's really aiming for good support for the new Dells.

Gutsy offered a special little control panel to enable some proprietary drivers, one for the nvidia 8400 graphics card (not offered on the 1420n, I think) - but enabling them trashed the system and I had to reinstall. Setting up WEP wireless wasn't smooth but I eventually entered things manually in the networking panel and it works. Haven't tried Bluetooth or audio yet. (Oh, I used the Kubuntu version BTW). The fancier effects in KDE work pretty well, haven't tried any of the fancy 3d things yet... lots to play with.

Stay tuned...

---

### Post by soupwell on 2008-01-15
Gutsy runs out of the box on the 1420N.  Wireless, bluetooth, lan, graphics, all work from live CD.

---

### Post by LMP900 on 2008-01-15
> **soupwell said:**
> Gutsy runs out of the box on the 1420N.  Wireless, bluetooth, lan, graphics, all work from live CD.

I'm using Dell's custom image for my 1420n (Intel graphics) and desktop effects is not working for me. I'm sure there is a workaround somewhere, but it's not really a concern at the moment. Just clarifying that not everything works out-of-the-box.

---

### Post by ghindo on 2008-01-16
> **LMP900 said:**
> I'm using Dell's custom image for my 1420n (Intel graphics) and desktop effects is not working for me. I'm sure there is a workaround somewhere, but it's not really a concern at the moment. Just clarifying that not everything works out-of-the-box.Maybe in Hardy. ;/

---

### Post by notwen on 2008-01-16
> **LMP900 said:**
> I'm using Dell's custom image for my 1420n (Intel graphics) and desktop effects is not working for me. I'm sure there is a workaround somewhere, but it's not really a concern at the moment. Just clarifying that not everything works out-of-the-box.

Unfortunately the Intel X3100 chipset is blacklisted in Compiz.  Check out this [page]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") form Dell's Linux wiki for more info and a workaround.

---

