---
title: "dell dw1350 mini pci wireless card not detected"
date: 2009-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rls53 on 2009-05-31
New B ?? Installed most recent Ver. Ubuntu on Dell 100L all is well except no detection of DW1350 wireless mini card. Is it advisable to install 3rd party driver or am I missing something here within Ubuntu drivers?
Virgin install of Ubuntu on new HDrive from Ubuntu disk.

---

### Post by coffeeaddict22 on 2009-05-31
Hi,
Find a terminal, type in the three following commands.  They give you (and us!) somewhere concrete to start with when troubleshooting.  Hope you don't mind the terminal; it's a lot easier to troubleshoot in because there's more control over what goes in and it's more explicit about what comes out.
```
lshw -C network
iwconfig
uname -a
```
if you want to know a bit more about them, type in ```
man xxxx
``` where xxxx is the name of the command you're interested in.
Post the results back if you need some more help.

---

