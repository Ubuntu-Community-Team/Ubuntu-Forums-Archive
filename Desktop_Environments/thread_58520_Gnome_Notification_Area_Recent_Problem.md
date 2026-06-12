---
title: "Gnome Notification Area Recent Problem"
date: 2005-08-20
forum: Desktop Environments
---

### Post by jpoe on 2005-08-20
I prefer gnome for 95% of purposes, however I like a few apps from KDE over anything Gnome currently has to offer (ie, klipper and kgpg).  Since linux offers me the opportunity to have the best of both worlds, I run these few KDE apps inside of Gnome and they always appeared in my notification area happily with the rest of my Gnome apps...

...Recently, however, whenever they are started (usually at login) they appear in an entire seperate window (1 for each tray icon, which is obviouslly really annoying).  I'm not sure how this happened.  I don't think I changed any configuration settings, I just logged out and logged back in and thats the way it was.  I did install GnuCash using apt which I noticed installed a lot of extra library files that I wasn't expecting, could one of those have caused the change?  I would gladly uninstall GnuCash if it would solve this problem... so far I have searched and can not come up with a solution.  

Any help would be greatly appreciated,

Thanks

---

### Post by elempoimen on 2005-09-01
Now having the same problem here after installing KWin and XFCE.  I removed KWin, but it did no good.  Thinking of removing XFCE now, too. :(

---

### Post by Jeff Eklund on 2006-01-05
Sorry to revive an old thread, but I'm having the same problem as the guys above me. KDE programs with tray icons show up in a separate window. Haven't touched the system, just rebboted. 
Please, if someone sees this and knows how to fix it, I would be truly grateful. It's bloody annoying...

EDIT: It might have something to do with programs not being able to talk to klauncher?
I added an attachment to illustrate how theese separate windows look like.

---

### Post by habtool on 2006-07-01
Hi

After running Gnome with afew KDE apps, i also have the above problem..

Any Ideas?

---

### Post by chalito on 2006-07-21
I just had this problem, and it seems to be dcopserver.. or at least that's what I can guess: I closed all the kde apps, but when I restarted them I still had the problem. Then I closed them all again, and killed dcopserver, and that seems to have solved the problem. Kde apps now go into the tray normally.

hope it helps

---

### Post by mahendra on 2006-12-07
I still have this very same issue. Did anyone finally find the solution ?

cheers,
mahen

---

### Post by FaceLeg on 2007-03-13
> **mahendra said:**
> I still have this very same issue. Did anyone finally find the solution ?

cheers,
mahen

I had the same problem - couldn't find an answer either, so I resorted to the good old 'trial and error' approach (since I don't know much about LInux...

This is what worked for me:

```
faceleg@faceleg-desktop:~$ kdeinit
```

Which generated the following output:

```
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/faceleg/.DCOPserver_faceleg-desktop__0
and start dcopserver again.
---------------------------------

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!

```

I then loaded Amarok, and was pleased to see the icon appear in its rightful place, among its peers in the Notification area.

Hope this helped!

---

