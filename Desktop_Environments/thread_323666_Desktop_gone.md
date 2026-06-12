---
title: "Desktop gone"
date: 2006-12-22
forum: Desktop Environments
---

### Post by leona on 2006-12-22
Hi.
Last couple of days I've booted up and I noticed I had not background impage, going into the desktop background settings, showed the image, click on and its back again, but tonight I boot in and not only have no background image, I now have NO Icons at all, its completely black, nothing there, empty, ziltch.

What is going on?

---

### Post by taurus on 2006-12-22
Did you do any updating the last few days?  What if you run these commands and then reboot?

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by leona on 2006-12-23
Thanks Taurus for your reply, I tried this, but sadly didn't fix my problem I still have no desktop, its totally gone.

---

### Post by taurus on 2006-12-23
What if you create a new user and log in with the new user to see if you have any Gnome desktop working!

---

### Post by leona on 2006-12-24
Yes creating a new user, they get a working desktop, background and icons, logged back on with my account, still nothing.

---

### Post by taurus on 2006-12-24
Maybe you want to boot into recovery mode and remove .gnome, .gnome2, & .gnome2_private!  And of course, all your personally settings will be wiped out too...

---

### Post by leona on 2006-12-27
ohh that sounds drastic, is there no other way to "repair" it?

---

### Post by taurus on 2006-12-27
There are other ways but it's kind of hard to explain...  

You can create a new user, let's called john.  Then, you can copy all the .gconf, .gnome, .gnome2, & .gnome2_private to john's $HOME directory.  Then use sudo to change the ownership of those directories and files under them to john.  Now, log in as john and see if everything is working!  Or at least that is the first thing I would do...

---

### Post by leona on 2006-12-28
ohh scary, did that and it wouldn't even log in,  It doesn't get passed the Metacity screen when logging in.

  Removing the .gnome .gnome2 and .gnome_private (this dir is empty) allows the "test" user to start again.

---

### Post by leona on 2007-01-01
any more thoughts / ideas?

---

### Post by ComplexNumber on 2007-01-01
**leona**
when you followed the following part of taurus' instructions, what command on the terminal did you use?
> Then, you can copy all the .gconf, .gnome, .gnome2, & .gnome2_private to john's $HOME directory. Then use sudo to change the ownership of those directories and files under them to john.
it should be:
 *sudo chown -R john:john .gconf .gnome .gnome2 .gnome2_private*

---

### Post by leona on 2007-01-01
> **ComplexNumber said:**
> **leona**
when you followed the following part of taurus' instructions, what command on the terminal did you use?

it should be:
 *sudo chown -R john:john .gconf .gnome .gnome2 .gnome2_private*

Well sort of, I did a longer hand version
sudo chown -R test .g*
sudo chgrp -R test .g*

I didn't know you could combine them :)

---

### Post by leona on 2007-01-04
Googling around seem to reveal that this was caused by a recent update that appears to kill nautilus (don't you just love quality control!).  Anyway fixed by running Nautilus in xterm & then logged out and back in. 
Gnome saved the session which now starts nautilus automatically.
So far everything is now back as it was, I have Icon and my desktop background back.
Sending a virtual 'slap on the wrist' to whoever broke it via the update!

---

