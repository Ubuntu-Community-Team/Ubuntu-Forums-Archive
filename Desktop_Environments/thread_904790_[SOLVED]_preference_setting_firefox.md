---
title: "[SOLVED] preference setting firefox"
date: 2008-08-29
forum: Desktop Environments
---

### Post by koba101 on 2008-08-29
Hi,

I just re-installed hardy and I'm having a problem with firefox, everytime i change the preferences (e.g. homepage) i get reverted to the default setting when i restart firefox

i discovered however that when i run firefox as root the settings are preserved, i'm thinking it's related to the profile where it's being saved

can anyone help me on this?

---

### Post by koba101 on 2008-08-30
ok i found another post mentioning that i should delete the profiles.ini from the ~/.mozilla folder

was that folder corrupted?

I'd like to know hwy running as admin worked in this case...what's the difference?

---

### Post by koba101 on 2008-09-12
solved this..needed to delete the file prefs.js under /etc/firefox-3.0/profile and it worked

---

