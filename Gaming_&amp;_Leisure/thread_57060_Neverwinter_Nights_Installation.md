---
title: "Neverwinter Nights Installation"
date: 2005-08-15
forum: Gaming &amp; Leisure
---

### Post by ItIsMe on 2005-08-15
Whenever I try to run Neverwinter Nights I get a message saying;


: command not found
: command not found
: command not found
: command not found
./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory


Does anyone know how to fix this?

---

### Post by matid on 2005-08-15
[QUOTE=http://nwn.bioware.com/forums/viewtopic.html?topic=203196&forum=72]Use the ./nwn script. It sets up your LD_LIBRARY_PATH properly to include ./miles, which is where it is located.
[/QUOTE]
Next time try to [google](http://google.com/search?q=libmss)

---

### Post by ItIsMe on 2005-08-15
What code am I meant to type in?

---

### Post by Muhammad on 2005-10-10
> muhammad@ubuntu:~$ cd NWN
muhammad@ubuntu:~/NWN$ ./nwn
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
muhammad@ubuntu:~/NWN$


:/

---

### Post by wylfing on 2005-10-10
@ItIsMe - As advised, open a terminal and go into your nwn directory. From there, type nwn. That's it.

@Muhammad - If you are getting segfaults when you try to launch Neverwinter, you have bigger fish to fry. Are you sharing this install in any way with a Windows install? Did you copy files over from a Windows install? Neither of those work in my experience. You need to do the Linux install from the ground up. See [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html).

---

### Post by kaamos on 2005-10-10
Following these instructions seems to fix most nwn problems. Mine at least.

[http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72)

---

### Post by Muhammad on 2005-10-13
[QUOTE=wylfing]Did you copy files over from a Windows install?[/QUOTE]

Yep, I guess this is my problem...

---

### Post by Badjaccur on 2007-08-31
Running the checks showed that some files were corrupted and even missing. I also used files from a Windows install. Everything runs fine now.

---

### Post by hikaricore on 2007-08-31
Stop digging up old threads folks.

Closed.

---

