---
title: "Update download errors .... help !"
date: 2009-03-18
forum: Desktop Environments
---

### Post by dejay68 on 2009-03-18
Hi,
Update manager tells me I have a number of updates available, but when i try to install them i get this message .....

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can anyone please help ??   :(

PS: They all look like music / video / codecs etc updates

---

### Post by kostkon on 2009-03-18
Close *Synaptic* or *Add/Remove*, if you have them open.

Then, open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give the command:
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.

Then try again to apply your updates.

---

### Post by dejay68 on 2009-03-18
Fantastic, it worked :popcorn:
You are a star .  :D Thanks again.

---

