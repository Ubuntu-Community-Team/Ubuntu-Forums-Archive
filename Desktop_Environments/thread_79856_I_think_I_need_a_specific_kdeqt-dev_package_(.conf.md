---
title: "I think I need a specific kde/qt-dev package (./configure error)"
date: 2005-10-21
forum: Desktop Environments
---

### Post by digby on 2005-10-21
I'm trying to compile a window decoration, and I've installed more -dev packages than I can count at this point. I've also installed all the normal packages needed (build-essential, etc.). I keep getting errors when running ./configure, however. I managed to get through several of them by installing the aforementioned -dev packages, but I'm stuck and can't figure out what I need now.

The error is: in the prefix, you've chosen, are no KDE headers installed. This will fail.

---

### Post by GeneralZod on 2005-10-21
This is going to be tricky, as you don't say which ones you have installed.  Do you have 

kdelibs4-dev
kdebase-dev

installed?

---

### Post by digby on 2005-10-21
Ah... that did it - thanks.  And I didn't list what I had installed because I couldn't remember all of them.  Is there a way to view recently installed packages?

---

### Post by GeneralZod on 2005-10-21
[QUOTE=digby]Ah... that did it - thanks.  And I didn't list what I had installed because I couldn't remember all of them.  Is there a way to view recently installed packages?[/QUOTE]

You're welcome; one of these days I'm going to have to create a completely blank install and write a couple of HOWTO's for compiling KDE apps, as it seems to cause a lot of people consternation :)

You can list all currently installed packages using

```

sudo dpkg --list

```

but I don't believe they are date-stamped.  You might want to check /var to see if there are any dpkg logs.  

Does anyone know how to get a list of installed packages together with date of installation?

---

### Post by shakin on 2005-10-21
[QUOTE=GeneralZod]Does anyone know how to get a list of installed packages together with date of installation?[/QUOTE]

Synaptic has the File -> History window that lets you view installed and uninstalled packages by date. I'm not sure if it tracks changes made outside of Synaptic, though.

---

