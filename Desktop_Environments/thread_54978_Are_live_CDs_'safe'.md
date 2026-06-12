---
title: "Are live CDs 'safe'?"
date: 2005-08-07
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-08-07
What I mean is, can you accidentally harm your system with a Live CD?

Err... Let's say you are on a Live CD, I don't have one at the moment, so I wont test.   Do you have root permissions, and can you accidentally format your hard drive?

Just wondering.

EDIT: I didn't mean CD drive, I meant hard drive.  My mistake.

---

### Post by jasmuz on 2005-08-07
Erm...Well if you have a mounted drive with write permissions you could easily but consciously fsck it up, because Live CD's are mainly for show-off or to fix problems.

---

### Post by wvslkr on 2005-08-07
It depends on the live cd.  Most by default mount filesystems read only.  Some you can switch to root and read write.  Some are read only. 

You can totally bork a system with a live cd,but you have to switch to root to do it.

---

### Post by arcanistherogue on 2005-08-07
What is an example of a safe read only one?

I basically want to carry one around with me to use when I use library computers and whatnot, and I want to make sure I can't accidentally do something bad.

---

### Post by wvslkr on 2005-08-07
If I remember correctly the Mandrake live was read only and I believe Linspire is read only if you can find it.  They are all safe as long as you don't start mucking around with other filesystems where you shouldn't.  Many libraries won't allow you to use them anyway.  Basically you won't screw anything up with livecd as long as you just run it in its default setup.  You pretty much have to do it on purpose. :)

---

### Post by poofyhairguy on 2005-08-07
[QUOTE=arcanistherogue]What is an example of a safe read only one?
[/QUOTE]

The original (Knoppix) is pretty safe.

---

### Post by arcanistherogue on 2005-08-07
Hmm... I think I might burn a knoppix one, I remember my linux using friend said it was the best Live CD and he always kept one with him incase he had a system error or something.

---

### Post by auburn on 2005-08-07
It's really safe. Dont' worry. I just taught how to use apache in my school. I had all the students boot up in knoppix. 

To get write access (at least in knoppix) you have to right click the drive icon, choose the correct tab and click the read/write checkbox. It NEVER defaults to read-write. Other than that, you'd have to go to the command line and specify the drive after you  issue an e2fsck, or cfdisk command. For example: cfdisk -d /dev/hda.

---

### Post by f1dave on 2005-08-07
I too choose knoppix.

There's just less of a chance to bork something. Hell, my family even used that and managed to do no damage ;)

---

### Post by ghostnet on 2006-04-29
I'm new to linux so forgive me if this is a silly question: Do the live CDs come with a generic root password?  If so, how do i change it?

---

### Post by aysiu on 2006-04-29
Ubuntu's live CD is not safe--it runs sudo commands without a password.

Well, you'd have to mount the hard drives first to do any damage.

I would advise Knoppix. I think live CDs generally use *root* as the password for root.

---

### Post by TitusDalwards on 2006-04-29
[QUOTE=ghostnet]I'm new to linux so forgive me if this is a silly question: Do the live CDs come with a generic root password?  If so, how do i change it?[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=36690]("http://www.ubuntuforums.org/showthread.php?t=36690")
your answer is above

---

