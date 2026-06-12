---
title: "How does the Dell recovery partition work?"
date: 2007-08-17
forum: Dell  Ubuntu Support
---

### Post by aldenhg on 2007-08-17
I've got a Vostro 1400 which came to me without Vista discs. I'm getting kinda antsy about the aging gaming prowess of my desktop with the upcoming release of Bioshock and following it Half-Life 2: Episode 2 and all the great games that go along with it. What I'm wondering is how does the recovery partition work? I didn't nuke it when installing Ubuntu just in case I wanted to bring it back for this exact reason. Will it give me the option of recovering to a specific partition or will I have to dd my Ubuntu partition and then put it back on after the Vista recovery?

---

### Post by notwen on 2007-08-18
From what I understand it's a basic wipe the HDD and re-install Vista.  Once the recovery is finished you should have your laptop back to the way it was when you received it.  My 1420n has a similar recovery option available through the GRUB menu and when I run it, it will wipe any partitions I have created and basically return the laptop to 'like-new'.  I'm not sure w/ your situation.  Perhaps you could check the dell website for a more info.  Good luck. =]

---

### Post by Phurious on 2007-08-20
Normally the recovery partition contains a Ghost (or Ghost-like) image of the hard disk in the state it was shipped.  You can get an option to boot to the recovery partition if you pres F12 during post (I think).

---

### Post by inchaos on 2007-08-23
Yes, it should be F12.  
Regardless of weather you have done away with Vista, if your recovery partition is still intact, you can always return your computer to it's factory shipped state.

Now these new fancy Ubuntu Dells have Linux recovery partitions....what newfangled crazyness, eh?  
Hehe.

---

### Post by r_l on 2007-08-24
> **aldenhg said:**
> I've got a Vostro 1400 which came to me without Vista discs. I'm getting kinda antsy about the aging gaming prowess of my desktop with the upcoming release of Bioshock and following it Half-Life 2: Episode 2 and all the great games that go along with it. What I'm wondering is how does the recovery partition work? I didn't nuke it when installing Ubuntu just in case I wanted to bring it back for this exact reason. Will it give me the option of recovering to a specific partition or will I have to dd my Ubuntu partition and then put it back on after the Vista recovery?

Call Dell and ask for a recovery disk.  I did that and they sent me a recovery disk without charging me - but even if they charge you, it will only cost $10 US .  I did that exactly because I was planning to installed Ubuntu on my Inspiron.  After that I freed up the two hidden partition for Dell restore so I have more space.

---

### Post by erfahren on 2007-08-24
although this may not be *completely* applicable to this thread, I noticed the topic: "Dell Recovery Partition" and wanted to share this.

[Inside the Dell PC Restore Partition](http://www.goodells.net/dellrestore/index.htm) is nothing short of impressive IMO. I actually used his DSRfix some time ago on my Dimension desktop after installing Norton GoBack (never even used the stupid thing) and it screwed up the recovery function. (I since deleted that partition but was glad I found his fix at the time.)

Anyway, he did update his information with a note about Vista.

EDIT:
> 
Call Dell and ask for a recovery disk. I did that and they sent me a recovery disk without charging me - but even if they charge you, it will only cost $10 US . I did that exactly because I was planning to installed Ubuntu on my Inspiron. After that I freed up the two hidden partition for Dell restore so I have more space.

Don't you have the option to burn off a set?

---

### Post by WeeWoh on 2008-04-02
I have a vostro 1000. I want to dual boot vista and kubuntu 64. Dell has used all the primary partitions up so you are basically saying that the recovery partition is not needed? I have the dell recovery disks with it. Also could i make a backup of the recovery partition? I have windows vista buisness.

---

