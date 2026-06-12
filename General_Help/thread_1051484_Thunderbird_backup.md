---
title: "Thunderbird backup"
date: 2009-01-26
forum: General Help
---

### Post by malel on 2009-01-26
I have just found a backup utility for Firefox called - FEBE - and was wondering do we have a similar one doing the same sort of functions for Thunderbird. If so where can I get that from. 
Thankyou

---

### Post by cptr13 on 2009-01-26
Backing up and restoring thunderbird is very easy.  Go to your home directory.  In gnome hit "control H" and you will see the thunderbird directory.  In KDE click "view", "show hidden folders".
Copy and paste the folder and the profile.ini file onto your backup source.

I have backed up and restored in linux this way more times then I can count.  Sometimes it gets quirky doing this switching distros.

---

### Post by 3pinner on 2009-01-26
Actually the only thing you really need is to go to the .mozilla Thunderbird folder, open Profiles, and inside there will be a folder with a random sequence of letters and numbers (something like y5zhqn1b.default)
This folder (default) has all your messages, settings themes etc. 
Just copy it and paste it into your backup media. 
You really don't need the profile.ini file. when you install Thunderbird, it is created for that distro.
To restore all your messages and settings, Paste the default folder into the Profiles folder, click YES when it asks you if you want to overwrite the existing one (also created when you do a fresh install of Thunderbird) and you're in business.
All total, takes about 5 minutes.

---

### Post by adamlau on 2009-01-27
Copy the entire .mozilla-thunderbird folder over, _including its contents, profiles.ini and all_. No need for any third-party apps, or extensions. Seamless :) .

---

### Post by Shadoefax on 2009-01-27
If you like FEBE, you may want to try [TEBE]("http://customsoftwareconsult.com/extensions/tebe/tebebeta.html").  It's still in beta, but nearly ready for release.

---

### Post by malel on 2009-01-27
Thank to all those who have replied . I have a few alternatives to look at and am sure that I will find one that works for me . TEBE looks good but I think I will leave that until it is fully released.
Regards:D

---

