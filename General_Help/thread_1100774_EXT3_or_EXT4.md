---
title: "EXT3 or EXT4?"
date: 2009-03-19
forum: General Help
---

### Post by Prominence on 2009-03-19
Which is better? Is it any faster? Advantages/disadvantages?

---

### Post by kryptikos on 2009-03-19
Well, without trying to sound dumb...it's the next generation of ext and improves on and adds features that ext3 does not have. A good reference point is:

[http://kernelnewbies.org/Ext4]("http://kernelnewbies.org/Ext4")

---

### Post by cros13 on 2009-03-19
I'm running on ext4... encountered several bugs so far...
I wouldn't trust it with anything you can't afford to lose.

---

### Post by bodhi.zazen on 2009-03-19
I am running ext4 without any problems. There have been reports of data loss with unexpected power loss. This is a known bug and a hopefully there will be a fix soon.

---

### Post by Vaphell on 2009-03-19
at the moment there are issues with ext4 - it can wait with saving data (if not explicitly told to do it immediately) to hdd up to 150 seconds (performance optimisation by buffering writes in big chunks, hdd is generally slow device) when ext3 has 5 seconds max. It means in most unfortunate circumstances you can lose data from last 2+ minutes if crash occurs. Also it doesn't perform actions 100% chronologically which is very counterintuitive - reportedly it is possible to update file content and rename it just to find out that rename was performed before actual write (up to minute?), in case of crash you can get new name, old data.
Ext4 is POSIX compliant but devs picked poor defaults which greatly increase risk of data loss in the name of better performance. Ext3 is more appropriate for general public at the moment.

[http://linux.slashdot.org/article.pl?sid=09/03/11/2031231&tid=198](http://linux.slashdot.org/article.pl?sid=09/03/11/2031231&tid=198)
[http://linux.slashdot.org/article.pl?sid=09/03/19/1730247&from=rss](http://linux.slashdot.org/article.pl?sid=09/03/19/1730247&from=rss)

---

### Post by u-ben-tu on 2009-03-20
If I choose to reformat my root partition to ext4, but leave my home partition alone (e.g. ext3), could this problem cause data on the home partition to disappear?

If not, this might be a good compromise. Hopefully, there would still be performance increases, but data remaining on ext3 would be safe.

If that's not the case, then, surely using unpatched ext4 is potentially disastrous as your computer could fry files not only on your system, but on your server or on other networked computers it had access to! :shock:

Can anyone explain which scenario is correct?

---

### Post by bodhi.zazen on 2009-03-20
I think you are over reacting u-ben-tu. I do not see ext4 as something that will cause such wide spread damage and, although some people have had problems, personally I do not see the potential to loose a few minutes of work as a show stopper. Nothing I do is that critical.

I would not use ext4 on a server where the data has to be accurate up to the second, but desktops are, IMO, just fine.

Also, you do not need to re-format, you can mount an ext3 as ext4.

---

### Post by u-ben-tu on 2009-03-20
Thanks bodhi.zazen, but from reading Vaphell's second link to Slashdot, I was under the impression that ext4 could actually delete the old data in a file, not just lose the recent changes. 

[http://linux.slashdot.org/article.pl?sid=09/03/19/1730247&from=rss](http://linux.slashdot.org/article.pl?sid=09/03/19/1730247&from=rss)

[INDENT]Spitzak
"For EXT4, if it crashes, you can get a zero-length file, with both the old and new data lost ... I don't really mind if a crash during this time means I lose the new version of a file. But PLEASE don't lose the old one as well!!!"[/INDENT]

If that's the case, it *is* a big issue (only when a crash occurs of course).

If that's not the case and you only stand to lose the work of a few minutes then, I agree, it's not the end of the world.

What I would really like to know is whether an ext4 root partition can cause this problem on other partitions formatted as ext3, HFS, NTFS or whatever.

---

### Post by bodhi.zazen on 2009-03-20
You will have to decide how big a risk you feel this is to you. I would not as of yet run ext4 on a production server or in an environment where losing data is potentially disruptive.

IMO it is a low risk as it only happens with power failure and any document that I feel is that important is backed up. If you have a document you can not afford to lose you should back up regardless of the OS or file system.

I am not an expert, and he is talking about documents or data that you are currently in use, not randomly wiping data from you HD let alone other partitions or network drives. IMO, I think you are being overly paranoid, but that may in fact be appropriate for your environment.

From your posts I would advise you stay with ext3 which is a perfectly reasonable decision.

---

### Post by binbash on 2009-03-20
ext4 is faster but may contain some bugs.That will be your decision

---

### Post by u-ben-tu on 2009-03-20
bodhi.zazen, sorry if I wasn't clear - I wasn't suggesting that data could be randomly wiped. My concern was that an entire file could be wiped if you have it open when a crash occurs, not just the last few minutes' work. 

Of course, we all back up our files on a daily basis ;), but you could potentially lose a day's worth of work, at least.

I am trying to work out if using ext4 on my root partition would put non-ext4 data at risk if it crashed when I was accessing it (whether that's my home partition, my NAS, my wife's computer, whatever). 

If that's not the case, then surely we have a perfect compromise: Use ext4 on root only and reinstall using ext3 if it proves to be too buggy; however, I'm not going to risk that if there is a chance that it can totally delete data which is not on ext4.

I'm looking for someone more technical than me to set me straight. Hope that makes sense!

---

### Post by bodhi.zazen on 2009-03-20
> **u-ben-tu said:**
> I am trying to work out if using ext4 on my root partition would put non-ext4 data at risk if it crashed when I was accessing it (whether that's my home partition, my NAS, my wife's computer, whatever).

No, why would it ? If you read the technical papers , data loss occurs because ext4 delays writing to the disk. If a power outage occurs there may be data loss on the ext4 partition.

This does not affect ext2, ext3, network drivers, etc. So I see no reason for your concern. the fact that you run an ext4 file system does not affect the other partitions any more then running a ext3 affects FAT or NTFS (just because you run root on ext3 does not mean permissions are supported on NTFS for example).

Again, from the nature of your posting style (it quite clear you find the possibility of data loss unacceptable, so really that right there makes the decision for you, IMO at least), I advise you stay with ext3 for now. Yes, ext4 means data loss on ext4 partitions, including system files on / . If you loose system files on / your system may be unstable or un bootable, depending on the file.


When ext4 is stable enough for your satisfaction, ext3 can be converted to ext4 without having to re format the partition.

---

### Post by 1ronlung on 2009-03-20
*newbie*

Would I be correct in assuming a lot of useful disk utils out there won't be compatible with ext4, and prolly haven't been updated yet ?

Personally, I stuck with Fat32 in Windows for a year until other people had encountered the problems with it.
They're always people out there willing to be ginuea pigs.  I personally can't see the advantage when you can chill and swap over when it's proven reliable ....

---

### Post by u-ben-tu on 2009-03-20
Thanks for clearing that up, bodhi.zazen.

Looks like there are three options then:

[LIST=1]
[*]Play it safe and stick with ext3.
[*]Convert to ext4 and accept the small risk of data loss, plus any other bugs.
[*]Install ext4 on root and keep ext3 on home.
[/LIST]

With option 3, you would get performance increase and other benefits, but if your system crashed, you would not be putting your data at risk and you could simply reinstall your system if it was unstable or unbootable. 

That sounds like a good compromise to me. (Though feel free to correct me if I have misunderstood the technical details.)

---

### Post by bodhi.zazen on 2009-03-20
I think your understanding is good.

Personally I do not see ext4 (or any file system) as blazing fast. 

IMO, when I look at so called benchmarks, they are artificial. do not get me wrong, they are helpful, but really, how often is it I write 10,000 im Kb files to disk then delete them ?

Again, IMO, I look at stability and features. For example if you use ACL, well that right there eliminates several file system.

So I would ask you, what features does ext4 have that you want ? Are you willing to sacrifice stability for testing ?

What I suggest is that you keep your system, including /home, on ext3. Make a test ext4 partition and use it for data.

Make a link(s) :

ln -s /mnt/data/music /home/user/music
ln -s /mnt/data/documents /home/user/documents

and on.

I also suggest you read [jdong's ext4 post](http://ubuntuforums.org/showthread.php?t=973701) as it will show you how to convert ext3 to ext4 as well as keeping it reversible and the point of no return.

---

### Post by u-ben-tu on 2009-03-21
> **bodhi.zazen said:**
> 

So I would ask you, what features does ext4 have that you want?



Yes, good point. And it comes back to Prominence's original question, i.e. what are the advantages/disadvantages of ext4? 

My  understanding was that 9.04 would benefit from general performance boosts, speedier boot times and faster fsck and that this was directly linked to implementation of ext4. 

If the real world differences are negligible, then to rephrase Prominence's question: is there a killer reason to upgrade to ext4?

---

### Post by Neo_The_User on 2009-03-21
EXT4 breaks all the time and if your power goes out while writing date, you're screwed. EXT3 is very difficult to break. I've tried before. Never broke. Well, until I connected the hard drive to 2 power supplies of 350W each. :/

EXT4 is much faster and just pure speed but its terrible because of all the virtual writing that goes on. This is not my opinion. This is all true.

DON'T USE EXT4!

The coreboot (LinuxBIOS) developers all say that ext4 is too unstable due to the virtual writing. 

An article on slashdot said something like, Ext4 works much quicker than ext3 by making it appear as though data is being written to the hard drive when it is in fact, not.

---

### Post by AdemoS on 2009-05-23
But it looks like Theodore Ts'o wrote a patch to fix the ext4 issue mentioned, and Ubuntu 9.04 should have the patch in the kernel:

[http://en.wikipedia.org/wiki/Ext4#Delayed_allocation_and_potential_data_loss](http://en.wikipedia.org/wiki/Ext4#Delayed_allocation_and_potential_data_loss)

---

### Post by VMC on 2009-05-23
> **Neo_The_User said:**
> EXT4 breaks all the time and if your power goes out while writing date, you're screwedIs this just FUD? I've been using Ext4 on Jaunty since it came out and a couple of times I had to power cycle the computer, unrelated to any file systems. Nothing, I mean nothing was lost or stolen. Then I again , maybe I'm just lucky...

---

### Post by bodhi.zazen on 2009-05-24
> **VMC said:**
> Is this just FUD? I've been using Ext4 on Jaunty since it came out and a couple of times I had to power cycle the computer, unrelated to any file systems. Nothing, I mean nothing was lost or stolen. Then I again , maybe I'm just lucky...

No, there have been many bug reports about data loss with ext4. yes, they (typically, but not always) occur with power failures. Yes, many have been patched. And yes data loss with ext4 is rare.

I have had one problem with ext4 (have been using it for some time now). No data loss, but I did need to boot to recovery mode and manually repair the file system.

Since ext4 is so new I am not sure if anyone "knows" the stability as of yet.

---

