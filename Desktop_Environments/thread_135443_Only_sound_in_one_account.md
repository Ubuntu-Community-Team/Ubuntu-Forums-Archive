---
title: "Only sound in one account"
date: 2006-02-23
forum: Desktop Environments
---

### Post by TTT_travis on 2006-02-23
Hi,
I have breezy installed on my familie's computer and they like it however, sound only works in the account created at the install on the new accounts I create sound doesn't work and no sound cards are listed in the sound prefs

Any ideas?

---

### Post by pestilence4hr on 2006-02-23
Most likely you need to add them to the "audio" group in /etc/group.  You will need to do this under sudo.

---

### Post by TTT_travis on 2006-02-23
thanks, that did it

---

