---
title: "Upgrade from 7.10 to 8.04 on Inspiron 530 Failed"
date: 2008-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jrc on 2008-07-09
In January 2008 I ordered my Dell Inspiron 530 desktop with Ubuntu 7.10 pre-loaded. All worked well until a few days ago when I decided to use the Gnome Update Manager to upgrade to Ubuntu 8.04. The upgrade seemed to be going well until it got to the reboot part.

After the reboot passed the GRUB step, I started getting an endless stream of error messages. The messages were identical except for the numbers that preceded each message. These numbers kept increasing. Here’s a sample of the constantly repeating error messages:

[257.024181] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[          ] ata2.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a 0 tag 0 pio 36 in
[          ] ata2.00: status: {DRDY}


I’ve searched the Dell Ubuntu forum for posts describing my problem, but I’ve seen only a few that seem to resemble my problem.  The posting at [http://ubuntuforums.org/showthread.php?t=762257](http://ubuntuforums.org/showthread.php?t=762257) might be similar to my problem, but I'm a little reluctant to go messing around with my BIOS when I don't understand this whole IDE/SATA/RAID issue.  And besides, if the BIOS worked for 7.10, why won't it work for 8.04? 

I'm surprised that I haven't seen this forum flooded with similar complaints because there’s nothing at all special about my installation and I would think that anyone who ordered an Inspiron 530 with Ubuntu 7.10 pre-loaded would be experiencing a similar problem when they try to upgrade to 8.04.

Can anyone point me in the right direction? Phone calls to Dell have only resulted in long waits, endless transfers, and dropped connections.  Thanks.

---

### Post by jbeaunaux on 2008-07-10
I'm a total rookie when it comes to Ubuntu and ran into your same problem with the exact same scenario. When my computer attempted to reboot I got that series of error messages, waited for a bit hoping that things would sort themselves out and then gave up. I shut the computer off by pressing the power button and restarted it after waiting a little. Everything started up just fine and it seems like 8.04 was installed correctly. Since then I've had the error issue crop up frequently when starting my computer. I've tried to figure out what's not working correctly and it seems to be related to the x.org X11R7.3 program which was installed with 8.04. I'm not sure what this program is or does - or even if this is what's causing Ubuntu to crash at start up. I'm hoping that someone might have some more insight about this problem and get us both sorted out!

---

### Post by gbrainin on 2008-07-10
> **jrc said:**
> I’ve searched the Dell Ubuntu forum for posts describing my problem, but I’ve seen only a few that seem to resemble my problem.  The posting at [http://ubuntuforums.org/showthread.php?t=762257](http://ubuntuforums.org/showthread.php?t=762257) might be similar to my problem, but I'm a little reluctant to go messing around with my BIOS when I don't understand this whole IDE/SATA/RAID issue.  And besides, if the BIOS worked for 7.10, why won't it work for 8.04?

I don't fully understand the whole IDE/SATA/RAID issue, either, but I can tell you from experience on my own 530n that I have confirmed that 1) 8.04 simply doesn't work in "IDE" mode, 2) switching modes in the BIOS doesn't appear to have any ill effect, even while you're running 7.10.

As for why IDE mode works with one but not the other, I can say because it's a different kernel, but that doesn't really answer the question, just changes it to "why does one kernel but not the other work in this mode?"  All I can say for certain is that it does, as evidenced by my own experience and several other people in this forum.

However, if you're still reluctant to make the BIOS change, there is another option: add the all_generic_ide parameter to your boot line.  At this point, you'll need to boot from a live CD in order to edit /boot/grub/menu.lst, but once you do add that switch, 8.04 should work happily with the BIOS in IDE mode.  Of course, you need to take the switch out if you decide to make the BIOS switch at some later date.

---

### Post by jrc on 2008-07-12
First of all, thanks to both jbeaunaux and gbrainin for taking the time to respond to my post.  

Jbeaunaux, sounds as if you've been trying to zero in on the exact cause of the problem.  Hats off to you for doing the research.  Gbrainin, you were correct.  I went into the BIOS and changed the SATA Mode from IDE to RAID, and everything was fixed.  I'm wondering whether the RAID setting will cause a problem when I eventually get around to adding a second hard drive, but I suppose that's a problem for another day.

Finally, I would like to express my appreciation to not only you guys, but to the entire Ubuntu community for all the help they give to those of us who are not exactly "power" users, and for the patience they show in working with us.

---

### Post by gbrainin on 2008-07-13
You're welcome, and also I wouldn't worry too much about the second drive.  From what I've read, "RAID" is kind of a misnomer in the BIOS settings, in that there isn't any mirroring/striping/etc. going on at the hardware level.

---

### Post by hansdown on 2008-07-13
Hi people. I can't give any technical help, but from browsing these forums, I've seen countless posts that suggest it is best to upgrade versions from an iso burned to disk than to try a straight version upgrade.

---

### Post by gbrainin on 2008-07-13
Further information:

I've actually got two 530s in my house, upgraded both of them from 7.10 to 8.04 in the past few weeks.  I did one as a fresh install and one through the update manager.  Both worked fine, though the update manager did present a couple of dialog boxes asking about configuration files (only because I had previously hand-edited the files in question).

The problem with doing the fresh install is that, if you purchased a system with 7.10 including DVD playback, I don't think the DVD playback feature will be included.

---

### Post by gbrainin on 2008-07-13
I did some further reading (the Dell manual for the 530), and apparently I was mistaken.  There IS hardware RAID support, but it only takes effect when the BIOS detects that there is more than one hard drive present.

Unfortunately, it appears that Ubuntu (and probably Linux in general) doesn't yet have the software to coordinate with this hardware RAID, so it's not recommended to use it.  My guess (not confirmed by reading or experimenting) is that things will still work so long as you don't go into the BIOS's RAID setup screen.

---

### Post by sethlbrown on 2008-08-02
I've had a similar problem. I've been running 8.04 on an old eMachines and have no problems except for poor performance from an old graphics card when trying to use compiz. I just purchased an Inspiron 530 from Dell loaded with 7.10. When trying to upgrade to 8.04 the upgrade process hung. I was forced to then reboot the machine. It became unbootable. I tried to reboot twice and was left with a black screen. I reinstalled 7.10 from the cd that came with the machine using the main existing partition as root. I attempted another upgrade to 8.04 and this failed as well. I'd like to get 8.04 installed so I can clone my installation from the eMachines system. Assuming everything works after setting BIOS configuration to use RAID, how do I get back all of the Dell extras like lindvd?

---

### Post by RedRat on 2008-08-02
> **sethlbrown said:**
> I've had a similar problem. I've been running 8.04 on an old eMachines and have no problems except for poor performance from an old graphics card when trying to use compiz. I just purchased an Inspiron 530 from Dell loaded with 7.10. When trying to upgrade to 8.04 the upgrade process hung. I was forced to then reboot the machine. It became unbootable. I tried to reboot twice and was left with a black screen. I reinstalled 7.10 from the cd that came with the machine using the main existing partition as root. I attempted another upgrade to 8.04 and this failed as well. I'd like to get 8.04 installed so I can clone my installation from the eMachines system. Assuming everything works after setting BIOS configuration to use RAID, how do I get back all of the Dell extras like lindvd?
Well I too have a 530n and due to trying to install Ubuntu Studio I messed the thing up. Being a Newbie and not having anything really committed to the machine I installed 7.10 from that disk that was included from Dell, but I wiped the disk and did a clean install (wiping out the Dell hidden partition) so I was running vanilla 7.10. It ran fine and Synaptic Manager proposed upgrading to 8.04LTS, I said yea but had no problems in the install except for that RAID issue, luckily seeing that here I quickly changed it in BIOS and things have worked smoothly ever since--knock on wood. I wonder if the Dell partition is giving 8.04 fits (there is a Dell 'hidden' Dell partition with the pre-installed 7.10 on 530ns)?? Did you download the Dell version of 8.04LTS or did you do it from Synaptic?

---

### Post by gbrainin on 2008-08-03
The IDE vs. RAID mode issue does not change depending on whether the extra Dell partitions (hardware testing tools and reinstall) are present.  I've confirmed this on the exact same machine with two different hard drives.

---

