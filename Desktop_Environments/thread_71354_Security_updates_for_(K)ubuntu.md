---
title: "Security updates for (K)ubuntu?"
date: 2005-10-03
forum: Desktop Environments
---

### Post by linuxa on 2005-10-03
Hi all

To some this might sound like a n00b question. :p 

But having come from a Windows background, the weekly Windows Update has become all too much of a habit. :rolleyes: 

Despite Linux having a much more secure track record. Are there any security updates that I should be installing (perhaps on a regular basis) for Kubuntu 5.04?

If so, what do I have to do to install them?

Thanks in advance

---

### Post by Hobbsee on 2005-10-03
Ubuntu has an update notifier, as part of gnome, but KDE for the moment, does not.  

Probably one of the easiest ways to update your system is to follow this guide: 
[http://ubuntuguide.org/#manualupdate](http://ubuntuguide.org/#manualupdate)
After running that, your system is completely updated...

---

### Post by linuxa on 2005-10-06
Hey **Hobbsee**, thanks for the reply. The command
*sudo apt-get upgrad*

at the link you included seem to upgrade ALL packages. 

Is there any way to only update/upgrade for **security** purposes?

e.g. akin to Window Update, which only patches the core system for security holes. Or are there no security holes in Ubuntu?
:D

---

### Post by weblars on 2005-10-06
Well, 
```
sudo apt-get update 
sudo apt-get upgrade
``` 
downloads and installs all packages that have been modified. Between two releases of Ubuntu/Kubuntu, i.e. Hoary and Breezy,  mainly (exclusively?) security fixes will be published. 
I don't know if there is a way to just download a patch instead of the whole package. But I guess that you would have to patch the sourcecode and recompile it. 
So, the easiest way to maintain a secure system is using the update notifier (Gnome) or 
```
sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by linuxa on 2005-10-13
Thanks, I simply wasn't aware that between major release, bug fixes would be published at the same source.

I figured there was some separate mechanism for updating security patches.

This does make a lot easier though.

Cheers.

---

