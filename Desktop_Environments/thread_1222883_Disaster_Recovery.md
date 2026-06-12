---
title: "Disaster Recovery"
date: 2009-07-25
forum: Desktop Environments
---

### Post by Felicity_X on 2009-07-25
I am running Hardy Heron. It was all working last night and, as far as I know powered down normally.  This morning, my husband powered up the computer and it produced some kind of error. I used CTRL/ALT/DEL and it restarted the BOOT.  It ran a disk scan and 61% of the way through it stalled with the message:-

/dev/sda5: Inodes that were part of a corrupted orphaned link list found.

It then goes on basically to say that automatic fsck failed and it must be run manually, as fsck died with exit status 4.

It the says that it has remounted the root filesystem in read-only mode and I am supposed to perform system maintenance (presumeably the manual fsck) and the press Ctrl-D to continue.  It then asks for the root password to continue.

Unfortunately, I do not know the root password.  It does not accept the supervisor password or ENTER.  If I enter Ctrl-D it reboots and cycles out when 61% through the boot precisely as previously.

One time when I went into the menu option it gives you around Grub stage.  The system temperatures looked rather high to me. Also the temp at which to cut out automatically was disabled.  It said the CPU fan was running at a sizeable rpm, but the sys fan was not running at all.  The lights on the front of the box seem to be showing as normal. No red ones at all!

Can someone please help?:confused:

---

### Post by jerrrys on 2009-07-26
Hi [Felicity_X]("http://ubuntuforums.org/member.php?u=601065"):

I have not had to deal with such a problem so I have no answers, just suggestions.

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=nR7&num=50&ei=HotsSvuNHZGANumT7PgG&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=Inodes+that+were+part+of+a+corrupted+orphan+linked+list+found.&spell=1&cts=1248627499989](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=nR7&num=50&ei=HotsSvuNHZGANumT7PgG&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=Inodes+that+were+part+of+a+corrupted+orphan+linked+list+found.&spell=1&cts=1248627499989)

[http://www.google.com/search?q=fsck+died+with+exit+status+4.+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=fsck+died+with+exit+status+4.+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://ubuntuforums.org/showthread.php?t=1146638&highlight=password](http://ubuntuforums.org/showthread.php?t=1146638&highlight=password)

Hopefully someone will come along that has dealt with this...good luck

---

