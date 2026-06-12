---
title: "Opera not loading..."
date: 2006-08-30
forum: Desktop Environments
---

### Post by Clark Nova on 2006-08-30
Whilst I was using Opera earlier on it stopped responding and I had to force close it. When I tried to load it again nothing happened at all so I clicked on the icon again. This time it told me that it was already running so I checked in System Monitor. Sure enough it was in there, so I ended it and tried again... still nothing appeared on the screen but the process showed up in System Monitor.

I uninstalled it using "sudo apt-get remove opera". I tried to reinstall it but it said it wasn't available in the repositories (or something similar, I forgot to write down the message). Then I remembered that I installed it using Automatix previously so I just fired that up and reinstalled it from there. Still didn't work and it just behaved as it did previously by showing the process as running but nothing appearing on the screen.

Can anybody help me with this? As nice as Firefox is I really prefer Opera and want to get it working again if I can](*,) 

Thanks in advance! :)

---

### Post by xtknight on 2006-08-30
What happens if you type opera from the terminal?  Any errors?  Maybe some errors about lesstif/motif?

---

### Post by Clark Nova on 2006-08-30
> **xtknight said:**
> What happens if you type opera from the terminal?  Any errors?  Maybe some errors about lesstif/motif?

This is what the terminal tells me:

> simon@simon-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.



---

### Post by xtknight on 2006-08-30
Maybe your user profile is corrupted.  Back it up and try to start opera with these commands.

**sudo killall opera**
**sudo mv ~/.opera ~/.opera.backup**
**opera**

---

### Post by Clark Nova on 2006-08-30
> **xtknight said:**
> Maybe your user profile is corrupted.  Back it up and try to start opera with these commands.

**sudo killall opera**
**sudo mv ~/.opera ~/.opera.backup**
**opera**

This is what I am getting:

> simon@simon-desktop:~$ sudo killall opera
opera: no process killed
simon@simon-desktop:~$ sudo mv ~/.opera ~/.opera.backup
simon@simon-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.


This time Opera has loaded so that's great news! Thanks! Any idea what those error messages mean?

---

### Post by xtknight on 2006-08-30
I get that a lot with Opera.  I think it's because those libraries are 64-bit and Opera is 32-bit so it can't load them.  They are Java components.  You can try obtaining the 32-bit version of them from a package called ia32-sun-java5-bin.

---

