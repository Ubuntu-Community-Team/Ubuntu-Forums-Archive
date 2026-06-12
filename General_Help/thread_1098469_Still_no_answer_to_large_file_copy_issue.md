---
title: "Still no answer to large file copy issue?"
date: 2009-03-17
forum: General Help
---

### Post by tgeer43 on 2009-03-17
I posted a more detailed message a while ago. [_[COLOR="RoyalBlue"]Click Here To View It.[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=6856614#post6856614")

The only reply I received was a suggestion to search for a resolution in the many other posts concerning this subject.
Well, I had already done some searching but I redoubled my efforts both here in the Ubuntu Forums and elsewhere on the net. There are indeed many instances of this problem floating around but I've still not found a fix or workaround or even if this bug is being considered for fixing in upcoming Jaunty.

Oversimplified, the problem is this: When copying/moving large files (like movies), whether within the same physical disk or two different disks, the transfers start out pretty fast and then quickly peter out to a slow rate and my fast computer is rendered virtually useless until the lengthy transfer is complete.

If there is any really useful information on the subject would someone please be so kind as to offer it up or point me in the right direction?

Much appreciated,

Tom

---

### Post by prince_niceguy on 2009-03-17
does the copying involve a ntfs file system??? if yes, i too have noted the issue with copying.. with other filesystem like ext3, reiserfs etc i didnt face any issues.

---

### Post by sedawk on 2009-03-17
You can run "iostat" to monitor the io statistics every 10 seconds, e.g.
"iostat 10 100" to do it 100 times.

Is there (heavy) disk activity when not doing anything?

You can copy the 800 MB file first to /dev/shm (ramdisk) and
then test copying it to your disks.
That is the read/write speed of the drives according to iostat?

You can use "sync" to flush disk cache, check if the
fast speed you see at the beginning drops as soon as you
enter sync in another terminal (e.g. run a script doing
a sync every second).

---

### Post by tgeer43 on 2009-03-19
> **prince_niceguy said:**
> does the copying involve a ntfs file system??? if yes, i too have noted the issue with copying.. with other filesystem like ext3, reiserfs etc i didnt face any issues.

prince_niceguy - please see my reply to sedawk below.

---

### Post by tgeer43 on 2009-03-19
> **sedawk said:**
> You can run "iostat" to monitor the io statistics every 10 seconds, e.g.
"iostat 10 100" to do it 100 times.

Is there (heavy) disk activity when not doing anything?

You can copy the 800 MB file first to /dev/shm (ramdisk) and
then test copying it to your disks.
That is the read/write speed of the drives according to iostat?

You can use "sync" to flush disk cache, check if the
fast speed you see at the beginning drops as soon as you
enter sync in another terminal (e.g. run a script doing
a sync every second).

sedawk - thanks a bunch. prince_niceguy nailed it but your suggestions allowed me to verify it. The problem is that the target drive is still formatted as ntfs from my Windoze days. I get a steady ~26MB/s when copying to the ext3 drive but when copying to the ntfs drive the speed quickly drops to ~6.5MB/s. Now I just have to figure out what to do with about 120 full length movies so I can reformat. They'll all eventually get burned to DVD but I'm not currently ready to invest the time or money to burn 120 DVDs. Anyone know where I can upload 100GB of files for free? :D

Seriously though, thanks a bunch to both of you guys. I was getting ready to put this issue on the back burner but now I can do something about it.

Tom

---

### Post by prince_niceguy on 2009-03-19
borrow a external drive from a friend and then i think you know what to do :)...

---

### Post by geometry_quiz on 2009-03-19
the numbers arent too accurate. a sata cable will only move at a max of 3gb/s.

---

### Post by HermanAB on 2009-03-19
Hmm, 800MB isn't a large file.  You should not have any issues with that.  On a laptop PC, you should expect to get a speed of 32 to 45 MB/s sustained on large files and hard disks.  I have run many tests with 100 Gigabyte files while researching a video replay system.

If you get bad performance with a hard disk then the trouble likely lies with the file system and you need to upgrade.

However, if the destination is a USB memory stick, then you should expect to see about 7 to 15 MB/s since that is the nature of these devices.

Hope that helps!

Herman

---

