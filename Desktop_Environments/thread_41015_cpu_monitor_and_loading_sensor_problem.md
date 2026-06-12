---
title: "cpu monitor and loading sensor problem"
date: 2005-06-11
forum: Desktop Environments
---

### Post by Omnios on 2005-06-11
Im trying to get Gdesklets to work expecialy the cpu and motherboard sensors working. On load I get a load sensor fail worning and just about every desklet with sensor fails to laod. I tryed finding and loaded a lot of sensor stuff and it still didnt work. Any help with this would be apreciated.

---

### Post by Joeb on 2005-06-11
You have loaded the lmsensors package (which profides the data for the various sensor desklets), right?  Also, a lot of the desklets in the ubuntu repository for Hoary are broke because of changes made to the gdesklet program itself.  The main gdesklets program is fine, but you probably want to download other desklets, especially the sensor ones, from gdesklets.gnomedesktop.org for the latest versions.

---

### Post by Omnios on 2005-06-11
Just checked something, tryed running cpu frequency monior in panel and its borked so I think there is something borked with monitoring in general. Might have been something I loaded but not shure. I do have Lm-sensors but on boot the script claims that sensors failed to config. I have no idea about how to fix this.

---

### Post by Omnios on 2005-06-11
"Edits Borked lol"
 
 K found out that lm-sensors has to be configed after loading by doing sudo sensors-detect and setting it up. Now a lot of the stuff works except what seems to be the main moduals Im going to see if I can download them. This may be a config thing as they changed the config but left all the old config stuff in so not shure but this may be borking.

---

