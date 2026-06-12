---
title: "Broken packages"
date: 2009-05-11
forum: General Help
---

### Post by Emil M on 2009-05-11
After I installed Kopete
# sudo apt-get install kopete
I accidentally have broken files which I'm unable to reinstall:

kdebase-runtime
kdebase-runtime-bin-kde4
kdelibs-bin
kdepimlibs5
khelpcenter4

I hope someone has the answer, I just installed Ubuntu and got no clues :-(

---

### Post by alexandari on 2009-05-11
Synaptic Package Manager to the rescue! 

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

this will help :) Scroll down for "How To Fix Broken Packages"

you can try **sudo apt-get install -f** too

---

### Post by BslBryan on 2009-05-11
Hello, Emil M. :-)

What is the exact command you are running, and what is the exact response?

EDIT: alexandari beat me to it. :-)  If his solutions don't work (which they should) I do have one other thing to suggest.  Good luck!

---

### Post by Emil M on 2009-05-11
Thanks I'll take a look, but I've tried install -f with an error too..

(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `python-virtkey' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by BslBryan on 2009-05-11
Just keep us posted. :-)

If nothing works, try this from a terminal:
```
sudo dpkg --clear-avail; sudo apt-get update
```

Make sure Synaptic is not running when you do this, or you'll get an error about not being able to lock the administration directory.

Good luck! :-)

---

### Post by Emil M on 2009-05-11
> **BslBryan said:**
> Just keep us posted. :-)

If nothing works, try this from a terminal:
```
sudo dpkg --clear-avail; sudo apt-get update
```

Make sure Synaptic is not running when you do this, or you'll get an error about not being able to lock the administration directory.

Good luck! :-)
Tried that but still get's the error when executing install -f and Add/Remove says:

**Failed to check for installed and available applications**
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

