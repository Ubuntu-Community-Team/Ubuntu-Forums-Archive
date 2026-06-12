---
title: "Radeon 9600 (flavor)buntu 16.04+"
date: 2017-09-07
forum: Desktop Environments
---

### Post by vorvalk on 2017-09-07
Greetings,

For an older machine (Athlon XP 1700+) I tried Xubuntu and Lubuntu with same results: with an ati radeon 9600 the system randomly crashes and monitor goes without signal. The only solution is a hard reset since neither Ctrl+Alt+F1 works. The drivers are the default ones, since there are no proprietary for this card. Also tried with the non-LTS versions. Same result. Anyone with similar problem that may have made some progress?

Thank you.

---

### Post by Autodave on 2017-09-10
Are you sure that this is a video issue?  Could very well be a power supply issue or a RAM issue. Do you still have some version of Windows on it that you can try? Can you boot it to the install medium and see if thew same thing happens on that?

---

### Post by yoshii on 2017-09-18
Try a LiveDVD of v14.04.x LTS.  That seemed to be the last version before the ATI/AMD video problems came up.  You might be able to check some of your system with that before going up to 16.04+ or 17.04+

---

### Post by vorvalk on 2017-11-23
I'm pretty sure it's video related, since I have another HDD with a windows XP installed and it runs smooth with those windows drivers. Tried with a 14.04LTS but the system freeze at startup. Couldn't try another flavor though, since all of them are EOL now :-/

---

### Post by mörgæs on 2017-11-26
Is the system stable if you install a [minimal Ubuntu]("https://help.ubuntu.com/community/Installation/MinimalCD") without adding a GUI?

---

### Post by vorvalk on 2018-01-06
Yes. Somehow I'm thinking it has something to do with the AGP speed. From old posts of Soltek some people in XP era noticed some incompatibility between Radeon and VIA chipsets. A workaround was to force AGP 4x speed instead 8x. Though in Windows drivers that can be done via Catalyst I'm not sure how I can force an AGP mode in Linux. Any hints?

---

### Post by mikewhatever on 2018-01-06
There should be a setting for AGP x4/x8 in the BIOS. Anyhow, Catalyst doesn't support cards older then Radeon HD 4000, so don't bother with it.

---

