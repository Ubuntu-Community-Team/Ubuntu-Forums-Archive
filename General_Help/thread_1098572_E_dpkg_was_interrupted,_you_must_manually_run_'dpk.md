---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2009-03-17
forum: General Help
---

### Post by AICollector on 2009-03-17
The error is; 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I'm getting that from the Update manager and Synaptic, both of which can no longer function!

Help!


Hoping my system isnt trashed,
-AIcollector

---

### Post by m_duck on 2009-03-17
Open up a terminal (Applications -> Accessories -> Terminal) and run```
sudo dpkg --configure -a
```then```
sudo apt-get update
```It will ask for a password the first time and it will be your login password assuming you are the only (or first) user on the computer. That should fix it and enable you to use synaptic again.

---

### Post by blazemore on 2009-03-17
Do what M-duck says.
This is caused by exiting an application like apt or synaptic, without letting a dpkg process finish.

---

### Post by kamicosmos on 2009-04-12
i get the same error, and when I run the sudo commands above, I get the same error again in the terminal window....

---

### Post by pleckie on 2009-04-12
<s>I'm having the same symptoms as kamicosmos.  dpkg isn't clearing with the suggested commands.</s>

clear out /var/lib/dpkg/updates with a sudo rm

then apt-get runs as expected.

that is all.

---

### Post by EmperorMoo on 2009-04-13
I was having the same problem as kamicosmos.  All fixed now thanks to pleckie's post.

---

### Post by kamicosmos on 2009-04-16
the rm command wouldn't work for me either.  I finally just open Nautilus with sudo via terminal, and cleared out the update folder that way.  Then, my system updated finally.

---

