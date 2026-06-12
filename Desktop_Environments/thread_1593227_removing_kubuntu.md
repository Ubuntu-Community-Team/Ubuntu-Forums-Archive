---
title: "removing kubuntu"
date: 2010-10-11
forum: Desktop Environments
---

### Post by toswells on 2010-10-11
I am running Ubuntu Studio 10.04 and installed Kubuntu a few months ago. I found that I don't use it, So before moving to 10.10 I wanted to clean up my system and remove kubuntu.  I tried the sudo tasksel remove kubuntu-desktop and now I have a problem.  rebooting brings up the kubuntu screen with the flashing dots and just sits there. 

I have since found [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) Is there a way to get back to ubuntu.  I looked around and cant find my 10.04 disk, but I have 10.10 downloading now.  will this still work?

---

### Post by ubunterooster on 2010-10-11
It appears the problem is your PC trying to boot into KDE which is no longer there; not sure how to fix that.


Once you log in to gnome that method should work though it may leave behind a KDE program or two; no big deal.

---

### Post by toswells on 2010-10-11
I am still having trouble.  I have a 10.10 disk, but it wants to repartitino the drive.  I can log on through the restore  Is there a way to just update from the terminal prompt

---

### Post by toswells on 2010-10-11
is there a way to point it back to gnome?

---

### Post by glitch323 on 2010-10-11
> **toswells said:**
> is there a way to point it back to gnome?

Have you done this?

$ sudo dpkg-reconfigure gdm

---

### Post by toswells on 2010-10-11
$ sudo dpkg-reconfigure gdm

just tried this.  gdm is broken or not installed.

---

### Post by ubunterooster on 2010-10-11
sudo apt-get install gdm -f

---

### Post by toswells on 2010-10-11
no luck yet.  I can install a new copy beside or overtop, but I cant get the org 10.4 back up or upgraded.

---

