---
title: "Ubuntu lost its mind?"
date: 2009-10-11
forum: Desktop Environments
---

### Post by ST3ALTHPSYCH0 on 2009-10-11
Well, today I started having the flashing panel issue that's been reported a few times, so I retreated back to windows to use the 'net. I had some time tonight, and logged back into Ubuntu (from the prefix you can see that this is a Wubi install). I started by logging into my wife's account to see if the isses were limited to (a) my account or (b) both accounts that had the OSX treatment. Turns out that hers was fine, so I logged into mine to find no issues whatsoever. Somewhere along the way I logged completely out of my account, then did the same to hers and finally back into mine. The panel was flashing again, so I shut down the machine. Upon reboot I received an error to the effect of "file check failed, must complete manual file check. Logged in as root--read only privileges.", and was promptly (no pun intended) dumped to a command prompt. The last thing I did in my account was backup the default mac4lin main menu icon and replaced it with my own. I uninstalled and am in process of reinstalling the wubi partition, since this is all an experiment in how well ubuntu and I get along, but for future reference, what should I have done in that situation, and what happened anyway?

---

### Post by semitone36 on 2009-10-11
> **ST3ALTHPSYCH0 said:**
> since this is all an experiment in how well ubuntu and I get along, but for future reference, what should I have done in that situation, and what happened anyway?

I dont want to sound like a jerk but IMO Wubi is your problem.  You may just want to install in the traditional dual-boot way.  Ive heard tons of people complain about small problems in Wubi installs.  

Otherwise it could have been a driver problem.

---

### Post by ST3ALTHPSYCH0 on 2009-10-11
You don't sound a jerk in the least... I actually wondered in the beginning if that wouldn't cause me headaches. As to the driver possibility, it had crossed my mind due to the fact that my Nvidia 9800gt card, that was installed when I first installed Jaunty, died Tues and I had to go back to my OB (ATI) GPU. I thought that I had gotten the old drivers cleared away and the new ones installed, but it could've just been an unstable truce. 
I didn't do a traditional install mostly dues to not having enough HDD space on one drive to give Ubuntu enough of a permanent home. When I get a little cash freed up and can get another slave, Ubuntu will definately get a healthy, and well deserved partition.

---

### Post by benmoran on 2009-10-11
I agree. Wubi is really only intended to "test drive" Ubuntu. Once you get to the point where you're install drivers and doing major system updates, its time to give it a dedicated partition. You'll be so much happier. It should be quite a bit snappier as well as more stable.

---

### Post by ST3ALTHPSYCH0 on 2009-10-11
My sleep deprived brain came up with a question to this earlier.... what's the difference between Wubi and a standard install besides the install process and the boot manager used (win boot manager vs. grub)? It seems like after the initial install that ubuntu has it's own little partition, and has full access to the system, so I just don't understand the difference. The sad thing is that I have over 100 Gb free.... it's just that I set such small partitions on one drive (I did this 5 years ago when defrag took so much longer than it does now w/ an OCed 2.5 GHz 4 core cpu) that there's just not enough usable in one spot, I need to look into moving stuff around and then merging 4 of my partitions into 2. That should give me enough room to feel justified in giving a dedicated Ubuntu partition. If I'm storing docs/pics/videos/etc on other partitions and only using the Ubuntu partition for the OS and apps, how big should I make it? Thanks.

---

### Post by nobar on 2009-10-29
> If I store my data elsewhere, How large does an Ubuntu partition need to be?

I just installed Ubuntu Karmic and the base install uses 2.2 GB from the partition.  So, that's basically the minimum space requirement.  Your disk usage beyond that is largely under your control.

I have installed Ubuntu many times, often on partitions of about 6 or 8 GB.  After initial install, Ubuntu's disk usage will swell a bit due to updates and application installations, but these effects will typically be relatively modest.  Also, there are ways of shrinking it back down if necessary.

To answer your question about Wubi vs. normal installs: The disk partition used for Wubi is actually a file under Windows.  That means that Linux has less control over the disk.  This will affect performance and reliability of disk storage.

---

### Post by steveneddy on 2009-10-29
> **semitone36 said:**
> I dont want to sound like a jerk but IMO **Wubi is your problem**.  You may just want to install in the traditional dual-boot way.  Ive heard tons of people complain about small problems in Wubi installs.  

Otherwise it could have been a driver problem.

Or use a virtual machine like VirtualBox.

---

