---
title: "[SOLVED] no gdesklet-deomon"
date: 2007-10-30
forum: Desktop Environments
---

### Post by cybergalvez on 2007-10-30
I tried to run the gdesklet shell (I want to add some desklets) and I get an error "unable to connect to gdesklet-deomon"

I checked synaptec and gdesklets is installed, what do I do, I have no idea how to use gdesktes
Thanks in advance for any and all help

Jose

---

### Post by taurus on 2007-10-30
Try running it from a terminal.

Applications -> Accessories -> Terminal
```
gdesklets start
```

---

### Post by cybergalvez on 2007-10-30
> **taurus said:**
> Try running it from a terminal.

Applications -> Accessories -> Terminal
```
gdesklets start
```


Tried that I this is what I got:

```
jc@phoenix:~/Downloads/firefox$ gdesklets start
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
```

Jose

---

### Post by taurus on 2007-10-30
Which release are you using and you did install both gdesklets & gdesklets-data?

---

### Post by cybergalvez on 2007-10-30
> **taurus said:**
> Which release are you using and you did install both gdesklets & gdesklets-data?
How do I find out which release I have, I just did the install from gutsy's add-remove programs.  When I check under synaptic it says that both are installed.  Shoud I reinstall?
Jose

Well i tried to reinstall and synaptic won't let me reinstall it - which I don't get why either
Jose

---

### Post by cybergalvez on 2007-10-31
anyone know how to use gdesklets? every time I try to start it I get an error stating that the deomon is not started (this is on gutsy)
Jose

---

### Post by cybergalvez on 2007-10-31
Found the answer in this post:
[http://ubuntuforums.org/showthread.php?p=3631953]("http://http://ubuntuforums.org/showthread.php?p=3631953")

easy to do and fixes it
Jose

---

### Post by KIAaze on 2008-03-23
The link you gave doesn't work.
And I currently have the same problem on hardy, even after compiling gdesklets from source. :/

---

### Post by cybergalvez on 2008-03-26
> **KIAaze said:**
> The link you gave doesn't work.
And I currently have the same problem on hardy, even after compiling gdesklets from source. :/

Thanks I entered the link wrong the correct link is [http://ubuntuforums.org/showthread.php?p=3631953]("http://ubuntuforums.org/showthread.php?p=3631953")

---

### Post by KIAaze on 2008-03-27
Thanks.
I did that, but I still get:
> Starting gdesklets-daemon...
Connecting to daemon [    ###      ]You need a recent version of PyGTK to run this program.

Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.


And ~/.gdesklets/logs is empty. :/

---

