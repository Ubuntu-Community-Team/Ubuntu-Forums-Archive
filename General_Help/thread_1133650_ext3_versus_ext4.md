---
title: "ext3 versus ext4"
date: 2009-04-23
forum: General Help
---

### Post by porchrat on 2009-04-23
Perhaps this is a strange question, but considering that jaunty jackalope is scheduled for release today and I am definitely going to be getting it, I thought I had better find out.

Which filesystem is best, ext3 or ext4?

I have been very happy with ext3, but I have been reading that ext4 has a nasty habit of losing information if a crash happens in the middle of data transfers.

I am going to be storing rather large files on this system and I would really like to know that they aren't going to be damaged.

I have been happy with ext3 and it has yet to let me down. Is there any benefit in moving to ext4? Is it perhaps faster or more reliable?

Just looking for more information really. Thanks

---

### Post by skymera on 2009-04-23
I've had no trouble with EXT4. 
It's much faster than EXT3 and far more reliable. As I've had over 10 hard shutdowns and the fsck took seconds.

I can't see EXT4 loasing data mid-transfer. It's been thoroughly tested. If it wasn't ready, it wouldn't be "stable".

---

### Post by porchrat on 2009-04-23
> **skymera said:**
> I've had no trouble with EXT4. 
It's much faster than EXT3 and far more reliable. As I've had over 10 hard shutdowns and the fsck took seconds.

I can't see EXT4 loasing data mid-transfer. It's been thoroughly tested. If it wasn't ready, it wouldn't be "stable".

Thank you for the response.

I have read though that if a crash happens in the middle of data transfer, ext4 can truncate the file to zero length, but hasn't yet begun writing the new data to the file, thus resulting in data loss.

However I also read that this was only occurring in late 2008, early 2009 and it seems that a few patches to the ext4 filesystem have solved this. Apparently jaunty ships with these patches integrated already.

I'm glad to hear about personal experiences with ext4, I am very pleased to hear about the speed of fsck, because the volumes I deal with are large and I hate sitting around for fsck to finish (sometimes as long as 15 minutes).

---

### Post by porchrat on 2009-04-23
Wow looked at a few more benchmarks. ext4 is fast to say the least.

This is going to be awesome.

---

### Post by Sef on 2009-04-23
Read this [thread]("http://ubuntuforums.org/forumdisplay.php?f=333") about which file system to use

---

### Post by tlroche on 2010-11-30
> **Sef said:**
> Read this [thread]("http://ubuntuforums.org/forumdisplay.php?f=333") 

Currently that URI ([http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)) points or gets forwarded to the forum front page, not to any thread. Please fix.

---

### Post by whiteman on 2011-03-07
I have been trying for months now to be happy with ext4. Using Jaunty I was able to run a lan with 3 printers..(canon Pixma, HP deskjets(2)) and assorted computers. The Ubuntu Jaunty was the main server. Hardwired to a dlink router i had a win7, and wireless had mac mini, MBPro, two iphones, ipad, 2 windoze laps. One with win7 and one with XP. So as you can see I had a very diverse family here. BUT Iwas able to share files using mainly just NAutilus gksudo filemanager....and my samba GUI tool. Maybe that was overkill. Dont know.
WHEN I UPGRADED TO THE 1st ext4.....My canon printer was gone! When I went to ADD PRTR...it just wasnt there. So I tried turboprint. This worked but it cost 30 bucks and there were problems with the Macs being able to SEE it.
Also I noticed that when I chose COMPUTER in my fileman....it showed a Canon as a disk drive? But no printer of this name. It has some kind of arrangement for using sd things to print from. I print from apps on my computers.
I tried everything up to Lucid. Pulled out lotsa hair. At one point I even had to replace motherbpard on Dell xps 400(Ubuntu). I am sure there was no correlation here haha. 
Soooowhen I decided to start back up again with new motherboard, I wiped HD clean and tried new Lucid. SAME OLED THING. No Canon printer.
I reinstalled with Jaunty..there it was!
But the problem is this...I am unable to use Handbrake, iphones, and lotsa things I used with ext4. There are many good upgrades, updates I am unable to use. All of this to have good sharing and printer usage. 
WHY IS THIS? Can ext and ext4 actually see things so differently? Believe me I have tried EVERYTHING. I did not wanna disable my perfect Lucid install just so I could use my printers. But I saw no ther choice. Also the sharing was undependable.
Is it the ext3? ext4? Is there something so different here? Is there any way to mimic the ext3? Why should it matter? I admit I dont know that much about it. All I know is I can print and share files with Jaunty. I cant with Karmic, Lucid, Meerkat. In fact Meerkat was so screwed up all I ver got with it was a dostype screen. Noway to get "windows""icons" etc. Justa big termnal. Id like to hear anyone else who had similar experiences.

---

