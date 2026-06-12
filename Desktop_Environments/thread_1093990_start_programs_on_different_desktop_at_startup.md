---
title: "start programs on different desktop at startup"
date: 2009-03-12
forum: Desktop Environments
---

### Post by klemens on 2009-03-12
Hi i'm looking to start different programs on different desktops @ startup, like for example amsn on desktop 3.

Using Ubuntu 8,10 64bits with kde 4.2 installed on it.

What i've tried.
make a startup script start.sh

sudo gedit /etc/init.d/start.sh

```
#!/bin/sh
kstart --desktop 3 amsn &
```

or add amsn to the startup sequence and make it listen to kstart --desktop 3 amsn.

by launching both of them i get the same result all the programs startup @ boot but on desktop 1.
The terminal gives me an error when i launch the startup script.
```
klems@ubuntu:~$ kstart(6762) main: Omitting both --window and --windowclass arguments is not recommended
kstart(6761) main: Omitting both --window and --windowclass arguments is not recommended
*** Search: Starting search engine enumeration...

*** Search: search engine enumeration done...


```
but still programs start on the different desktops it just ain't working on startup atm.

I also tried to startup the program a little later with the wait command in the script (to be sure that everything is loaded), didn't help either.

can somebody help?

---

### Post by mtbsoft on 2009-03-12
Don't know if it will work with KDE but I use devilspie to open certain applications on specific desktops, then I just launch them at session start and they appear on the requisit desktops.

---

### Post by klemens on 2009-03-23
devilspy looks like a powerfull program but it isn't really user friendly.

I tried it and i don't have the time to spend as much time on this, anyone an other idea?

---

### Post by mtbsoft on 2009-03-23
There is a UI for it called gDevilspie.  Sometimes *you* have to do a little work to get things to happen exactly like *you want.*

---

### Post by mcduck on 2009-03-24
If you use Compiz, you can use the Window Rules-plugin to define which workspaces your applications will be located when started. Then you'll just need to add apps to startup like normally and everything should work fine.

---

