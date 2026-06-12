---
title: "Why must the file manager insist on not responding?"
date: 2010-04-14
forum: Desktop Environments
---

### Post by drinkleadsoup on 2010-04-14
I fixed it:

[http://ubuntuforums.org/showthread.php?p=9100417#post9100417](http://ubuntuforums.org/showthread.php?p=9100417#post9100417),

but then after use the other day, the file manager did it again.

Cannot click on anything, the icons on the desktop disappear, everything is sluggish, and just the entire user environment is freaking frustrating.  

This is what I get when I type nautilus in a terminal:

[HTML]corey@computkenstein:~$ sudo nautilus
[sudo] password for corey: 

(nautilus:5317): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:5317): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5317): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5317): WARNING **: No marshaller for signature of signal 'ShareCreateError'

[/HTML]

I don't want Thunar.  I want my Desktop back.

If there is anyone who believes they know a permanent fix, please, please, please let me know.

---

### Post by drinkleadsoup on 2010-04-14
Bump, and I forgot to add instant email notification subscription.

---

### Post by drinkleadsoup on 2010-04-18
So, on my 10.04 machine, yesterday I was watering my plants and my laptop was beneath my watering table, and I was like ****.  Then, I dried it out, and I have my file manager back on my machine.

I am afraid to try this on my 9.10 machine because it is the nicer computer.  

Seriously, this worked.  

I wish I knew what really fixed it though.  I messed around with some settings, and I haven't updated in a while.  I really just want a permanent fix forever.

Anyone know?

---

### Post by drinkleadsoup on 2010-05-16
I figured out the problem is with .svg files on my desktop.

---

