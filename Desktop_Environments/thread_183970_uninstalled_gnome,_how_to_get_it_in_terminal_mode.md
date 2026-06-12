---
title: "uninstalled gnome, how to get it in terminal mode"
date: 2006-05-29
forum: Desktop Environments
---

### Post by villem123 on 2006-05-29
hi people, 

funny thing I succeeded to do. Using edubuntu, I installed kde some time ago and enjoyed it a bit more than gnome (problems with proper keyboard installation, etc.).  So my simple mind decided to get some free space in system and uninstall gnome. Not really thinking and reading during that time, I indeed did it and now the graph. interface for logging is gone. 

As I'm rather new in Linux and interested to learn it more, then I prefer if someone could tell me the hard way to fix the problem (reinstallation of ubuntu is proven already for several times and seems I'm "smart" enough to manage with this). But if there is any way to get gnome and install it w.o. graphical environment. My default network connection is set to DSL, but it would be useful and helpful if someone could explain how to set up wireless (eth0) in terminal mode. 

Hope on your understanding and nice replies.

---

### Post by mcduck on 2006-05-29
To get gnome back, just run 'sudo apt-get install ubuntu-desktop'. Or perhaps edubuntu-desktop, if there is such a package..

---

### Post by timfrost on 2006-05-29
sudo apt-get install ubuntu-desktop

This will pick up gdm (the display manager) and all the gnome packages

---

### Post by mrazster on 2006-05-29
I'm not sure about the wireless usage in CLI...but I suspect it should work.

As for the gnome installation, in CLI (command) just do:
```
sudo apt-get install ubuntu-desktop
```

Restart your machine or just logout...in the loginmanager choose Gnome for your session and you're all set.

---

### Post by villem123 on 2006-05-29
thanks for the advices. In synaptic I'marked complete removal - :-), I'm no sure whether apt-get will help me.

BR,

---

### Post by mcduck on 2006-05-29
[QUOTE=villem123]thanks for the advices. In synaptic I'marked complete removal - :-), I'm no sure whether apt-get will help me.

BR,[/QUOTE]
Sure it will, even 'Complete removal' doesn't remove it from Ubuntu servers ;)

---

### Post by n00bWillingToLearn on 2006-05-29
[QUOTE=villem123]thanks for the advices. In synaptic I'marked complete removal - :-), I'm no sure whether apt-get will help me.

BR,[/QUOTE]

I believe all that "complete removal" does is simply delete configuration files as well as uninstalling the packages so apt-get should still work. FYI you can also just install the Gnome Desktop Manager ( graphical login ) or the KDE equivilent if you still don't want gnome but want to be able to log into KDE ( Gnome is not required to use KDE)

---

### Post by villem123 on 2006-05-29
Thank you all, I will do it.

BR,

---

