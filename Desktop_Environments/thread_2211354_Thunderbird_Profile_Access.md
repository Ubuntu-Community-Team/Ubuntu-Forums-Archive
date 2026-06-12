---
title: "Thunderbird Profile Access"
date: 2014-03-15
forum: Desktop Environments
---

### Post by Daniel_Devor on 2014-03-15
Thunderbird has a user profile and a Mail subdirectory containing a popstate.dat file that I must reach. Normal access to TB-profile (Thunderbird -P) simply leads to an option window that does not seem to meet the requirement. Please advise on how to reach the TB profile and subsequently the Mail subdirectory. All help appreciated.

---

### Post by SeijiSensei on 2014-03-15
Thunderbird stores everything in /home/username/.thunderbird.  This is a "hidden" directory because its name begins with a dot.  If you are using a graphical file manager like Nautilus or Dolphin you need to tell it to display hidden files.  From the command prompt. you can just use "cd /home/username/.thunderbird".  You'll see a directory with a name like 1u6xg3bo.default; that's where your profile is stored.  If you have more than one directory like that, look in the profiles.ini file to see which is the current default profile.

---

