---
title: "temporary Internet files"
date: 2005-11-01
forum: Desktop Environments
---

### Post by Irony on 2005-11-01
Where is the equivalent of the *temporary Internet files* folder in Ubuntu

---

### Post by paddyg on 2005-11-01
something like

/home/yourhome/.mozilla/firefox/something.default/Cache

---

### Post by niko_ on 2005-11-01
yep like

ls /home/`whoami`/.mozilla/firefox/*.default/Cache/

---

### Post by Irony on 2005-11-01
Thanks all, I hadn't thought of looking at hidden folders (Ctrl+H), here's the path;

*/home/irony/.mozilla/firefox/g45iquqq.default/Cache*

---

### Post by Kyral on 2005-11-01
or nuke the /tmp folder (I think it gets nuked everynight anyway)

---

### Post by anthro398 on 2005-11-01
Irony,

You might be interested in a simple script I posted to the Suse forums at [http://forums.suselinuxsupport.de/index.php?showtopic=17430&hl=temp](http://forums.suselinuxsupport.de/index.php?showtopic=17430&hl=temp) .  While locations won't be the same it may give you an idea of the areas in which to look.  Of course, it was written for kde, but I imagine you'll get the picture.

I've got a ton of handy little scripts like this if anyone is interested.  You know, one that comes in handy constantly, is a script that backs up personal files (like thunderbird and firefox profiles) prior to the copy script used after upgrades on systems with encrypted partitions, then restores the back ups after the copy so you don't lose overwrite your personal stuff.   Hmm, should post that one at least...

---

