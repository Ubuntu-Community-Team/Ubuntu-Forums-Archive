---
title: "Getting Thunderbird XP profile into Ubuntu?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by kendals on 2006-08-30
Heya guys.

I've already tried copying the files under my Thunderbird profile folder in XP to the Ubuntu thunderbird profile folder, but it gives me a security alert  telling me it couldn't initialise the browser's security component, most likely caused by files in my profile directory, blahblah...

Anyway, not sure what I'm doing wrong. I even tried to not copy over the extension files in case it messed them up, but still nothing. And when I click on different folders in Thunderbird to view the emails, it sits there 'loading' but doesn't ever load the emails :(

Please help :confused:

---

### Post by gibbylinks on 2006-08-30
What I've done is made a new partition FAT32 that I can share between windoze and Linux. Then copy your profile folder to this partition. Open Thunderbird profile manager and create a new profile, then you can choose folder and select your profile on the fat32 partition. 

Hope that helps

---

### Post by lha on 2006-08-30
Check if [Move an existing profile or restore a backed up profile]("http://www.mozilla.org/support/thunderbird/profile#move") helps you.

---

### Post by kendals on 2006-08-30
Hey guys. Thanks. I found out that I was doing the correct shifting already, but the files had been shifted as root, and so when I wasn't logged as root, I couldn't view them ;)

So I shifted them as a normal user, and they're all there now, and edited profile.ini w00t! :)

---

