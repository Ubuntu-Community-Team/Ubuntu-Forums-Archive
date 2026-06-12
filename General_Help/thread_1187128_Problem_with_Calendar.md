---
title: "Problem with Calendar"
date: 2009-06-14
forum: General Help
---

### Post by geeoff on 2009-06-14
Hell All,

I have recently migrated back from Linux Mint (Elyssa) to Ubuntu 8.04
Everything went fine with all my programmes except Mozilla Sunbird which causes the following error message when I try and open it -: 
"Calendar data in your profile was updated by a newer version of Calendar which will probably cause information to be lost or corrupted (Null) will now quit."

I have tried removing and re-installing Sunbird with no improvement and also installing Lightning, which just produced the same error message.

Any help would be appreciated

---

### Post by Failbot on 2009-06-14
Well your calendar profile/data/settings etc are stored under ~/.mozilla/sunbird. To start with you could rename this, say to "sunbird-old", then fire up Sunbird and see if it works.
Unfortunately, it will fire up as though it's the first time you've used Sunbird - your old calendar data won't be there. If that's ok with you, then just re-setup Sunbird how you like and you're done. Otherwise you'll need to reconnect to your old calendars - I only use networked calendars so that's easy. If you were using calendars "on your computer" then you'll need to find a way to import that old data back. I'm only guessing here, but you might be able to copy some of the files from under the "sunbird-old" folder (maybe the storage.sdb file?), or import one of the backup .ics files from under the "backupData" folder.

Good luck!

---

### Post by geeoff on 2009-06-14
Thanks for the help Failbot, it now fires up.

As you say, it comes up as a 'first time used' version. Fortunately the old Linux Mint was on another partition which I can still access, so I can go into the old Sunbird and manually copy the relevent dates over.

Thanks again,

---

