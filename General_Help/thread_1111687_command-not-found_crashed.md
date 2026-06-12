---
title: "command-not-found crashed"
date: 2009-03-30
forum: General Help
---

### Post by steevz on 2009-03-30
Okay, I downloaded some levels for Pingus and extracted them in my ~/downloads folder and it said some files couldn't be transferred then my icons in my quick bar disappeared, I couldn't access my home folder, ect so I tried to reset X Server with Ctrl+Alt+Backspace and I got the following error and it keeps happening on boot. I think I typed: sudo mv share/* usr/*

share/ had all the directories to put the levels in the right place, don't know what happened.

I get something telling me there is No resume image, doing normal boot... then I get command line in boot.

If I type xserver or hit ctrl+alt+F7 I get something like this:

command-not-found has crashed.

command-not-found version: 0.2.21
Python version: 2.5.2 final 0
Distributor ID: Ubuntu
Description: Ubuntu 8:10
Release: 8.10
Codename: intrepid
Exception information:

[Errno2] No such file or directory: '/usr/share/command-not-found/programs.d'
Traceback {most recent call last):
File "/usr/lib/python2.5/site-packages/CommandNotFound/util.py", line 32 in crash_guard
File "/usr/lib/command-not-found", line 24, in main
         Command NotFound{options.data_dir).advise(args[0], options.ignore_installed)
File "usr/lib/python2.5/site_packages/CommandNotFound/CommandNotFound.py, line 63, in __init__

OSError: [Errno2] No such file or directory: '/usr/share/command-not-found/programs.d

Any help would be great. Thanks.

---

### Post by steevz on 2009-03-31
bump

---

### Post by steevz on 2009-03-31
If I go into the recovery console are there any commands I can type to restore my default system files? Or from the live CD?

---

### Post by steevz on 2009-04-01
Is it really that hard to just backup all my programs to put on a new install on Linux. I just want to know what directories to backup so my new install will have all the software mine does now. I have an external.. if someone could just tell me what directory trees contain all my software I'll be good to go.

Thanks,

steevz

---

### Post by steevz on 2009-04-02
Heyro?

---

### Post by steevz on 2009-04-04
Well, I got it backed up no thanks to anyone on here.

Copied my home directory to my external and then used the command
```
 dpkg --get-selections > /backup/directory/programs.log 
```

After I reinstalled linux I just copied my home folder back over and then ran
```
 dpkg --set-selections < /back/directory/programs.log 
```

So, I've got it working again.

---

