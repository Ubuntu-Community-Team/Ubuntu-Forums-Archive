---
title: "Completely remove Mozilla Lightning and Reinstall"
date: 2009-03-16
forum: General Help
---

### Post by Dragonmantank on 2009-03-16
I have a profile that I've been moving around from PC to PC during reinstalls of the OS, but this last time I tried moving my Mozilla Thunderbird profile Lightning was broken. No calendars displayed and I could not add a new calendar, the menu options were disabled. I removed and tried redownloading 0.9 from Mozilla's add-ons site since 0.9 was what I had installed, but that did not help.

I removed 0.9 via the Add-Ons panel, installed 'lightning-extension' from the repos, and deleted the 'storage.sdb' file from '.mozilla-thunderbird'. Now when I go into my calendars it shows three 'Home' calendars but I cannot delete them, and I still cannot add a new calendar.

What else can I do? I'm not interested in retrieving any old calendar information, I just need to keep my e-mail.

---

### Post by shadow_code on 2009-03-16
I had this problem. I think I fixed it by deleting all the setting files and backed up the mail boxes. Then did a fresh install of Thunderbird. Though redoing my calendar didn't bother me. You might be able to backup the calendar as well.

---

### Post by pmla on 2009-07-05
In another post.

Install from repository:
libstdc++5

open Thunderbird and uninstall lightning.
restart thunderbird
install lightning again
restart thunderbird and problem should be solved.

edited:
needs a final step
* Remove calendar database "storage.sdb" from your profile 
.mozillathunderbird

---

