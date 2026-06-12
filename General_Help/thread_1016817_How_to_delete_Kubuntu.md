---
title: "How to delete Kubuntu ?"
date: 2008-12-20
forum: General Help
---

### Post by rams123 on 2008-12-20
I have win xp. Then I installed Kubuntu (manual installation). 

Now I want to **delete** Kubuntu from my pc. How to do that ? 

**Can I delete Kubuntu partitions ?** (I'm afraid to do this because - one of my friend done the same , when he restarted computer there is **NO** boot options to select and he again installed kubuntu for that reason)

[CENTER][IMG]http://fumpr.com/images/c5b27ni706eq9i6w6vh7.png[/IMG][/CENTER]

Please help me in this..

---

### Post by bodhi.zazen on 2008-12-20
See this thread :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927) 
 
    wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by Cannaregio on 2008-12-20
I fear that you didn't give enough hard disk space for a thorough Ubuntu testing, is that the reason you want to remove it?
I suggest you'll try  soon or later another, smaller linux distro (TINYME for instance) on those spaces, and so keep them for the moment.

Anyway, to remove, use gparted, see instructions here:
[http://www.howtoforge.com/partitioning_with_gparted]("http://www.howtoforge.com/partitioning_with_gparted")

Also if you really want to completely edit partitions FROM INSIDE windoze, you'll have to use software like "partition magic". 

Mind it, being proprietary software you are supposed to pay for it -alternatively just search for one of its -already regged- free to download copies on the web.

---

### Post by Wisp558 on 2008-12-20
You are right to be cautious. If you slay the Ubu partitions from Win, you will wipe out grub, which will cause ... issues. 

If it breaks like that, I believe there is a command in the Win install recovery console ... Mbrfix, or something like that.

---

### Post by arrange on 2008-12-20
This might help you: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

---

### Post by skern03 on 2008-12-20
IMHO, if you want to dual-boot Linux (any flavor) and XP, it is a far, far better thing to put Linux on a separate drive. Drives are cheap - or if you're like me, you probably have several older drives around gathering dust. I currently have three hard-drives stacked in my box, two dedicated to Linux, one to XP. XP is hd0, and is where grub lives. That makes the whole thing with deleting Kubuntu easy. You just reinstall to the second drive, which whacks the partitions (and in your case, Kubuntu), and you're in biz. That way, you don't adversely affect the XP installation. It's well worth the lack of aggravation now and in the future.

I partition my drives like so: /(root) 5 GB; swap 1 GB; /home (rest of space). Altho if I were to do this again, I'd make the swap partition 2 GB. The reason I put /home on its own partition is so that I can reinstall/upgrade without losing my files and settings.

Even if you have to buy a new drive, they're dirt cheap. My first hard-drive was $400. For 20 MB. (and yes, that is an "m" as in mega-byte). Now you can get 160 GB drives for $50.

---

### Post by bodhi.zazen on 2008-12-20
I believe you can obtain the same results with standard partitioning of a single hard drive. Linux installs need as little as 5 Gb (10 if you wish), so a 160 Gb HD can store 10 distors + a 60 Gb data partition.

Also I suggest a data partition rather then a home partition. Home stores configuration files which may, although rare, conflict across distros. In addition different distros use different UID (Fedora = 500 , Ubuntu = 1000). 

You then use links to $HOME

ln -s /data/music $HOME/music

and on ...

---

### Post by skern03 on 2008-12-20
Re: using a single drive. Even as recently as last week, Ubuntu 8.10 completely whacked a drive during install. It was toast, and only on a reinstall (8.04) with a complete reformat of all partitions was I able to recover it. I sure would rather it whack a drive *not* containing XP since XP is much more of a PITA than Linux to reinstall. I agree you can add 10 distros on a single drive under perfect circumstances, but I'd rather not take take the risk. Circumstances are rarely perfect. So I guess we'll have to agree to disagree on this topic!! ;-)

Tell me more about using a /data partition. That sounds intriguing, especially since I've seen weird things happen with a dual boot of Kubuntu and Ubuntu. So once I create this data partition, do I have to manually create links for each user I add to the system? And for each item, like My Docs, My Music, My Pics, etc.?

Just FWIW, the advice I follow, using a /home partition, is found in many places, not just here but on the Kubuntu forums and in other Linux sites on the web. But if using /data is easier and more reliable, then I'll switch to it, especially since I'm going to purchase a new drive as an xmas present for myself!

> **bodhi.zazen said:**
> I believe you can obtain the same results with standard partitioning of a single hard drive. Linux installs need as little as 5 Gb (10 if you wish), so a 160 Gb HD can store 10 distors + a 60 Gb data partition.

Also I suggest a data partition rather then a home partition. Home stores configuration files which may, although rare, conflict across distros. In addition different distros use different UID (Fedora = 500 , Ubuntu = 1000). 

You then use links to $HOME

ln -s /data/music $HOME/music

and on ...

---

