---
title: "How to force ET to save it data NOT in home directory?"
date: 2005-12-16
forum: Gaming &amp; Leisure
---

### Post by Barts_706 on 2005-12-16
Hi,

The question is more or less as in topic. Enemy Territory keeps all its user files (including hefty downloaded maps and such) in user's home dir. As my home partition is only one Gb big (I did not think that any settings could grow to 700Mb, as .etwolf did) and I do not want to repartition my disk, I was wondering if it could be changed somehow so that all this data goes somewhere else (on my data storage partition for example)?

Any of you knowing the answer and willing to help? I would much appreciate.

---

### Post by Zimmer on 2005-12-16
Where is your usr/local/games/Enemy-Territory folder located?
If it is not on the Home partition then transfer your downloaded maps to the etmain or relevant mod folder located there.
If you run et from the terminal and quit you will see that it looks for the start files in the user folder and then looks in the usr/local/games   folders if it fails....I am guessing it would do the same for the maps...
There does not seem to be anything set in the config files to change for map locations, but I haven't scoured the ET forums for config info as yet......

Zimmer

---

### Post by Barts_706 on 2005-12-16
Yup, you got it right - the main directory was elsewhere. Transferred the maps and it alleviated problem a little.

Thanks.

---

### Post by Zimmer on 2005-12-16
Glad to help.. oh and watch out for the cvar_backup*.cfg files in the etpro folder... they are only half a kb each but they could soon mount up if you play the ETPro mod. 

Regards

Zimmer

---

