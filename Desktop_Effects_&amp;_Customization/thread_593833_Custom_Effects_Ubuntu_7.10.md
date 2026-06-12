---
title: "Custom Effects Ubuntu 7.10"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by rjtrumbley on 2007-10-27
Hi, I have compiz effects enabled without a problem I can go to System--> Preferences --> Appearance and choose Visual Effects and pick None, Normal or Extra without any issues. Everything works.

The problem is I have installed the compiz settings manager to try to change the effetcs for opening / closing windows ..etc.

That added an extra option called "custom" 

When I choose custom and close the window then go back an look it switchs from custom to extra every time.

Not enabling any of the changes I made.

Does anyone know what I am doing wrong?:confused:

---

### Post by itsbradman on 2007-10-27
not sure.  try removing ccsm and reinstalling it.

---

### Post by ThrobbingBrain66 on 2007-10-27
Are you using the gconf or flat-file backend?  To find out, go to preferences in compizconfig settings manager.  You may just need to change between the two.

Flat-file works best for me.  You must also have the Inotify plugin active for it to work correctly.

Your problem doesn't have anything to do with not staying on Custom....mine doesn't either.

---

### Post by rjtrumbley on 2007-10-31
That worked, thank you :)

---

