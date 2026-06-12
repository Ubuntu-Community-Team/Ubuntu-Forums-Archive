---
title: "evolution requires reboot to launch after closing"
date: 2006-03-23
forum: Desktop Environments
---

### Post by jjf on 2006-03-23
There are some funky things happening with my installation of Ubuntu Breezy.  I'll list the big 3 here.  Right now I'm focusing on #3, but if you know an easy fix or a good link for the first 2, I'd be glad to know it.

 1. when I **r-click > properties > open with**, any application I select or type in the little command line gives this error: "Could not add application to the application database"
 2. I can't run "Applications Menu Editor" from the menu.  An entry appears in my "taskbar" at the bottom like it's about to start, then the entry disappears and smeg doesn't start.  I have to go to terminal and type "sudo smeg" (typing just "smeg" in the terminal gives me errors I don't understand).  
 3. Evolution won't relaunch after I close it.  It will run the first time after I've rebooted, but if I close it and try to reopen, it won't.  Like smeg, an entry appears in my "taskbar" for a few seconds, then vanishes and nothing else happens.  In order to get evolution working, I have to reboot.

Pertinant info:

- running "evolution" in the terminal returns this error msg:
```
(evolution:13306): Bonobo-Activation-WARNING **: Strange exception (IDL:omg.org/CORBA/COMM_FAILURE:1.0) from active server registration
```

- running "sudo evolution" in the terminal returns this error msg:
```
(evolution:13266): evolution-smime-WARNING **: initializing security library without cert databases.
adding hook target 'source'
Setting up initial mail tree
addressbook_migrate (0.0.0)

(evolution:13266): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
```
...but evolution does start with it's "welcome new user, let's set up your account" screen like I'm just running it for the first time.

- In my System Monitor, I can see these two processes running: evolution-alarm-notify (taking up 55.8 MB of virtual memory) and evolution-data-server-1.4 (taking up a whopping 256.5 MB of virtual memory).  I've tried ending both those processes, but evolution still won't launch.

Any help would be greatly appreciated.

---

### Post by jjf on 2006-03-23
<bump>

---

### Post by jjf on 2006-03-24
<bump>

Any ideas?

---

### Post by trent dillman on 2006-03-24
Reboot

then
```

ls -laAR /tmp/ > ~/no_evolution.txt 2> /dev/null

```

This will dump a txt file into Home with a long listing of all files, recursively, in /tmp (dumping errors about permissions that will inevitably occur)

start evolution
close it
then

```

ls -laAR /tmp/ > ~/evolution.txt 2> /dev/null

```

then post the results of this command:

```
diff ~/no_evolution.txt ~/evolution.txt
```

or just see if there's a tmp lock somewhere :p

---

### Post by hw-tph on 2006-03-24
...or just run **evolution --force-shutdown** instead and see if it's possible to start it again after that.


Håkan

---

