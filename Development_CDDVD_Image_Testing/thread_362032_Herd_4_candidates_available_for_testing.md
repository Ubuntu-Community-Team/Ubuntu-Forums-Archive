---
title: "Herd 4 candidates available for testing"
date: 2007-02-15
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-02-15
List of available candidates: [https://bugs.launchpad.net/ubuntu-iso-tests/+bugs](https://bugs.launchpad.net/ubuntu-iso-tests/+bugs)
(and test tracker)

Instructions: [https://wiki.ubuntu.com/Testing/ReportingResults](https://wiki.ubuntu.com/Testing/ReportingResults)

(some common questions and answers from the Herd 3 round [here]("http://www.ubuntuforums.org/showthread.php?t=350902"))

---

### Post by Remi Rokosa on 2007-02-16
I'm looking forward to testing this latest release.

What sort of changes can I look toward in this release, compared to the latest official distribution I'm using. (Ubuntu 6.10)

Any solid information to suggest 7.04 will support an accelerated desktop by default compatible with my ATI Mobility 9600?

---

### Post by DJNOVA2006 on 2007-02-16
Im currenty downloading the i386.iso Hope the testing goes well

---

### Post by vhaarr on 2007-02-17
First of all, let me note that getting hold of the ISO download link was unbelievably difficult. I can't see why you don't link directly to the download page from the initial post here.

After finally locating it and burning it out, I rebooted and got the shiny menu where I could start ubuntu normally, in safe mode, or boot from the first hdd (and 2 other options I don't remember).

No matter which of the first two options I selected, it started loading with a kind of progress bar that bumped back and forth between its boundaries a few times (a lot of screen flickering from this bar, but not the "ubuntu" text + logo), and after a few "bumps", I got thrown out in to some sort of busybox/ash/something shell with the message

/bin/sh: can't access tty; job control turned off

Or similar.

Ubuntu Dapper and Edgy run just fine on my computer, and so does Windows XP. It's a Pentium 4 HT with a nVidia 7600 GT card, LCD screen, Plextor CD/DVD-RW and an ASUS mainboard, I think.

---

### Post by gnarula on 2007-02-17
**@vhaarr**

when u boot the cd Press F6 key in your keyboard then type the following command:

**noapic nolapic**

It worked for me and should work for you too.

Regards,
Gaurav

---

### Post by DCM36 on 2007-02-17
> **vhaarr said:**
> First of all, let me note that getting hold of the ISO download link was unbelievably difficult. I can't see why you don't link directly to the download page from the initial post here.


well since i also had some trouble finding the page, i'll just go ahead a post the link in here..

[Feisty Herd 4 CD Images]("http://cdimage.ubuntu.com/releases/feisty/herd-4/")

---

### Post by rictus007 on 2007-02-17
Just wondering.... what new features ubuntu 7.04 has?... what is new?

---

### Post by Yeeha on 2007-02-17
People should download desktop install cd it seems, as alternate install cd partitioner aint working at all - [http://ubuntuforums.org/showthread.php?t=336907](http://ubuntuforums.org/showthread.php?t=336907). Too bad that i burned my  alternate iso before reading this thread :) .

---

### Post by Red Knuckles on 2007-02-17
> **DCM36 said:**
> well since i also had some trouble finding the page, i'll just go ahead a post the link in here..

[Feisty Herd 4 CD Images]("http://cdimage.ubuntu.com/releases/feisty/herd-4/")

Thanks. For Kubuntu users:

[https://wiki.kubuntu.org/FeistyFawn/Herd4/Kubuntu](https://wiki.kubuntu.org/FeistyFawn/Herd4/Kubuntu)

---

### Post by vhaarr on 2007-02-17
> **DCM36 said:**
> well since i also had some trouble finding the page, i'll just go ahead a post the link in here..

[Feisty Herd 4 CD Images]("http://cdimage.ubuntu.com/releases/feisty/herd-4/")

Yeah, I didn't do that since I wasn't even sure I had found the correct link. Now I know that I had not. I downloaded the daily ISO build from the 15. Is that basically the same ISO or a completely different one?

Gaurav, I tried with "noapic nolapic", but I was unsure where to insert it at the boot prompt. I booted the CD and clicked F6 I think, and got some edit box where I could edit the boot command, that ended in "--"; I tried inserting "noapic nolapic" after "--" and also removing "--" and adding it directly behind the rest - neither worked, and both yielded the same result a s my original post.

Anyone know what I'm doing wrong?

---

### Post by rictus007 on 2007-02-17
Responding to myself:

[http://www.ubuntu.com/testing/herd4](http://www.ubuntu.com/testing/herd4)

---

### Post by LaneLester on 2007-02-18
> **Yeeha said:**
> People should download desktop install cd it seems, as alternate install cd partitioner aint working at all - [http://ubuntuforums.org/showthread.php?t=336907](http://ubuntuforums.org/showthread.php?t=336907). Too bad that i burned my  alternate iso before reading this thread :) .
I found a workaround somewhere. Instead of clicking the install icon, use the terminal to enter: ubiquity --old-partitioner

It worked for me when the icon didn't.

Lane

---

### Post by suziequzie on 2007-02-18
> **Yeeha said:**
> People should download desktop install cd it seems, as alternate install cd partitioner aint working at all - [http://ubuntuforums.org/showthread.php?t=336907](http://ubuntuforums.org/showthread.php?t=336907). Too bad that i burned my  alternate iso before reading this thread :) .

This is the first I've heard about a partitioner problem...   But fortunately, I already had my partitions set up before the install, though it did give me a weird message about my vfat junk drive (/junk: an 80 GB HD devoted to storing downloaded crap on it, hence the name) and file sizes being off...  but since I wasn't making changes to that drive, I just clicked "ignore"... or "continue"... can't recall.

Can't stand using the live CD to install, I need to use the alternate.

---

### Post by gh0st on 2007-02-19
Downloading the ISO now can't wait to test herd 4, I tried herd 3 and it was surprisingly stable. Only had a few bugs to report. Let's see what herd 4 has to offer :)

---

### Post by saxin on 2007-02-19
This looks very nice. I really like the "Easy Codec Installation" part. I tried it out yesterday, and it works very well. I'm really impressed :)

---

### Post by majoridiot on 2007-02-20
for those hoping for faster bittorrent downloads, i will be seeding the 
i386 desktop cd from my remote box in approximately 45 minutes...

so feel free to give it a shot if your downloads are slow. :D

---

### Post by randell6564 on 2007-02-20
> **Henrik said:**
> List of available candidates: [https://bugs.launchpad.net/ubuntu-iso-tests/+bugs](https://bugs.launchpad.net/ubuntu-iso-tests/+bugs)
(and test tracker)

Instructions: [https://wiki.ubuntu.com/Testing/ReportingResults](https://wiki.ubuntu.com/Testing/ReportingResults)

(some common questions and answers from the Herd 3 round [here]("http://www.ubuntuforums.org/showthread.php?t=350902"))

HEY ALL!!
Long time since my last post!  Didn't know anything about an upcoming ubuntu release.  (thats how long it's been!) :lolflag: 

Anyway,  Ill be downloading herd4 iso just as soon as I get my own internet connection back.  Believe it or not, I'm currently using a T1 connection and cannot download anything over 5 MB without pulling my hair out!!  (The network Admin is controlling my bandwidth.) ](*,) 

Can't wait though!  UBUNTU ROCKS!!  Keep it up guys!!

---

### Post by PatrynXX on 2007-02-21
That release hates my monitor.  Gives me a nice oval.  Can't be good on my Viewsonic.  Gotta be good ol Nvidia coming back to Haunt me.  :lolflag:

---

### Post by slackern on 2007-02-22
I just wanted to make a quick note that i have had problems with K/Ubuntu before doing installs with my ATi X1950Pro AGP card, it worked from the start now with Kubuntu instead of crashing during loading of KDM/GDM/X and new ATi drivers just came out so experimenting with those now.

---

### Post by Botunda on 2007-02-24
> **Remi Rokosa said:**
> I'm looking forward to testing this latest release.

What sort of changes can I look toward in this release, compared to the latest official distribution I'm using. (Ubuntu 6.10)

Any solid information to suggest 7.04 will support an accelerated desktop by default compatible with my ATI Mobility 9600?


I am in the same boat my friend. Let's keep our fingers crossed. 


Beryl, I long for thee!

---

### Post by pochu on 2007-02-24
No, Feisty Fawn won't ship the ati proprietary drivers by default, so (I think, but correct me if I'm wrong) you won't have direct 3d acceleration by default, as the proprietary are the ones who can do that.

Regards
Pochu

---

