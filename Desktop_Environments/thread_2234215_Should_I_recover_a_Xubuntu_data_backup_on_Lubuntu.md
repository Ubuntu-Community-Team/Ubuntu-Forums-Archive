---
title: "Should I recover a Xubuntu data backup on Lubuntu?"
date: 2014-07-13
forum: Desktop Environments
---

### Post by Ralf_Hutter on 2014-07-13
Hello everybody,
i made a data backup with deja dup on xubuntu, copying my personal folder. Now my new computer runs lubuntu and i want to get my data on it. I already installed deja dup there. Could there be a problem if i do the data recovery on lubuntu?

---

### Post by Bucky Ball on 2014-07-13
These are just data files, right? As in documents, videos, music, etc. Not system or settings files? If so, go right ahead.

---

### Post by Ralf_Hutter on 2014-07-14
Right, just the personal folder. But as there are the thunderbird emails included, i thought that maybe i should watch out.
What can i do to copy the thunderbird and firefox settings from xubuntu to lubuntu?
Thanks anyway!

---

### Post by Bucky Ball on 2014-07-14
For Firefox simply navigate to the backedup profile (ends with .default) then copy/paste it into the Xubuntu install by navigating to /home/*username*/.mozilla/firefox/. In there, you will see an existing profile named 'w6ejaxr7.default' or something like it (could be any alpha-numeric combination). Delete and replace with the backup profile. 

For Thunderbird, pretty much the same. /home/*username*/.thunderbird/. Delete the profiles.ini and replace with the backed up profiles.ini. Done. Hopefully that all works.

(PS: *username* = your username. E.g. /home/Ralph_Hutter/.mozilla/firefox. ;))

---

### Post by marcussive on 2014-07-25
Does the same apply to Ubuntu? I've been using Ubuntu and Backup and am planning to switch to Xubuntu and hoping I can restore my Ubuntu backups into Xubuntu. Yes?

---

### Post by Bucky Ball on 2014-07-25
> **marcussive said:**
> Does the same apply to Ubuntu? I've been using Ubuntu and Backup and am planning to switch to Xubuntu and hoping I can restore my Ubuntu backups into Xubuntu. Yes?

All depends what you are backing up and trying to restore to Ubuntu, but please start a new thread about it with a descriptive title in the appropriate sub-forum. Thanks and good luck.

---

