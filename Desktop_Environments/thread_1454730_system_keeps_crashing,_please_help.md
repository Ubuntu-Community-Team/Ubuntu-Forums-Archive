---
title: "system keeps crashing, please help"
date: 2010-04-15
forum: Desktop Environments
---

### Post by meomike2000 on 2010-04-15
i installed ubuntu 9.10 few months ago and all has been working well till couple days ago. now when i open something it will exit on its on normally as soon as it is done loading. when i try to install or remove anything from the command line or through the gui, dpkg crashes....

can somebody help me find the problem and get this fixed....

also, if the app that i open dont close, if i open it again after i close it, it will close on its on......

---

### Post by meomike2000 on 2010-04-15
also i found i have 1 broken package, firestarter , and it is missing menu.

i tried to remove and error, said to reinstall before trying to remove, so i tried to reinstall and it errors...

this is the details

(Reading database ... 40%dpkg: unrecoverable fatal error, aborting: files list file for package 'python-gmenu' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2) A package failed to install.

thanks again mike.....

---

### Post by meomike2000 on 2010-04-15
ok used the recovery console and got the firestarter issue fixed, this hadnt worked the first few tries, i would get the same error....

but the reason i was istalling firestarter was due to the page closing problem, it was doing this with firefox only at first.

so still need some help please, mike

---

### Post by iponeverything on 2010-04-15
```
/var/lib/dpkg/info/python-gmenu.list
```

Is corrupted. Delete it and do:

```
sudo apt-get install python-gmenu --reinstall
```

---

### Post by meomike2000 on 2010-04-16
i got the corrupted file fixed with the reinstall of firestarter from the recovery console. but i still need to get the original problem fixed and that is whatever i have open just closes on its on and goes back to the desktop... it is not always sudden though normally, sometimes it is delayed by a few minutes....

any help with this issue would be great.....

---

### Post by meomike2000 on 2010-04-16
well, i think that i found the problem, it appears to be a bad memory stick, as i take out that stick and the problem seams to go away......

thanks mike....

---

