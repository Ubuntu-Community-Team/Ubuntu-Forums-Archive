---
title: "firefox/thunderbird profile help"
date: 2009-06-03
forum: General Help
---

### Post by pstrbrc on 2009-06-03
OK, I finally pulled the trigger, and completely reformatted my laptop with Xubuntu 9.04. (I had it dual-booted with WinVista and Ubuntu 8.04, and 8.04 didn't like my wireless card, so I couldn't just upgrade to 8.10 then 9.04, so I just flushed the whole harddrive and started fresh)
OK, I saved my Firefox and Thunderbird profile folders, and have them in /home/(me)/firefox/ and /home/(me)/thunderbird/. 
How do I move the contents of these folders into /etc/firefox/ and /etc/thunderbird/? I've tried using the terminal and the cp command, but that only seems to work for individual files. How do I copy an entire folder? 
Or, is there a simpler way?

---

### Post by merlinus on 2009-06-03
It may be different in xubuntu, but in ubuntu profiles for firefox and thunderbird are in hidden directories in /home/user.  These directories start with a dot (.).

If this is the same for you, then you should copy your profiles over, using the existing structure as a guideline.

hth....

---

### Post by pstrbrc on 2009-06-03
=D> Thank you! Bookmarks, passwords, everything is here! Thanks!

---

