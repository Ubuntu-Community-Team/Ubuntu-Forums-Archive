---
title: "screensaver password not working"
date: 2006-09-15
forum: Desktop Environments
---

### Post by watermark on 2006-09-15
When my screensaver comes up, it wont accept my password.  I've tried changing my password with the passwd utility with no luck.  It used to work, but I can't think of what I might of done to make it not work.  For now I've been killing gnome-screensaver, but that gets tiresome.

---

### Post by ciscosurfer on 2006-09-15
You need to use the same password in gnome-screensaver as you do when you log into GNOME.

---

### Post by watermark on 2006-09-15
Uh, I know.  Say my password to login at gdm is letmein, I type letmein into gnome-screensaver...it pauses, shakes, and says no.

---

### Post by ciscosurfer on 2006-09-15
Glad you know.

Reinstall gnome-screensaver.

---

### Post by watermark on 2006-09-15
Thanks for helping btw.

I marked it for reinstallation in synaptic and it reinstalled fine, but it didn't solve my problem.

---

### Post by watermark on 2006-09-17
Does anyone have any more ideas?

---

### Post by watermark on 2006-09-21
Suse users are having a similar problem with an update...Ubuntu has an earlier version of gnome-screensaver then suse, but the exact same symptoms but no fixes.

[http://www.mail-archive.com/opensuse-factory@opensuse.org/msg03905.html](http://www.mail-archive.com/opensuse-factory@opensuse.org/msg03905.html)

---

### Post by dryliketoast on 2008-01-15
i am also having the same problem - although I think i actually caused it

i ran the following code to chown some files to root:

```

chown root\:../*

```

funny thing was, i was one level deep from the root of the file system! i ended up changing ownership of about 100 files before I pressed ctrl+c 

it was after that that i started getting the screensaver issue mentioned in this thread - whether its actually related, who knows?

---

