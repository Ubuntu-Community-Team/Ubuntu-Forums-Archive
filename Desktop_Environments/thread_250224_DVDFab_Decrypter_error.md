---
title: "DVDFab Decrypter error"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Corp_Punisher on 2006-09-03
Hi.

I am fairly new to Ubuntu and am currently trying to get DVDFab Decrypter (The free version 2.9.8.3) to run. I ran the install using wine (the latest version of wine from syaptic) and was able to establish a working shortcut link. I have the application open the terminal as I do with DVD Decrypter and DVD Shrink, both of which work well.

DVDFab Decrypter attemts to open but there is a small "error" window that simply says "error" with an OK button. The terminal gives the following result:

Xlib:  extension "GLX" missing on display ":0.0".

I also followed the advice found here:

[http://appdb.winehq.org/commentview.php?iAppId=2377&iVersionId=3372&iThreadId=10644](http://appdb.winehq.org/commentview.php?iAppId=2377&iVersionId=3372&iThreadId=10644)

But with the exception that once I placed those files in the /system32/ folder with the same "error" results I then also copied them into the /system/ folder as well. Same result.

Is there some type of glx file I need or possibly an edit to a config file that would remedy the situation?

Edit: I am running a new install of Dapper (Not an upgrade, but an original Dapper version 6.06

---

### Post by Corp_Punisher on 2006-09-03
Bump

---

### Post by orb9220 on 2006-09-03
"Xlib: extension "GLX" missing on display ":0.0"."

I believe refers to your linux video nothing to do with wine or dvdfab.
what video drivers do you have installed? What is your video card type?

---

### Post by Corp_Punisher on 2006-09-03
I have an NVidia 6600 AGP.

The Driver is from synaptic more than likely.

That version is nvidia-glx 1.0.8762+2.6.15.11-3.

I am able to run DVDDecrypter and DVDShrink with no problems. It's just the one error issue with DVDFab Decrypter.

---

### Post by Corp_Punisher on 2006-09-04
bump

---

### Post by Corp_Punisher on 2006-09-04
OK. I just installed the latest NVidia driver for my box per here:

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

Installed like a charm.

Now, I still get the small error box but the Terminal window is blank now. In otherwards, the GLX error is no longer there, Unfortunately there is still an error which is keeping DVDFab Decrypter from opening.

Is there some sort of log file that I might read that could tell me what is or is not occuring? If so, I could post the info.

---

### Post by orb9220 on 2006-09-04
Well did you check winehq in thier app database and verified that it works. Not just program name but you must match version numbers. Example version 3.1.1 works but when you try 3.1.2 it dosn't. This is common annoyance in getting apps to run in wine.

---

