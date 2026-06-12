---
title: "Wireless wont activate"
date: 2006-01-07
forum: General Help
---

### Post by hove99 on 2006-01-07
Hi everybody

I'm trying to get my wireless to work with kubuntu, but when I try to activate my wireless connection having entered the ESSID and key, it stays activated for only a second or so and the deactivates. Any ideas as to a solution?

Thanks :-)

---

### Post by harisund on 2006-01-07
Are you sure your wirless card is recognized and working? And that the router that is broadcasting your wireless connection is working and stable? 

In that case, assuming your wirelss connection is through wlan0 do the following

iwconfig wlan0 mode Managed essid <your_essid>
dhclient wlan0

and post back if you are able to work.

---

### Post by hove99 on 2006-01-07
Hi again and thanks for the answer. I reset my router, and changed the ESSID/key accordingly and suddenly it worked. Very strange, since I'm sure I entered the information correctly. But something was apparently wrong :-) think there is a bug in the ubuntu kernel on the cd, since I couldn't even get into administrative mode. Had to use ethernet cable to upgrade.

---

