---
title: "People in &quot;Upgrades and Installation&quot; won't help"
date: 2009-03-02
forum: General Help
---

### Post by Rlad78 on 2009-03-02
[http://ubuntuforums.org/showthread.php?t=1084254]("http://ubuntuforums.org/showthread.php?t=1084254")

I've been sitting here for 2 hours waiting for someone to reply and my patients has run out.
I'm having difficulties understanding the Partitioner in text mode (8.10 Livecd) and the three people who were helping me before seem to have given up on me.

ANY help would be greatly appreciated as I don't want to loose any of my Windows XP data.

EDIT: WHERE ARE ALL THE 14000 ONLINE USERS AT!?

---

### Post by jARLAXL on 2009-03-02
Ok if i understand well now you have defragmented correctly the partition and the problem is that you dont know if you should use guided or manual partition right?

I always use manual. So i advise you to use manual and so you have to create in your free partition the following:
1. a linux swap partition (size about 2-3 times your RAM memory)
2. The rest of the disk space in your free partition should be a primary partition where you should have to mount the filesystem. that is you will choose the "/" (without the ") to be the mounting point.
when it asks you if grub should be installed in master boot record (MBR) say yes.

Edit: and please be a little patient with all the users

---

### Post by Rallg on 2009-03-02
New responses added on the other thread. I also advised manual.

Let's take this topic back to the Installation and Upgrades section...

---

