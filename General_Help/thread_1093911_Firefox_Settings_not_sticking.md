---
title: "Firefox Settings not sticking"
date: 2009-03-12
forum: General Help
---

### Post by ramjet_1953 on 2009-03-12
Hi, Guys!

I am experiencing an interesting problem with Firefox Web Browser.

What is happening is that every time I re-start Firefox all of my user settings have gone back to default.

This problem occurred after I copied my /home drive to an external USB drive.

After the copy was completed and the next time I re-booted, I got a warning message when logging in that my home drive now had write privileges for all users. I opened Nautilus in super user mode and re-set the permissions. I have no idea why the permissions changed in the first place, as I did not manually change them.

I tried doing a re-install of Firefox, but the condition persists, which is most frustrating.

I haven't lost any of my add-on's, passwords, or bookmarks, just the things that you set-up in the Edit>Preferences menu keep defaulting.

Any ideas why this is happening would be appreciated.

Regards,
Roger :D

---

### Post by nelskurian on 2009-03-12
I think you reset the home directory permissions to the earlier state.
Just check the permissions of ~/.mozilla/firefox.This directory actually holds the local setting of firefox.The default permissions of this directory is 700
The default home directory permissions is 755.
pls fix this using 
sudo chmod -R 755 ~
sudo chmod -R 700 ~/.mozilla

---

### Post by ramjet_1953 on 2009-03-12
Thanks for the suggestion, but I'm afraid that re-setting the permissions that you suggested didn't work.

I am sure that this is the correct line of thought, though and it just requires nutting-out which file/s need to have their permissions re-set.

Regards,
Roger :D

---

### Post by ramjet_1953 on 2009-03-13
My apologies, nelskurian.

Your suggestion did work, it just required a re-boot, not just a log out and log back in.

Regards,
Roger :D

---

