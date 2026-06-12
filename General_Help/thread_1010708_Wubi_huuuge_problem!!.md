---
title: "Wubi huuuge problem!!"
date: 2008-12-14
forum: General Help
---

### Post by blandino123 on 2008-12-14
omfg....well iw as using ubuntu linux for the first time.i found it a litttle dificult but i lllllllllloooooooooovvvvvvvvveeeeeeeeeeeddddddddddd it!
then my pc crashed!!!!!!!!!!!!!


when i first installed wubi i used the 30 gb option.when i crashed i let my pc just chill for a couple of hours and then i tryed to boot into vista and i crashed again!!!
then vista told me to restaore or i might mess up my pc the next time booted.i went in and i tryed to uninstall ubuntu but wubi wassent in uninstall program files!!! i even re opened the set up for wubi and the install came up.i need real help because now im missing 30 gb!!and when ever i boot i still have the option to boot into ubuntu...i want to completely remove it from my system to reinstall MAYBE.so can anyone help me please?

---

### Post by solwic on 2008-12-14
> **blandino123 said:**
> omfg....well iw as using ubuntu linux for the first time.i found it a litttle dificult but i lllllllllloooooooooovvvvvvvvveeeeeeeeeeeddddddddddd it!
then my pc crashed!!!!!!!!!!!!!


when i first installed wubi i used the 30 gb option.when i crashed i let my pc just chill for a couple of hours and then i tryed to boot into vista and i crashed again!!!
then vista told me to restaore or i might mess up my pc the next time booted.i went in and i tryed to uninstall ubuntu but wubi wassent in uninstall program files!!! i even re opened the set up for wubi and the install came up.i need real help because now im missing 30 gb!!and when ever i boot i still have the option to boot into ubuntu...i want to completely remove it from my system to reinstall MAYBE.so can anyone help me please?

My experience is that once you run the install, you have to reboot into Windows and then reboot *again*, this time into Linux.  It'll finish installing, and then you can reboot a *third* time into Windows and the option to uninstall should be there then.

Hope that helps.  :)

---

### Post by ago on 2008-12-15
> **blandino123 said:**
> then vista told me to restaore or i might mess up my pc the next time booted.i went in and i tryed to uninstall ubuntu but wubi wassent in uninstall program files!!! i even re opened the set up for wubi and the install came up.i need real help because now im missing 30 gb!!and when ever i boot i still have the option to boot into ubuntu...i want to completely remove it from my system to reinstall MAYBE.so can anyone help me please?

Run chkdsk /r. Delete the wubi folder. Note that sometimes windows moves files into a hidden folder called C:\found.0000, make sure you can see hidden files and look for that.

---

### Post by blandino123 on 2008-12-16
> **ago said:**
> Run chkdsk /r. Delete the wubi folder. Note that sometimes windows moves files into a hidden folder called C:\found.0000, make sure you can see hidden files and look for that.
lol can u say that in words that a pc noobie can understand please?:lolflag:

---

### Post by ago on 2008-12-19
Open a dos box, go in the drive where you installed wubi and run 

chkdsk /r

Then make sure you can see hidden folders (explorer > tools > folder options) and look for a folder called C:\found.000 where windows sometimes move files.

---

