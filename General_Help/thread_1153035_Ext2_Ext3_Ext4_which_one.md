---
title: "Ext2 Ext3 Ext4 which one"
date: 2009-05-08
forum: General Help
---

### Post by speed32219 on 2009-05-08
Which filesystem would be better to use for a video server?

Nothing fancy, just fast and low overhead.  And I may want to use LVM2 or some form of raid for multiple hard drives for media protection. (Large files 2-15GB)

---

### Post by Chemical Imbalance on 2009-05-08
Ext 3 is stable and dependable while ext 4 is fast, yet too new to heartily recommend.

Your choice.  I'd personally go with ext 4, but it might have risks.

Ext 2 is too old and doesn't have journaling, so I don't recommend that.

---

### Post by raymondh on 2009-05-08
> **Chemical Imbalance said:**
> Ext 3 is stable and dependable while ext 4 is fast, yet too new to heartily recommend.

Your choice.  I'd personally go with ext 4, but it might have risks.

Ext 2 is too old and doesn't have journaling, so I don't recommend that.

speed... no problems so far on ext4.... however, you can't deny the stability and dependability of ext3 .

---

### Post by colau on 2009-05-08
Booting with ext4 filesystem seems faster than ext3.
+1 for ext4.

---

### Post by HuckleSmothered on 2009-05-09
ext4
Using it on two machines and happy with it.
Other distro's have been using it for longer the Ubuntu.

---

### Post by Legace on 2009-05-09
I suggest EXT4, too.
I've been using it for quite a while, and I've haven't had any problem so far :)

---

### Post by edonia on 2009-05-09
I had already 2 times lost some datas after system crash with ext4 :-(
I do not recommend it. Since 6 Years usinf reiser without loosing datas...

---

### Post by umaxtu on 2009-05-09
I'm using ext4 with no problems but the utility that I used to read my Linux drive from windows doesn't seem to support it.

---

### Post by -kg- on 2009-05-09
All in all, I think I personally would suggest ext3 in a video server application.  I have read there are issues with the transfer of larger files on ext4, and while ext4 does seem to be a bit faster (I'm using it in my installation), it isn't ***that** much* faster, and in a server-type environment I would opt for stability more than a little speed gain.

---

### Post by wiznillyp on 2009-05-09
EXT4, if Linus says it is okay, then I agree.  :)

---

### Post by -kg- on 2009-05-12
> **wiznillyp said:**
> EXT4, if Linus says it is okay, then I agree.  :)

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/317781")

[http://bugzilla.kernel.org/buglist.cgi?product=File+System&bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&component=ext4]("http://bugzilla.kernel.org/buglist.cgi?product=File+System&bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&component=ext4")

It's your choice.

---

### Post by deepclutch on 2009-05-13
ext4 if you are a Desktop User.If you are particular ,make a seperate /home partition formatted in ext3 to keep your files.

---

### Post by stathol on 2009-05-13
There's also the "none of the above" option. XFS and EXT4 seem to have pretty comparable performance, but between the two, XFS has been around longer. For now, I suppose that makes it the "safer" option if you're looking for a journaling filesystem with better performance than EXT3 or ReiserFS.

Personally, I'm just going to stick with XFS until things settle down a little more with EXT4, but I'll certainly be considering in the future. It looks like it has at least a small performance lead over XFS, for whatever that's worth.

Either way, I recommend that /boot be formatted ext3 for safety's sake. Everything else can be whatever your personal sense of risk aversion will tolerate :D

---

### Post by dcstar on 2009-05-13
> **stathol said:**
> There's also the "none of the above" option. XFS and EXT4 seem to have pretty comparable performance, but between the two, XFS has been around longer. For now, I suppose that makes it the "safer" option if you're looking for a journaling filesystem with better performance than EXT3 or ReiserFS.
......

I specifically use reiserfs for VMs because it handles smaller quantities of large files better than EXT2/3 which are more optimised for lots of smaller files.

In my tests I got better performance from having my (VMware) VMs in a resierfs environment - and I have no reason to believe that they are "less" safe than EXT3.

---

### Post by stathol on 2009-05-13
For specific usage scenarios, all bets are off as far as performance is concerned. ReiserFS could very well perform better than ext4 or XFS for certain types of access patterns. But just speaking to the *general* case for most desktop users, it's generally the case that ext4 and XFS will be the fastest, but riskiest options, while ext3 and reiserFS will be the slower, but safer options. As with any "which <foo> is the best?" kind of question, answers should be taken with a generous grain of salt ;)

---

### Post by gjoellee on 2009-05-13
EXT 4 is what I have been using since christmas, and I have never had any problems with it

---

