---
title: "System stops if I don't constantly give it input, keyboard repeats"
date: 2009-06-24
forum: General Help
---

### Post by Aleksei Vasiliev on 2009-06-24
Hello,

My Ubuntu 9.04 system is completely unusable and worthless.

If I do not give it input (finger on touchpad, key press) constantly, it will stop. For example, during a git fetch of the jaunty kernel, everything stopped. The text cursor block in Terminal stopped, the download stopped. As soon as my finger hit the touchpad everything started again, except that my wireless card had to be restarted.
This happens during boot, shutdown, everything. If I don't press buttons it will just stop all disk activity and all other activity.

Typing also has major difficulties. Occasionally, seemingly at random, it will repeat characters. Here's an example I just tried by typing some stuff from a reading speed website:
> This seems surprising since most readers, actively reeeeeeeeeeeading work documents, newspapers, magazines, books or the contents of a computer display are practicing daily for at least one hour. With such aaaaaaaaaaaan intense training everyone should be close to top performances.

Unfortunately, this is ttttttttt

I am not holding the key down and the key is not sticking, it works fine in Win7 and, previously, XP.

This is happening on:
Ubuntu 9.04 AMD64 with default kernel
* with the kernel I got through apt-get upgrade
* with the linux-image-2.6.28-13-generic kernel
* with a custom kernel compiled from the ubuntu-jaunty git repository, based on Ubuntu-2.6.28-13.44

I am using an ext4 system. Somebody once mentioned that this was a bad idea, but at the time I was running an alpha version of 9.04. I had the exact same issues. Is ext4 the problem?

Sager NP2092 laptop (Compal JFL92)
Intel C2D T9500 2.5GHz
4GB RAM

---

### Post by Aleksei Vasiliev on 2009-06-24
I've disabled AHCI and it still happens, though it may be occurring less often.

---

### Post by t0p on 2009-06-24
You could get a nodding dog or one of those birdy desk ornaments whose head bobs up and down to drink water.  Positioned correctly, the toy would repeatedly hit the Return key and keep your machine working.

:p

---

### Post by Aleksei Vasiliev on 2009-06-24
System just completely froze in the middle of executing a program. Had to hit the power button, which immediately made it start working again.

Could ext4 be the problem?

---

### Post by t0p on 2009-06-24
I did a search for 'ext4 system freeze' and found a bundle of reports/complaints.  [This bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/370925") seems typical. But it doesn't sound quite like yours...

Anyway, maybe ext4 is to blame, maybe not.  I suggest you reinstall, after formatting the disk to ext3.  That ought to answer your question.

---

### Post by Aleksei Vasiliev on 2009-06-24
Solved: Ubuntu 9.04 will forever be unusable on my system and I am not going to try it again.

Not only do the freezes and repeating occur in ext3, they occur *in the install process running from disc*. It is obvious that something in 9.04 is completely broken for my hardware.

I'm probably just going to install 8.10 since that didn't have this problem.

Anybody know what could have changed to cause this?

---

### Post by P4man on 2009-08-21
have a look at this:
[http://ubuntuforums.org/showpost.php?p=7824338&postcount=5](http://ubuntuforums.org/showpost.php?p=7824338&postcount=5)

---

