---
title: "Mounted Drives don't appear"
date: 2005-10-31
forum: Desktop Environments
---

### Post by sdr_ar on 2005-10-31
Hi! I have made some modifications in /etc/fstab and since then the links to the mounted drives don't appear in "Storage Media" 
May I have to change some option?
Regards

---

### Post by tonysathre on 2005-10-31
whats your fstab look like

---

### Post by jeremy on 2005-10-31
if you open konqueror and go to /media can you see them there? If you can, then you are probably seeing this bug; [http://bugzilla.ubuntu.com/show_bug.cgi?id=18211](http://bugzilla.ubuntu.com/show_bug.cgi?id=18211)

---

### Post by sdr_ar on 2005-11-07
yes, it is that bug. I have read about it. I made many tries, but nothing. 
Thank you for your answer

---

### Post by sdr_ar on 2005-11-08
I fixed the problem uncommenting the last line of the file /etc/default/hal
That permits hal work with root permissions, so it can use fstab-sync (as you can read it in the same file)

---

### Post by ZiZi on 2005-11-14
[QUOTE=sdr_ar]I fixed the problem uncommenting the last line of the file /etc/default/hal That permits hal work with root permissions, so it can use fstab-sync (as you can read it in the same file)[/QUOTE] Yes, that really worked, thanx a lot! Does it bring up some security problems, or is it just a misconfiguration in Kubuntu? I wonder how this could happen and why it couldn't be avoided, because it must be very confusing for common users, who are the main target of this distro... :confused:

---

### Post by sdr_ar on 2005-11-17
Hi! I have been using Linux since 5 years, and it advanced a lot, and it will go on. Linux distros like Kubuntu or Mandriva are thought for newbies, but Linux is still difficult at some points. But to day, it is much easier than 5 years ago. If you come from Windows, it will take a time to you to get used to Linux, but if you are patient, you will see many good things in Linux.

---

### Post by sdr_ar on 2005-11-17
But this distros that are right for newbies, are right for advanced  too. That's the advantage of Linux, that it is for all people. Linux is for free.

---

