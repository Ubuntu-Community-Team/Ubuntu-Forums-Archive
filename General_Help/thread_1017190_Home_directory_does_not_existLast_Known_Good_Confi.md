---
title: "Home directory does not exist/Last Known Good Configuration?"
date: 2008-12-20
forum: General Help
---

### Post by kms017 on 2008-12-20
I'm VERY new to Ubuntu and I've been searching for hours but I cant find any answers, please help!

I have a new Dell mini that loads all the way up till it comes to the Ubuntu log in screen thats when I get an error message saying, "Your home directory is listed as: '/home/katie' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you usea failsafe session.". The only failsafe session that will work is a terminal failsafe and while I know how to get in there honestly I dont know what to do once I'm there. As it is brandnew I'm not worried about losing any information but I dont have my external drives to restore using my disks is there a way to restore from the failsafe terminal session? PLEASE HELP!

---

### Post by taurus on 2008-12-20
After you've logged in, post the output of these commands to see if you even have a $HOME.

```
ls -la /home
tail -5 /etc/passwd
```

---

### Post by kms017 on 2008-12-20
ls -la /home :
total 12
drwxr-xr-x 3 root root 4096 2008-12-17 06:45.
drwxr-xr-x 23 root root 4096 2008-12-20 13:58..
drwxr-xr-x 36 doris doris 4096 2008-12-20 14:03 doris


tail -5 /etc/passwd :
Messagebus: x:109:118::var/run/dbus:/bin/false
avhi: x:110:119:Avahi mDNS daemon,,,:var/run/avahi-daemon:/bin/false polkituser: x:111:121: policykit,,,:/var/run/policykit:/bin/false haldaemon: x:112:122:Hardware abstraction layer,,,:/var/run/hald:/bin/false doris: x:1000:1000:Katie,,,,:home/katie:/bin/bash


I have to type it all out as I cant access anything so I'm pretty sure thats all correct.

---

### Post by unutbu on 2008-12-20
Type
```

sudo cp /etc/passwd /etc/passwd_20081220
```

This save a copy of your original passwd file, just in case.

Next type
```

sudo nano /etc/passwd
```

A text editor will appear. Go to the bottom of the file and change ```
doris: x:1000:1000:Katie,,,,:/home/katie:/bin/bash
```
to```

doris: x:1000:1000:Katie,,,,:/home/[COLOR="Red"]doris[/COLOR]:/bin/bash
```

Press Ctrl-X to save and exit.

Finally type
```

init 2
```
to resume a normal boot. You should end up at the gdm (graphical) login screen. Try to login as doris.

Good luck, tell us how it goes.

---

### Post by dcstar on 2008-12-20
> **kms017 said:**
> ls -la /home :
total 12
drwxr-xr-x 3 root root 4096 2008-12-17 06:45.
drwxr-xr-x 23 root root 4096 2008-12-20 13:58..
drwxr-xr-x 36 doris doris 4096 2008-12-20 14:03 doris


tail -5 /etc/passwd :
Messagebus: x:109:118::var/run/dbus:/bin/false
avhi: x:110:119:Avahi mDNS daemon,,,:var/run/avahi-daemon:/bin/false polkituser: x:111:121: policykit,,,:/var/run/policykit:/bin/false haldaemon: x:112:122:Hardware abstraction layer,,,:/var/run/hald:/bin/false doris: x:1000:1000:Katie,,,,:home/katie:/bin/bash


I have to type it all out as I cant access anything so I'm pretty sure thats all correct.

Can I make the assumption that the system was built with one user name (Katie) and later the user name was changed to Doris?

---

### Post by kms017 on 2008-12-20
Whenever prompted for a password I cannot enter anything whatever I type does not show up all I can do is hit enter and start over.

---

### Post by kms017 on 2008-12-20
It was started as Doris and changed to Katie.

---

### Post by kms017 on 2008-12-20
UPDATE:

I can now get on to the desktop using a testuser screen name how ever I really need to fix the main log in, it is the administer screen. Does anyone know how I can do this?

---

### Post by kms017 on 2008-12-20
Thanks for all the help! I've worked fixed it due to help from someone on the fourm, some how the home directory was changed and had to be changed back! Thanks so much for everything!

---

