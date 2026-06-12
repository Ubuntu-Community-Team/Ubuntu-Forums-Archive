---
title: "Ext4"
date: 2009-04-16
forum: General Help
---

### Post by joey-elijah on 2009-04-16
I will be clean installing Ubuntu when 9.04 hits in less than a week and i was wondering if there are any reasons NOT to install it using EXT4?

I don't use an encrypted home partition or databases. In fact most of my files are on a NTFS partition shared with Windows 7.

Given the benefits of using EXT4 seemingly out weigh the drawbacks i know of, should i go gung-ho and use it?

---

### Post by codeseer on 2009-04-16
Good question. I've heard some rambling here and there saying that it isn't ready. It won't be the default in Jaunty, Ext3 will still be; but it will be an option. In short, I'd like to know myself. :P

---

### Post by paradigm2 on 2009-04-16
> **codeseer said:**
> Good question. I've heard some rambling here and there saying that it isn't ready. It won't be the default in Jaunty, Ext3 will still be; but it will be an option. In short, I'd like to know myself. :P

I've read of problems too.  Some even full on data loss.  However those were mainly a few weeks ago.  Many are now saying that ext4 is mostly fixed now... :unsure:

Even if the major data corruption issues are worked out, I imagine there are minor compatibility issues with some specialised applications which are not yet updated to work with ext4.

I'm holding off for now on my jaunty install but will probably go for it with the Koala release unless there are numerous reports of unfixed problems.  From what I understand one advantage of ext4 is speed, another is that it is almost impossible to significantly fragment with modest disk space free.

---

### Post by callie510 on 2009-04-16
The thing that really stops me from trying out ext4 is the lack of a working Windows driver (I know, I'm sorry) ... I too share all my files with Windows, but I keep them all on ext3 drives and it only works because Windows can read and write to them.

To my knowledge, there is no ext4 driver... right?

---

### Post by zero777zero on 2009-04-16
yea i heard there was some data loss issues.

btrfs cant come soon enuff

---

### Post by notoriousdbp on 2009-04-16
I've had Jaunty since Alpha.  If you're at all worried why not have the root partition as ext4 and have a home partition as ext3.  I've had that set up and ext4 is really quick.  My machine boots up in 15 seconds and routine scans of the root partition take no time at all.

---

### Post by hockeyhead019 on 2009-04-16
ok i know that this is a seperate question but what... in very basic explanation is ext4?... and what are it's benefits...

sorry i know i should search it and stuff but i figured i'd slide my question into a live thread haha :D  

i just want to know because i am considering changing it to ext4 with the next release (Jaunty)

---

### Post by LowSky on 2009-04-16
> **hockeyhead019 said:**
> sorry i know i should search it and stuff but i figured i'd slide my question into a live thread haha :D  


[http://www.lmgtfy.com/?q=EXT4](http://www.lmgtfy.com/?q=EXT4)

Im using it and it seems to work really well. No data loss or other issues.

---

### Post by James_Lochhead on 2009-04-16
I have been using Jaunty (both GNOME & KDE) initially with ext4 and then with ext3. I noticed that Jaunty was randomly freezing, locking up the whole OS so I had to hard crash, using ext3 I do not have this problem.

---

### Post by Therion on 2009-04-16
Phoronix has a pretty easy to follow "Executive Summary" on [Page Nine](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=9) of it's benchmarking report.  You can read all nine pages if you want of course (link goes to summation).

Summary of the Exectuive Summary:  It's a reasonable upgrade.  Nothing in real world performance to jump and down about, but certainly a worth doing.

I've been using it since Alpha 6 and have no complaints.  And just so you know, you DO have to *specifically* format your partition/s using it, ext4 is NOT the default filesystem.

---

### Post by Slim Odds on 2009-04-16
> **paradigm2 said:**
> ...From what I understand one advantage of ext4 is speed, another is that it is almost impossible to significantly fragment with modest disk space free.

The only speed improvement is in file system checking. Otherwise, it not that much different from ext3.

This link is very helpful: [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by Slim Odds on 2009-04-16
> **callie510 said:**
> The thing that really stops me from trying out ext4 is the lack of a working Windows driver (I know, I'm sorry) ... I too share all my files with Windows, but I keep them all on ext3 drives and it only works because Windows can read and write to them.

To my knowledge, there is no ext4 driver... right?

As long as you don't use extents, it's forward compatible with ext3.

This link is very helpful: [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by joey-elijah on 2009-04-19
I've heard you need to reinstall GRUB if you use EXT4 - is this correct? and how exactly do you reinstall grub?!

---

### Post by oldos2er on 2009-04-19
It's my understanding only Grub2 can boot an ext4 partition. You would install it just like any other program, i.e. with your favorite package manager.

---

### Post by cariboo on 2009-04-19
If you are doing a clean install, the correct grub vesion is installed. If you Upgrade, grub will also be updated even if you aren't using ext4. 

I've been using ext4 sice about a week after it became available. The data lose problems have been fixed. 

I have found that over all ext4 is quicker than ext3 in operations, not only disk checking and booting.

Jim

---

### Post by joey-elijah on 2009-04-19
> **cariboo907 said:**
> If you are doing a clean install, the correct grub vesion is installed. If you Upgrade, grub will also be updated even if you aren't using ext4. 

I've been using ext4 sice about a week after it became available. The data lose problems have been fixed. 

I have found that over all ext4 is quicker than ext3 in operations, not only disk checking and booting.

Jim

I'm sold! EXT4 it will be in 4 days time! :)

---

