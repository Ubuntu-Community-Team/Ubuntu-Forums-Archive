---
title: "How would I recompile Nautilus to test a change I make?"
date: 2009-01-24
forum: Desktop Environments
---

### Post by sproaty on 2009-01-24
I basically want to hook up middle mouse click on a tab -> close tab.
I figured, there's code in there for left clicking a tab to change to that tab, so it should be a fairly trivial edit to hook up what I want (close tab code exists, detect mouse click within tab "regions" code exists - just need to link them)

so, I downloaded the source, pretty sure I found where the change would go, but then I realised I'd have no idea how to compile it..

any ideas? I don't know if ubuntu has anything specific compilation flags for it or whatever

---

### Post by ajmorris on 2009-01-25
hi there,
make sure you uninstall the nautilus from the ubuntu repos first, then do the following:
```
sudo apt-get install build-essential
``` (the build-essentail package, is a meta package that pulls down all tool required to compile, such as the default C compiler, GNU C Compiler, (gcc).
then to compile, run:
```
./configure
```(this configures the Makefile according to the default options that the source developer has set, and to what options you pass on the ./configure stage)
```
make
```(makes the source from the Makefile)
```
sudo make install
```(installs the compiled source)

AJ

---

### Post by sproaty on 2009-01-26
awesome, I thought there would have been certains flags to set for Ubuntu or something. Do I just add nautilus to my session list then?

---

### Post by ajmorris on 2009-01-29
> **sproaty said:**
> awesome, I thought there would have been certains flags to set for Ubuntu or something. Do I just add nautilus to my session list then?

theoretically, no. As your gnome session should still be configured to use nautilus.

AJ

---

