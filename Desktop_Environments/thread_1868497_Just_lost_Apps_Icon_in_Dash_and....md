---
title: "Just lost Apps Icon in Dash and..."
date: 2011-10-24
forum: Desktop Environments
---

### Post by Matt 6:27 on 2011-10-24
... "More Apps" icon, while present in Dash, doesn't do anything and won't display any of my installed Apps.  This started just after this morning's update and an attempt to run Kino under Alt-F2. Rebooting didn't help.  Any pearls of wisdom out there?

---

### Post by blackmail on 2011-10-24
I would gladly help, but please give a bit more details, what is missing from where, please also a screenshot if possible.

Thank you in advance

---

### Post by Matt 6:27 on 2011-10-24
Thanks for giving it a shot.  Below is a shot of the Dash... notice just three icons at the bottom (applications is missing).  A second image is of a search for apps in which I look for Kino (which I know is installed) and there are no results.  In the Dash, three of the four options (Media Apps, Internet Apps, More Apps return blank pages.  The Files button does seem to work. Software Center in the Launcher also appears to have a problem as it won't load after hitting that Launcher icon.  All worked very early today.  Thanks again.

---

### Post by AppleWiz on 2011-11-13
Sorry not be really helpful...

But I have the exact same problem in 32-bit. I tried "unity --reset-icons fromt the terminal, but no effect. Still hunting for an answer!

~Rob

---

### Post by ricardof84 on 2011-11-14
i am having the same problem. But i haven't tried 'unity --reset' yet...

---

### Post by Matt 6:27 on 2011-11-14
Since my install was so recent, I decided to re-install using the 32bit version of Oneiric.  Not certain it had anything to do with the 64bit version, but the problem went away and has not recurred.

---

### Post by gogink on 2011-11-14
Having same problem , just run unity --reset, and terminal throw me this:

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4400044

WARN  2011-11-14 19:13:30 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-14 19:13:30 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
compiz (core) - Warn: unhandled ConfigureNotify on 0x1000095!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
I use 64-bit ubuntu onoric, and this happened after update.

---

### Post by gogink on 2011-11-14
ooook, after some long talk with google, found this
[http://askubuntu.com/questions/43096/unity-lenses-missing-files-folders-applications](http://askubuntu.com/questions/43096/unity-lenses-missing-files-folders-applications)

And when i check if is package unity-place-applications installed, i found out that is NOT!!! I am sure that i had it installed, but after update something went wrong. I install it again, with all dependencies that synaptic sugested, restart and evrything was fine again. Any explanation for this?

---

