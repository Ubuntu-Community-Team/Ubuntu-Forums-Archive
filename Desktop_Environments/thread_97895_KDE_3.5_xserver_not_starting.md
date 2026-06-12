---
title: "KDE 3.5 xserver not starting"
date: 2005-12-01
forum: Desktop Environments
---

### Post by nrwilk on 2005-12-01
I just installed KDE 3.5 and after a reboot the xserver tries to start, but I immediately get a segfault, before it shows me the login screen.  I get the nvidia splash, then the spinning cursor, then the blue background, then the segfault.  Any ideas?  At this point I'm forced to use only the command line.


I'll brb with the segfault's details.

EDIT:  OK, the specific error is this:

the application unknown (kdmgreet) has crashed, causing a signal 11 (SIGSEGV).

When I hit the cancel button, the same error just pops up again and it throws me into tty1.

---

### Post by ltmon on 2005-12-01
Have you tried deleting the KDE temporary and cache directories

~/.kde/tmp-<hostname>
~/.kde/socket-<hostname>
~/.kde/cache-<hostname>

L.

---

### Post by nrwilk on 2005-12-01
[QUOTE=ltmon]Have you tried deleting the KDE temporary and cache directories

~/.kde/tmp-<hostname>
~/.kde/socket-<hostname>
~/.kde/cache-<hostname>

L.[/QUOTE]
I had not tried it, but now that I have tried it, my problem is completely fixed!  Thanks so much!

I was afraid to delete the files, so I just renamed them.  Is it ok to delete them?  I once had someone suggest that I delete my ~/.kde directory, and when I renamed it I lost all my settings.  I was really glad I hadn't deleted it.

Will I lose anything if I delete these?

---

### Post by ltmon on 2005-12-01
Glad it helped :)  This has become my "first thing to try" whenever I experience or hear about a weird KDE problem.

The tmp, socket and cache directories all contain temporary files only.  If you delete them then your next KDE startup will be a bit slow, but that's the only effect you will have.

L.

---

### Post by nrwilk on 2005-12-01
[QUOTE=ltmon]Glad it helped :)  This has become my "first thing to try" whenever I experience or hear about a weird KDE problem.

The tmp, socket and cache directories all contain temporary files only.  If you delete them then your next KDE startup will be a bit slow, but that's the only effect you will have.

L.[/QUOTE]


Thanks again, man.  I'll remember this fix for sure!

<Strongbad-style> DELETED! </Strongbad-style>

---

### Post by nrwilk on 2005-12-04
Gah!  Ok, so the problem is a bit more persistent than I had been able to see last time.

Turns out that it happens every time I boot up the computer now, and to get it to start correctly, I have to go to a tty and type
```

$ sudo /etc/init.d/kdm stop
$ startx

```
and then it works.  It may have been that I had in effect done this the last time when I deleted those files, and mistaken the cure as the file deletion, when the real fix came from the stopping and restarting of the xserver.

Any new ideas?

---

### Post by nrwilk on 2005-12-06
OK, everything is working now.  Looks like all I needed to do was do a few more update/upgrades in Adept.  Now I can log in graphically!

That's probably a good suggestion for those who are upgrading to KDE 3.5.

Do several upgrades.

---

### Post by joey111 on 2006-02-23
hi, i had the same pro when upgrading konqueror; the kdm displaymanager had gone, the crashbomb said: kdmgreet caused 11 (SIGSEGV).
I had tried to use the VESA driver with
```
dpkg-reconfigure xserver-xorg
``` before but it didnt help.with ```
startx
``` ic just could enter ubuntu;
so
for me that above worked superbly, thanks guys!
joey

---

