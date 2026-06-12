---
title: "sharing files between Ubuntu/Lubuntu"
date: 2010-11-04
forum: Desktop Environments
---

### Post by MZ250Supa5 on 2010-11-04
I have a problem sharing files between two machines on my network, one, my main one running 10.10 and the other running Lubuntu.  I've used the share files option on my main computer, and they show up on the Lubuntu machine, but when I try accessing the files, I get a message telling me that they'failed to mount'.  It's frustrating in that I can see that the files are there, and obviously the Lubuntu machine can 'see' them too.  I'm sure that I must have missed out something, and I've tried searching, but so far have only come accross some very old tutorials that just confuse me more.  Surely there must be a fool proof way of getting this all working?  Any help would be most appreciated. (I've tried Giver, but the Lubuntu machine refuses to run Giver!)

---

### Post by Morbius1 on 2010-11-04
"failed to mount" is usually not a samba issue but a linux file permissions issue.

Post the output of the following commands from the "main computer" so we can see how you are set up:
```
net usershare info --long
```
```
testparm -s
```

---

### Post by Paul A C on 2010-11-09
Are you getting an error along these lines -->
Dbus error
org.freedesktop.DBus.Error.NoReply  ?
If so, I may be able to help.

---

### Post by MZ250Supa5 on 2010-11-12
Thanks, I got it working quite nicely about 10 minutes after posting my request for help - it seems that I was mouse clicking too fast and 'confusing' the Lubuntu machine which is really geriatric!  It now works well on this machine, and over the wireless network to my laptop.  Now all I need to do is to work out how to share files from the Lubuntu machine with all my other computers as it's not as simple as with the Gnome desktop... (It probably is, and I'm just too sleep deprived to work it out!)

---

