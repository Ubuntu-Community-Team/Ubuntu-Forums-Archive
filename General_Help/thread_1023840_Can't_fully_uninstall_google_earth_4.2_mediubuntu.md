---
title: "Can't fully uninstall google earth 4.2 mediubuntu"
date: 2008-12-28
forum: General Help
---

### Post by 45acp on 2008-12-28
Synaptic returns an error when uninstalling goolge earth 4.2 from the mediubuntu repros. It says something about it being a bad package. It is listed as not installed but Synaptic will not completely remove it (configuration files) I tried reinstalling and removing it from the terminal with apt-get install and apt-get purge with the same results. Any ideas?

---

### Post by randallecook on 2008-12-28
For installed packages, Synaptic lists the files that were installed, so you can remove them manually, if that is important. Yes, this is hacking, and not to be done lightly. Of course, to do the job right you probably would want to update whatever data structure Synaptic/apt-get uses to record which packages you have installed. I don't know how to do that. The man page for apt-get lists a lot of options. Maybe you could start there, if you haven't already. Good luck.

Randall

---

### Post by 45acp on 2008-12-28
I tried removing the files manually but synaptic still shows Not Installed (residual config.) Its not really a big deal. I installed the latest version of Google Earth - 4.3 and it works fine. Just a little annoying that I can't completely get rid of 4.2 is all. Thanks for the reply.

---

### Post by randallecook on 2008-12-28
Yeah, it is annoying. I love the package management system--it makes it so easy to acquire software, but there is this repository thing that must never break for the system to stay usable. It's like the Windows registry but for Linux :(

Randall

---

### Post by radens on 2009-02-08
try this ... first run

**sudo apt-get remove googleearth**

then

**sudo apt-get autoremove**

---

