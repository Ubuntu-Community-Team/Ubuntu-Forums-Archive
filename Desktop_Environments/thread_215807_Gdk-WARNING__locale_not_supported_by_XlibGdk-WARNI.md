---
title: "Gdk-WARNING **: locale not supported by Xlib
Gdk-WARNING **: cannot set locale modifi"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Bad2theBone on 2006-07-14
I've noticed that when I start a GUI app from a terminal I'll get the above error:
Gdk-WARNING **: locale not supported by Xlib

Gdk-WARNING **: cannot set locale modifiers

I'm not sure if this is a problem because the apps will continue to run. When I do a locale -a I'll get:

C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

Is this correct, or am I barking up the wrong tree?

TIA

---

### Post by Bad2theBone on 2006-07-17
Problem has been resolved. I didn't realize that the lang. setting was set to another nationality of english, Using Lang. Supp. to reset to eng_US (System -> Administration Tools -> Language Support) fixed the problem. I'm still not sure how it got changed since I know I had set it right on install. The only thing I can think of is that it seems (the errors) to have started after I installed MSFonts. The curse of M$, I guess!:rolleyes:

---

### Post by sleepyrohan on 2006-12-07
i have the same problem. that is i see 
Gdk-WARNING **: locale not supported by Xlib

Gdk-WARNING **: cannot set locale modifiers

everytime i open a gui app from terminal too.

also i too get the same output with locale-a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

however i tried changing language to english(united states of america) form english(india), and it makes no difference. even the output for locale-a remains the same. what shoulld i do? btw the apps run fine..just want to remove this annoying message.

---

### Post by elektrolott on 2006-12-12
I have the problem, too:


lothar@zaphod$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=


lothar@zaphod$ /opt2/linux/ix86/eclipse-3.2/eclipse

(process:6032): Gdk-WARNING **: locale not supported by C library

(<unknown>:6032): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

---

