---
title: "How do I install build-essentials in Breezy?"
date: 2005-10-15
forum: Desktop Environments
---

### Post by mostwanted on 2005-10-15
I need make and what ever else there might be, but I don't feel like tracking each package down individually.

EDIT: Hm... could it be just build-essential...?

---

### Post by GeneralZod on 2005-10-15
[QUOTE=mostwanted]
EDIT: Hm... could it be just build-essential...?[/QUOTE]

Yep :)

---

### Post by Manny C on 2005-10-15
Not necessarily. 

I have found some applications need x, kde and or qt libraries to build properly. However, I can't remember exactly which ones.

Build-essential package is good as it includes heaps of stuff, but not everything.

---

### Post by az on 2005-10-15
[QUOTE=Manny C]Not necessarily. 

I have found some applications need x, kde and or qt libraries to build properly. However, I can't remember exactly which ones.

Build-essential package is good as it includes heaps of stuff, but not everything.[/QUOTE]


Then you install whatever -dev ackages you need.  If it is for kde, then you need the kdelibs-dev packages,  X will be xlib-dev, ncurses will be libncurses5-dev.... etc....

You need to look in the readme in the tarball to see what library depandancies you need to install.  To install *all* the developental packages would take up way to much hard disk space.  That is why build-essential is just the essential bits.

---

### Post by fishfork on 2005-10-15
If there's an older version of the package you're compiling in the repo's, you can try
```
sudo apt-get build-dep package_name
```
which should pull in most / all of what you need.

---

