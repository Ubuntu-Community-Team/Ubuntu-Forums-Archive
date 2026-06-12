---
title: "Intrepid died.  Sudo segfaulted, now I can't log in"
date: 2009-01-12
forum: General Help
---

### Post by muszek on 2009-01-12
This is my sister's PC.  She said her printer doesn't want to work..

I didn't want to mess with it too much, so I wanted to just re-install it.  I started with backing up /etc/conf.
sudo cp -R /etc/cups /home/ania/temp
... and it segfaulted when I typed in a correct password (asked me to repeat when I made a mistake).

I rebooted.  And now I can't log in at all. 
Gnome login screen goes to black and then reloads (as if I pressed ctrl+alt+backspace).
In CLI mode, it just re-asks for username after I give a correct password.

Sister hasn't been doing anything as root for a week or so.  Faulty HDD?

What would you do?

---

### Post by blazemore on 2009-01-12
I would boot to recovery mode, log in as root, run startx, copy across all personal files, delete the user, make a new user and copy the files back across after the first sucessful login.

---

### Post by adamlau on 2009-01-12
Or faulty memory, or system bus, or anything. I would mount her HD under a known good install on a known good box and copy over /home/ania before verifying and writing zeroes to the drive and reinstalling from scratch. Or at least run e2fsck on all of her partitions.

---

