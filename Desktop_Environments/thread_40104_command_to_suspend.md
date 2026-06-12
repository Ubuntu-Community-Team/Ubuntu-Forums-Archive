---
title: "command to suspend?"
date: 2005-06-07
forum: Desktop Environments
---

### Post by dave9191 on 2005-06-07
Hey guys, 

I can suspend to RAM by right clicking on the klaptop in my sys tray. But I would like to know how I can do that from the command line. I though that klaptop_acpi_helper --suspend (or standby) would do it since --hibernate hibernates the system. but that doesnt work for suspending. and I would like to assign to the command to one of my FN keys. The --suspend option actually shuts my system down. 

Dave

---

### Post by GrumpySimon on 2005-06-07
The gnome display manager uses this command to suspend: /usr/sbin/pmi action sleep

This may work for you instead

--Simon

---

### Post by dave9191 on 2005-06-08
Im affriad that I had no luck with that. Did nothing. When I did pmi capabilities, then it said it just does hibernate. Im guessing that its configured differently on kubuntu. 

Dave

---

### Post by NLChris on 2005-06-08
Try this (as root):

```
echo -n "mem" > /sys/power/state
```

Edit:
Or look at [http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM)

---

### Post by dave9191 on 2005-06-08
well that worked :) But I was hoping to attach that command to one of my hot keys. And running it as root isnt too handy. Even using sudo (which is doesnt like) wouldnt be good if it asked for the password. 

Ill have a read of the link now.

Dave

---

### Post by dave9191 on 2005-06-09
Well I read the link, but it suggests stuff that I have already tried and didnt work. Plus I cant have sudo infront of the command. It just has to be a plain and simple command I can assign to a hot key and wont ask me for a password.

---

