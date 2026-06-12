---
title: "Moving Programs and Files to a New System"
date: 2007-08-10
forum: Desktop Environments
---

### Post by eeefresh on 2007-08-10
I have Ubuntu set up exactly how I want it on my desktop.  Now I want to install it on my laptop, as well.  I remember reading somewhere (can't remember where)  that you can back up all the packages on a CD/DVD to transfer to other computers. Does anyone know how to do this?  Also, is it just the packages, or can other settings (themes, program settings, etc.) be transferred?

---

### Post by merlinus on 2007-08-10
Configurations, settings, and preferences are in /home.  Make sure Show Hidden Files is activated.

Not certain about migrating everything else due to differing hardware.

-merlin

---

### Post by eeefresh on 2007-08-10
Backing up the home folder seems simple enough, but how can I move the actual programs (Google Earth, Amarok, etc.) over without having to download all of them again?

---

### Post by merlinus on 2007-08-10
Since many apps place various files in different directories/folders, I believe you will need to install them again.

The install packages may still be on your computer in /var/cache (or somewhere else), but someone more knowledgeable will hopefully chime in about this.

-merlin

---

### Post by eeefresh on 2007-08-14
Bump

---

### Post by djwohls on 2007-08-15
have you tried  APT-on-CD?  I believe that is what it is called.  I believe it is in synaptic...

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")


I believe that you would still have to copy the home folder to keep your settings and configurations

---

### Post by kellemes on 2007-08-15
> **eeefresh said:**
> (..) is it just the packages, or can other settings (themes, program settings, etc.) be transferred?

Only settings etc.. not the packages.

---

