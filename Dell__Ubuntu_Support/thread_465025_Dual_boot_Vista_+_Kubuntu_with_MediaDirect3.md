---
title: "Dual boot Vista + Kubuntu with MediaDirect3?"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by Mutiny32 on 2007-06-05
I've got an Inspiron 1505 and It is currently running Vista with MediaDirect 3. I want to dual-boot Vista with Kubuntu and keep the MediaDirect functionality, but I've heard installing anything else that modifies the MBR pretty much hoses the machine. Is there a method to install all three and keep functionality? I understand that Mediadirect won't be able to read from the Linux partitions for music/video, but I don't care about that. Any advice would be appreciated.

---

### Post by Barrius on 2007-06-05
> **Mutiny32 said:**
> I've got an Inspiron 1505 and It is currently running Vista with MediaDirect 3. I want to dual-boot Vista with Kubuntu and keep the MediaDirect functionality, but I've heard installing anything else that modifies the MBR pretty much hoses the machine.

Wrong.  I've installed Ubuntu onto several Vista boxes with no problem.    If for some reason it did hose Vista's MBR simply boot from the Vista CD and repair/write a new MBR.

---

### Post by Mutiny32 on 2007-06-05
> **Barrius said:**
> Wrong.  I've installed Ubuntu onto several Vista boxes with no problem.    If for some reason it did hose Vista's MBR simply boot from the Vista CD and repair/write a new MBR.

MediaDirect is a button on the laptop that boots into a low-power media player based on Windows XP in a 2gb partition on the disk. It handles the MBR. First you install MediaDirect, then you Install Vista.

---

### Post by Jeroen Vernooij on 2007-06-05
Well MediaDirect is crappy anyway so i completely hosed the partition after 5 mins and the key on my laptop is now a hotkey to MythTV frontend.

seriously, MediaDirect is a worthless and ugly piece of crap.

---

### Post by Mutiny32 on 2007-06-05
> **Jeroen Vernooij said:**
> Well MediaDirect is crappy anyway so i completely hosed the partition after 5 mins and the key on my laptop is now a hotkey to MythTV frontend.

seriously, MediaDirect is a worthless and ugly piece of crap.

I'd rather have it for travel, it saves power.

---

### Post by Jeroen Vernooij on 2007-06-05
> **Mutiny32 said:**
> I'd rather have it for travel, it saves power.

Barely

The main power consumers, screen and cpu are still running

CPU load is about the same I'd guess: cpu load in ubuntu with rhythmbox running is near zero.
RAM does take both the same power if it's filled or empty.
and the harddrive is still running and scanning because you play media.


I see no use for MediaDirect (does it even play divx or let's say OGG...?) other than its fast boottime.

Edit: heck, but you should use it if you like it. just saying.

---

### Post by Arcquist on 2007-06-08
I was trying to do this as well (Vista+Kubuntu+MediaDirect) and managed to somehow break the media direct functionality even though I installed Ubuntu using the alternate CD and placed Grub in the same partition as Ubuntu (not the MBR). I used Vista's tool to shrink the vista partition and added Ubuntu to the newly freed up space. Maybe just repartitioning the HD to add the linux partitions in the new space screwed it up...

Looking at how to repair it now it seems like I have to reinstall everything from scratch which is kind of a pain.

> **Jeroen Vernooij said:**
> Well MediaDirect is crappy anyway so i completely hosed the partition after 5 mins and the key on my laptop is now a hotkey to MythTV frontend.

seriously, MediaDirect is a worthless and ugly piece of crap.

What do you mean when you say that key is a hotkey for a MythTV frontend? (I have no experience with MythTV) Do you mean pressing that key will boot into a MythTV setup similar to the way MediaDirect works or is it just a hotkey after you have Ubuntu running? If it lets you boot into MythTV do you have any instructions or a link on how to do that?

Thanks,
-Arcquist

---

### Post by Hypnoz on 2007-06-27
> **Jeroen Vernooij said:**
> Well MediaDirect is crappy anyway so i completely hosed the partition after 5 mins and the key on my laptop is now a hotkey to MythTV frontend.

seriously, MediaDirect is a worthless and ugly piece of crap.

I also would really appreciate a description of how you made this happen. I have never used MythTV but I've seen screenshots and it would definately be interesting to try.

---

### Post by Jeroen Vernooij on 2007-06-28
I meant to start MythTV within Ubuntu (so when ubuntu is running); hopefully that's what you want.
I don't think the button can be programmed to start MythTV when the laptop is off (mythtv can only be started when linux is running; however you can auto-start mythtv when your ubuntu is booting, see: preferences--->session)

You can read a howto here:
[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)
You need to start reading at 'Quick recipe', because starting MythTV isn't a default action in ubuntu (mythtv is an add-on program).

---

