---
title: "Gnome-Pilot Setup Assistant"
date: 2004-12-11
forum: Desktop Environments
---

### Post by bubble on 2004-12-11
I accidentally clicked on gnome-pilot and it launched the set-up assistant.  I canceled out of it and now the set-up assistant starts (sometimes even twice) every time I log in .
Can anyone help?  8-[ 

tia

---

### Post by bubble on 2004-12-13
[-o<

---

### Post by bubble on 2004-12-14
I can't believe i'm the only one with this problem...

---

### Post by Rancoras on 2004-12-14
See if there's a preferences file in your home directory.  It may be named .gpilot or .gnome-pilot or something like that.  You may need to "show hidden files" in nautilus.  Delete it if you find it, that should make it like it was never run in the first place.

---

### Post by bubble on 2004-12-14
Thanks a lot, gonna give it a try  :o

---

### Post by wazoo on 2004-12-29
Try these two commands:

$ sudo ps -ef | grep pilot

This lists any process currently running the gpilot daemon (or anything else connected to a pilot. After your user name, you'll see a process ID number, eg. "1833"

$ sudo kill 1833

Do that for all instances of gpilotd, and the problem should go awa.

---

