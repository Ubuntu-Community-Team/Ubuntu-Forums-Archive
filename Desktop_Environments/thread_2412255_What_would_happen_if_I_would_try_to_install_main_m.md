---
title: "What would happen if I would try to install main metapackages for ALL Ubuntu flavours"
date: 2019-02-10
forum: Desktop Environments
---

### Post by raphaell2 on 2019-02-10
This is an admittedly kinda silly question, and I hope it hasn't been asked and answered before, but...

What would happen, theoretically, if I would try to install the main desktop metapackages for all Ubuntu flavours at once? Probably nothing *good*, I guess. They probably contain mutually exclusive software, and if the different window managers or login screen managers would try to start at the same time, it might destroy the whole system, or at least none of them would manage to run properly. 

Does anyone have a more informed take on this than mine?

---

### Post by ajgreeny on 2019-02-10
You would end up with a rather bloated system with many duplicated applications such as file-managers, text editors, terminal-emulators, etc, etc.

The system will still (probably) run but the menus (on those DEs that use a menu)  will certainly be full of a variety of applications that you may never use.
One way to deal with this need to check the different DEs is perhaps to use separate partitions of about 20GB and install new OSs of Xubuntu, Kubuntu, Ubuntu-MATE, etc etc, and then create soft links to the data folders in your main (first) OS installed, ie, what you have at present.

If your computer is powerful enough you might consider looking at all the different versions of the *buntu family as virtual installs using, for example, virtualbox; this is how I review new versions and the various DEs available, leaving my main installation of Xubuntu untouched.

---

### Post by crip720 on 2019-02-10
If you want to try, look for AIO linux, used to be AIO ubuntu.  It has all the desktops on one ISO you log out of one and in to another.  If we try to do this it usually at best is messy.

---

### Post by raphaell2 on 2019-02-11
Ah, thank you, good to know.

---

### Post by albone3000 on 2019-02-11
Ive done this recently and it works fine. Yes you will have some duplicate programs.

---

### Post by raphaell2 on 2019-02-11
> **albone3000 said:**
> Ive done this recently and it works fine. Yes you will have some duplicate programs.

Thank you, good to know. Though, to be honest, I'm a bit surprised to hear that. Shouldn't the various desktop environments' software packages for doing things that, by their very nature, can only be done in one way at a time, get in each others' way somehow?

---

### Post by deadflowr on 2019-02-11
Only parts that can only be run one at a time are usually the X/window management parts. 
So you cannot run plasma's kwin and unity's compiz at the same time.
But you shouldn't have a problem running all the programs like terminals and text editors and file managers at the same time.
(Or music players or video players or what have you.)

For me a bigger issue is theme inconsistency.
Some DEs programs might look great with one theme and the same theme can look like total garbage with another DEs programs.

---

