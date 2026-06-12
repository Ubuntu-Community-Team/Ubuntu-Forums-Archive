---
title: "Accidentially Deleted Dell Recovery Partition"
date: 2010-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gomab2k4 on 2010-04-20
This is the deal. My Latitude 13 came in today, and the first thing I did was update 9.10 to get it up to date. After requesting a reboot, it would not let. Anyhow, I reinstalled Ubuntu, but the Dell Restore tool (or whatever it is called) is no longer there. Is there a way to get the Dell Restore software back? My system came with two CDs...Dell Utilities and Ubuntu 9.10 (Canonical...not Dell issued it seems), but they do not have restore tools on them. Please help. All I want is the Dell Restore option in case I need to restore the computer to its original state.

---

### Post by wilee-nilee on 2010-04-20
Have you looked at the hard drive with either gparted which needs to installed in a Ubuntu installed system. 

This is a confusing post, is this a dell you purchased with Ubuntu only? and how did you reinstall Ubuntu?

---

### Post by gomab2k4 on 2010-04-20
> **wilee-nilee said:**
> Have you looked at the hard drive with either gparted which needs to installed in a Ubuntu installed system. 

This is a confusing post, is this a dell you purchased with Ubuntu only? and how did you reinstall Ubuntu?

I did use GParted, but it is no longer there, and yes, I purchased the laptop from Dell with only Ubuntu installed. I used the Ubuntu CD that came with the computer to reinstall Ubuntu.

---

### Post by LK_gandalf_ on 2010-04-20
I know that the recovery partition is useless if you have your CDs...

I give you an advice, you can create two different partitions, one with mount point / (around 18-20GB will be enough for ubuntu) and one with mount point /home. Both in ext4 or ext3 as you prefer.
This way you always have your data safe, and you can make a fresh installation at every new release. This is the best option to have a working and clean system, because the upgrade system bring almost always problems. Unfortunately at Canonical they don't understand that it's not user-friendly to have a release every 6 months if this come as a completely new release which request such a big upgrade.

---

### Post by wilee-nilee on 2010-04-20
> **LK_gandalf_ said:**
> I know that the recovery partition is useless if you have your CDs...

I give you an advice, you can create two different partitions, one with mount point / (around 18-20GB will be enough for ubuntu) and one with mount point /home. Both in ext4 or ext3 as you prefer.
This way you always have your data safe, and you can make a fresh installation at every new release. This is the best option to have a working and clean system, because the upgrade system bring almost always problems. Unfortunately at Canonical they don't understand that it's not user-friendly to have a release every 6 months if this come as a completely new release which request such a big upgrade.

Love the signature, I am not sure a representation that upgrades almost always bring problems is fair, I think this is your view, I have had very little of any problems from Dapper to Lucid and many other Linux or Debian based OS, other then my own ineptness.

So to the OP there are various ways to do backups, the one described here is a good one, but there are others so you might search the forums or start a thread for help with this. Or hopefully people will post with some of the different methods.

A backup restore partition like you get with a MS OS is unusual in the Linux sphere so to speak. I think Dell has done this so that users who are new to this type of a OS will find in more familiar. And if a new user like me who had to reimage my system 3 times in the first six months of learning would be able to get back to the original install easily, if they are not familiar with downloading the ISO. Three years later now, no reinstalls because of any misunderstanding of the software.

---

### Post by LK_gandalf_ on 2010-04-21
Yes of course (hopefully!) the upgrade doesn't bring problems to every users! But I see that at every release forums became full of topic of users experiencing problems, and many of these end up with a fresh install.
I don't want to criticize the 6-months policy of Canonical, only I think they should find a completely safe method to update the system. 
Something like a default install with two partition (/ and /home), and a wizard which will install freshly the new system affecting only the / partition, keeping the compatible program lists and removing automatically the .folders from the home which can cause problems?
 
In every case, it's imperative (I think) that this become a one-click and 99% safe procedure, otherwise it's better to avoid this frequent updates because they discourage users and request a lot of assistance for normal users (forums + personal experience with many many friends).

Do you have some links to the other methods we can use to do backups, in addition to the / and /home partitioning?
Thank you! ;)

---

### Post by donghui86 on 2010-04-21
This is a confusing post

---

### Post by LK_gandalf_ on 2010-04-30
Have a look at: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333) as a proof of what happens every 6 months....:(

---

### Post by RedRat on 2010-04-30
Unless things have changed drastically in the last 3 years, I think that the Ubuntu disks that ship with Dell computers are just plain old vanilla Ubuntu. I pretty much screwed up my pre-installed Ubuntu 7.10 from Dell and used the accompanying disks (Dell 530n). Found out that they were just the Canonical Ubuntu 7.10. However, back then Dell did not have any special utilities on the machine. I agree that as long as you have the disks, why would you need to complicate your life with a Dell partition.

---

### Post by wilee-nilee on 2010-04-30
> **LK_gandalf_ said:**
> Have a look at: [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333) as a proof of what happens every 6 months....:(

So I am assuming you know the definitions of cause and effect, scientific inquiry, and anecdotal evidence. Using a link like that as proof of anything is not objective in even the slightest way.

This is a site where people come to fix their problems, and is not a valid statistical base for anything, to many outliers and variables, and no demographics.

---

