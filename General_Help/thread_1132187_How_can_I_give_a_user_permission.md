---
title: "How can I give a user permission"
date: 2009-04-21
forum: General Help
---

### Post by abenner2 on 2009-04-21
I am very new to Ubuntu, and I'm having a few issues figuring some things out. 
The biggest issues that I have is that I have a second hard drive that I use to store my media on, and I can't figure out how to give my user permission to use this drive.
I have been able to put files there using nautilus. I open these files as my user, but I'm unable to move files onto this hard drive or even create folders to put them into, while outside of nautilus.

---

### Post by bodhi.zazen on 2009-04-21
It depends on the file system on the hard drive :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by abenner2 on 2009-04-21
The file system is ext3

---

### Post by bodhi.zazen on 2009-04-21
I would add a line in fstab (see the link I gave you).

Then ```
sudo chown user.user /mount/point
sudo chmod 770 /mount/point
```

Of course, change user to your log in and /mount/point to where you mounted the drive.

---

### Post by abenner2 on 2009-04-21
Thank you very much, the link that you provided was very helpful. I was actually able to figure it out before you posted the code for it.

---

### Post by themacedonian on 2009-04-21
thank you

---

