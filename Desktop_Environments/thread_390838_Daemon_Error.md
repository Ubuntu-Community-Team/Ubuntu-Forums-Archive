---
title: "Daemon Error"
date: 2007-03-22
forum: Desktop Environments
---

### Post by simonalexander2005 on 2007-03-22
Hi,

I have edgy eft 6.10.???.11.

I have just done some system updates (for the first time after installing last week). now, when I try to log in, I can get past the login screen, but then have to wait 10 minutes for the desktop to load. when it does load, there is an error message saying:

"There was an error starting GNOME settings Daemon. Some things, such as themes, sounds or background settings may not work correctly. The last error message was:"

[the error message shown varies on each logon. The first one i got was]

"unable to determine the address of the message bus. (try 'man dbus-launch' or 'man dbus-daemon' for help)
GNOME will still try to restart the settings Daemon next time you login."

when I do finally log in, the theme (Human) isn't working

help...?!?!?

---

### Post by ernstblaauw on 2007-03-22
I got the same error. I think it is caused by an update this day. I actually installed a couple (FUSE, beryl, some KDE stuff). Has anyone else this error?

---

### Post by ayoli on 2007-03-22
what happens if you trying to run gnome-settings-daemon from CLI (command line) ? if your theme works after running this put this command in your startup progs (menu System>Preferences>Session then Startup Programs tab)

---

### Post by ernstblaauw on 2007-03-22
> **ayoli said:**
> what happens if you trying to run gnome-settings-daemon from CLI (command line) ? if your theme works after running this put this command in your startup progs (menu System>Preferences>Session then Startup Programs tab)

I tried that, but I got an error message (cannot connect to dbus or something).

However, my Ubuntu is running fine now. What I did: Select KDE as session, which started fine. However, my screen was still running at a lower resolution so I guessed something was wrong with my zorg.conf. And indeed: a new one has overwritten my old one, but by backing up my old one. So I copied that one back, and restarted my computer. Now everything works fine!

---

### Post by cyrano24100 on 2007-04-01
> **ernstblaauw said:**
> I tried that, but I got an error message (cannot connect to dbus or something).

However, my Ubuntu is running fine now. What I did: Select KDE as session, which started fine. However, my screen was still running at a lower resolution so I guessed something was wrong with my zorg.conf. And indeed: a new one has overwritten my old one, but by backing up my old one. So I copied that one back, and restarted my computer. Now everything works fine!

Hum, I'm getting the exact same error message as reported above: first time install on a 64-bit server, so I'm not sure where to go. Let me say though that it takes 30 minutes for an error message to come up - same as above  "There was an error starting GNOME (...)"  It takes another 30 minutes for GNOME to finally comeup and it doesn't look like I'm missing icons or themes...

Now, I don't get your "fix" above.. zorg.comf I'm assuming is xorg.conf, which has not moved, so must be something else. as for initializing GNOME on command line I'll have to try... I just wish there was something to point to (missing file/line/conf)

Adiusiatz!

---

### Post by iluminate on 2007-04-13
Same problem here! 
Happens when I log in and then the screen flickers and the background (wallpaper) looks like its in 8 bits and then I get an automatic logout!
Checked logs -
and it said something with dbus deamon.

Will do some updates (can only log in with safeMode Gnome) and the restart to see if it helps.

Cheers

---

