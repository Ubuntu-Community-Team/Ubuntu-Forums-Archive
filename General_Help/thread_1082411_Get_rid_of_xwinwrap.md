---
title: "Get rid of xwinwrap"
date: 2009-02-27
forum: General Help
---

### Post by steigerjb on 2009-02-27
Please help me. I installed xwinwrap but I can't get it work so I want to get rid of it. I don't know how. I don't like not having desktop icons.

---

### Post by yeats on 2009-02-27
What steps did you take to install it?  If it was the typical ./configure, make, sudo make install method you should be able to cd into the installation directory and do:

```
sudo make uninstall
```

---

### Post by steigerjb on 2009-02-28
I did:

sudo apt-get install xwinwrap

sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs

cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cd xwinwrap
make
sudo cp xwinwrap /usr/bin



so how do i uninstall? I'm lost

---

### Post by yeats on 2009-03-05
> **steigerjb said:**
> I did:

sudo apt-get install xwinwrap

sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs

cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cd xwinwrap
make
sudo cp xwinwrap /usr/bin



so how do i uninstall? I'm lost

okay - so you installed it using apt-get and then installed it from source?  That would probably explain why nothing's working.  Were you following instructions from somewhere?

Okay - try this:

```
sudo apt-get remove xwinwrap
```

which should remove what you installed from the repositories.  Then report back.

---

