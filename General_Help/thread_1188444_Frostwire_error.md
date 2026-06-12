---
title: "Frostwire error?"
date: 2009-06-15
forum: General Help
---

### Post by nolliecrooked on 2009-06-15
anyone have any idea what may be causing this?

---

### Post by nolliecrooked on 2009-06-15
bump

---

### Post by bichopro on 2009-06-15
try to delete the folder .frostwire4.18 in your home...
this folder is hidden and sorry my bad English

---

### Post by nolliecrooked on 2009-06-16
> **bichopro said:**
> try to delete the folder .frostwire4.18 in your home...
this folder is hidden and sorry my bad English

I tried but nothing, its still giving the same error. thanks anyway.

---

### Post by nolliecrooked on 2009-06-16
ok Ive tried re-installing Frostwire like 1000000000000000 times.

everything else that requires java works,  so do I need to completely purge everything  Javanised(?) and re-install?

---

### Post by TrakerJon on 2009-06-16
It's a glitch, there is an known issue that causes the program to fail when using the Ubuntu GDebi Package Installer. The latest release of FrostWire requires that you install it from a terminal window **sudo dpkg -i frostwire-4.18.0.i586.deb** (the knot heads that programmed it have been notified). Note that it installs as the root user, when it launches shut it down and relaunch as the current user (Applications > Internet > FrostWire) and it should allow you complete functionality from there.

---

### Post by nolliecrooked on 2009-06-16
> **TrakerJon said:**
> It's a glitch, there is an known issue that causes the program to fail when using the Ubuntu GDebi Package Installer. The latest release of FrostWire requires that you install it from a terminal window **sudo dpkg -i frostwire-4.18.0.i586.deb** (the knot heads that programmed it have been notified). Note that it installs as the root user, when it launches shut it down and relaunch as the current user (Applications > Internet > FrostWire) and it should allow you complete functionality from there.

lol@knotheads

thanks for the info bro.

---

### Post by bobby159 on 2009-06-25
thanks!! worked like a charm! really appreciate it, keep up the help and good work

---

### Post by giggy on 2009-07-18
had the same problem followed TrakerJon instructions and it worked thanks 
trakerjon

---

