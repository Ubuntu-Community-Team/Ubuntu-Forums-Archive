---
title: "Recovery Partition"
date: 2009-01-19
forum: General Help
---

### Post by BattleStarJesus on 2009-01-19
I would like to fabricate a recovery partition.  I currently arrange my hard drive in the following manner: / 20GB, /home 76GB, SWAP 4GB.  I would like to configure another partition that would contain a backup image that is regularly updated, perhaps weekly. I would then like to fabricate an option in GRUB enabling me to restore the backup image.  

How do I establish this arrangement?

---

### Post by jimmy the saint on 2009-01-19
As for the backups you could probably work something with partimage and cron. Partimage will copy your Partitions, but leave out any empty blocks so if you are becking up a 40G partition with 10G of data, you will only need 10G of space.  The downside is that you will lose half of your drive.  That and it will do nothing for you if that drive fails since your backup will be on the same drive.  This means you will have to have yet another backup on another drive in order for it to really be a goog backup.

As for the grub thing, I am not sure that is possible.  You would likely need to boot into a live cd or usb installation in order to apply the restore from this type of backup.

---

### Post by indytim on 2009-01-19
I agree with Jimmy 100%.  To elaborate a bit with respect to Partimage, you will need to boot to either another Lx ops or a LiveCD (could be a utility app) and launch Partimage.  You cannot restore your ops (or anything else that is currently mounted from Partimage).  I'd also recommend forgetting the GRUB thinger.  For Partimage, you need to do the restores from within Partimage.

If you can swing the currency, I'd suggest either buying or building an external h/d.  With the dropping prices of h/d's they are becoming quite a bit more affordable.  Do your image backups to that rather than your internal h/d.

I have tried on a number of occasions to do a cron inspired Partimage.  Haven't gotten it work yet.  If you are successful, I'd be very interested in the specifics.

I have put together a somewhat detailed paper on Partimage and related backup items on my web site.  If you're interested, check my sig.

Hope this also helps.

IndyTim

---

### Post by adamlau on 2009-01-19
I prefer to manually run CloneZilla off live media in order to clone partitions to a secondary HD. Not exactly the fastest way to do things, but it works and works well.

---

### Post by BattleStarJesus on 2009-01-20
Your responses are awesome and going to help me a lot, yet there is more I would like to know.  Perhaps others will present additional viable suggestions, information, or experience here. Allow me to elaborate on what it is that I am attempting to achieve.  I am doing what I can to assist my friends and family in their adoption and conversion into becoming familiar with the intuitive dimensional expansion Linux has to share.  Fortunately their anchors to Microsoft are light, as they are not power users, but they still enjoy the full immersion of a PC capable of exploring, discovering, learning, creating, and sharing.

They have entrusted me to retrofit their computers. They are excited that I can provide them with reliable system configurations; as I've talked up Linux quite a bit.  They have lots of questions and are somewhat unsure, but since they have come to know Microsoft as being an unstable platform their willing to explore Linux. They know nothing beyond the user perspective, and have no faith in PC service centers, so I have been awarded the opportunity to introduce them to Linux.

There are four machines at in my workshop that I am configuring:  SibonOX (Xubuntu), ZeXon (Xubuntu), InvenTower (?), and AunTower (Edubuntu).  Currently I am directing attention to SibonOX and ZeXon, as I intend to have the systems back to them by . . . perhaps . . . Thursday (maybe).  My focus is: ease of use, base user functionality (internet, audio, video, dvd, images), stable/reliable, secure, and intuitive user help.  I would like functionality to assist them and perform maintenance, help, or configuration changes through desktop sharing. I want to do what I can to make the computers as "Bullet Proof" as possible.

I was asking about the backup configuration on local drive, because my friends do not have additional hard drives, and it is potentially unlikely they would follow a backup routine anyway.  So if the process was automated and only backed up the core Linux OS files, or after I have their systems configured in a manner to the preferences of their liking, I could make a backup of the install, then in the event of catastrophe (as long as the hard drive is still intact) reinstall the base system.  

What I am thinking when bring Grub into the equation, is having an option in that boots into an operating system on the partition with the backup image.  That OS would function as a means to restore the backed-up disk image.  It would be very simple with limited user functionality, strictly maintenance. An operating system like [[COLOR="RoyalBlue"]SystemRescueCD[/COLOR]]("http://www.sysresccd.org/Main_Page").  

My friends grill me about security issues with Linux.  They ask about firewall and anti-virus software.  I am not sure how to respond, any advice?  What security software should I install on their computers and how should it be configured?

What are effective ways to get people interested in Linux to a point where they will explore it on their own? 

All input is appreciated.

---

