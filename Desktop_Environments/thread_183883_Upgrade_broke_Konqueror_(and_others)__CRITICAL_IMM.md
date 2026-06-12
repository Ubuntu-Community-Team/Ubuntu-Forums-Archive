---
title: "Upgrade broke Konqueror (and others?)  CRITICAL: IMMEDIATE HELP NEEDED"
date: 2006-05-28
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-05-28
I got online today, and looked in Adept. Seeing updgrades, I fetched QParted and upgraded the packages. Since then, I have not been able to explore my hard disk or anything else due to "mime type" errors or something. If I open it from a folder on the desktop, its fine. But I need to be "root" to back up these files and cannot do so because "mime is not installed" or something if I try to run it from the konsole.


EDIT: I cannot access any mounted folders or anything in /media or the root folder, for that matter ( / ). Error message:
```

Could not start process Unable to create io-slave:
klauncher said: Error loading 'kio_file'.
.

```


EDIT AGAIN:

Could not find mime type
application/octet-stream



EDIT: FIXED. I restarted the system, and it works. Yall really should include a "recommend restart" message or something. It scared the hell out of me


EDIT: Not fixed. The root user still cannot copy or paste files onto my USB drive and my other user is denied access.

---

### Post by Wr8EYilK8Y on 2006-05-28
Sorry for the double post, but I have a new problem and I cannot track all the upgraded packages because there were 40+ of them, but now the panel takes a long time to reappear at the bottom of the screen, if ever.

---

### Post by ltmon on 2006-05-28
Can you try doing the following, and then logging out of KDE the logging in again:

```

rm -rf ~/.kde/socket-<hostname>
rm -rf ~/.kde/tmp-<hostname>
rm -rf ~/.kde/cache-<hostname>

```

Replace <hostname> with your computers hostname.

This won't be destructive at all, it will just remove all temporary files and locks from KDE.  They'll be regenerated when you log in again.

If this doesn't work have a look in the file /var/log/kdm.log for any obvious errors.

Cheers,

L.

---

### Post by Wr8EYilK8Y on 2006-05-28
I'll try. I reinstalled the mime packages, now its not consistently copying/pasting files to the USB Hard Disk, and some other weird stuff.


EDIT: Oh yeah- other programs are having troubles too. 


Didn't work. Konsole errors are still same.

```

williamd@williamskubuntu:~$ sudo konqueror
Password:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-10670' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program


```

---

### Post by Wr8EYilK8Y on 2006-05-28
Double Post: See Above

---

### Post by ltmon on 2006-05-29
Ok, errors trying to "sudo konqueror" like that give me a hint.  There is some kind of permissions problem with your xhost, which is what controls access to the GUI for users.

Does "kdesu konqueror" work any better?

If this doesn't work try:

```

xhost +
sudo konqueror

```

L.

---

### Post by markitos on 2006-05-29
I am having problems also with kdesu.... when I am typing kdesu konqueror at the terminal, nothing happens. This is really worrying me, what can I do to solve this problem? Also there are problems at control panel, for example when trying to edit network connections. When I type my password to edit, nothing happens and the text stay "inactive".

Thanks guys for help

M

---

### Post by ltmon on 2006-05-29
[QUOTE=markitos]I am having problems also with kdesu.... when I am typing kdesu konqueror at the terminal, nothing happens. This is really worrying me, what can I do to solve this problem? Also there are problems at control panel, for example when trying to edit network connections. When I type my password to edit, nothing happens and the text stay "inactive".

Thanks guys for help

M[/QUOTE]

Unfortunately this sounds like you are being hit by a known bug in the older version of KDE used by Kubuntu 5.10 Breezy.  This causes the administrator mode button (especially in the control center) to fail more often than not.

The bug report is here: [https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/15001](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/15001)

It's fixed in later versions of KDE, and so will be available in the next release of Kubuntu in a few weeks, but other than that I can't help.

L.

---

### Post by markitos on 2006-05-29
Thanks, I will wait for the new release:)

---

### Post by Wr8EYilK8Y on 2006-05-30
Well, now the problem is quite different.
[http://www.ubuntuforums.org/showthread.php?t=184594](http://www.ubuntuforums.org/showthread.php?t=184594)

As far as the button failing, I just hit "Show All" and try again- that usually does the trick. BUT- the sudo DOES fail a lot

---

### Post by ltmon on 2006-05-30
Just make sure you read this page: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

> 
NEVER use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.


I think using sudo for graphical programs can create other errors also, maybe yours included (?)

CHeers,

L.

---

### Post by Wr8EYilK8Y on 2006-05-31
No, it didn't cause the Kubuntu crash- or not directly, at least. kdesu is much more reliable than sudo, anyway. I now use it to mount my hard disk from the desktop.

---

