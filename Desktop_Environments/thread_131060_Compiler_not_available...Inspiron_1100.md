---
title: "Compiler not available...Inspiron 1100"
date: 2006-02-15
forum: Desktop Environments
---

### Post by racsw on 2006-02-15
Hi,
  Due to Umbutu not having the correct video driver for the Inspiron 1100, I downloaded the driver from Intel. (actually a Sourceforge project)
When I try to install (as root), I get "Compiler not available to compile modules".
What do I need to do to get this to function correctly?

Thanks,
Robert

---

### Post by shams2 on 2006-02-15
do:
apt-get install build-essential

---

### Post by racsw on 2006-02-15
Well, we made some progress, thanks to you.
Here the message:
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory. Stop

Then I get a "Cannot find a kernel config file".

I don't know.  I know there's an 845patch, with SuSe 9.0 instructions, but I'm not sure how things are layed out in the Umbutu system structure.

What a pain this is trying to do this with a miniature 7"x6" screen...

Thanks,
Robert

---

### Post by shams2 on 2006-02-15
do:
apt-get install kernel-headers
if that doesn't work do:
apt-get install linux-headers

---

### Post by racsw on 2006-02-15
Boy, this is like pulling teeth...
The last command worked, and it went farther, but now..

It keeps looking for gcc-3.4, giving out "Command not found".

If at some point, like now, you want to give up on this, let me know.  It wasn't my intent to drag you into all this.

Thanks,
Robert

---

### Post by RAOF on 2006-02-15
You can install gcc-3.4 with
```
sudo apt-get install gcc-3.4
```
You need it (and not the default 4.0 which is installed with build-essentail) because the Breezy kernel was built with gcc-3.4

---

### Post by racsw on 2006-02-15
I'm doing this now, and I'm an x-Suse person, who feels handicapped without Emacs for terminal editing.  Can I use this apt-get for this?  I looked under available programs, but it wasn't listed.  I hate switching back and forth to use a gui gedit.

Thanks,
Robert

---

### Post by racsw on 2006-02-15
That didn't work.  Apparently, the iso image I downloaded to CDROM was not a Breezy Badger version.  bummer...
Will apt-get go and find this online?

Robert

---

### Post by RAOF on 2006-02-15
Yeah, emacs should be perfectly available.  For the console junky in you, "aptitude" is a one-stop shop for your apt-get type needs.

"aptitude search emacs" spits out a whole list of emacs packages.  I suggest emacs-snapshot-gtk, for an emacs with nice GTK widgets.

On the terminal, emacs -nw will give you a terminal-based emacs.

---

### Post by racsw on 2006-02-15
Nope, I was wrong.  It was the latest Breezy Badger 5.10, I double-checked.
It can't find it on the CDROM, though.

---

### Post by engla on 2006-02-15
The emacs version available from the repositories is called 'emacs21'; get it with aptitude/apt-get/synaptic

---

