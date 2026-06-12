---
title: "96dpi ?"
date: 2007-04-27
forum: Desktop Environments
---

### Post by x1a4 on 2007-04-27
Hi,

How do I configure X to display fonts at 96dpi?  

I'm using a 15" (diagonal) LCD screen at a resolution of 1024x768.  

I set **DisplaySize** in _xorg.conf_ to **271 203** but I only get 86x84dpi

Thank you.

---

### Post by Pox on 2007-04-27
Try 243x178... not sure, but that _should_ give you 96dpi.

---

### Post by falt004 on 2007-04-28
I'm having a similar problem actually - I'm unable to set the DPI to 96. Added a line under Monitor to xorg.conf

DisplaySize     329.2 272.3

which matches the specs of my laptop's LCD monitor, however regardless of that value (tried tweaking around with it), I *still* have a dpi of 86x84 (according to xdpyinfo)...

Any ideas?

Cheers,
/Fuad

---

### Post by Iokua on 2007-05-01
> **falt004 said:**
> I'm having a similar problem actually - I'm unable to set the DPI to 96. Added a line under Monitor to xorg.conf

DisplaySize     329.2 272.3

which matches the specs of my laptop's LCD monitor, however regardless of that value (tried tweaking around with it), I *still* have a dpi of 86x84 (according to xdpyinfo)...

Any ideas?

Cheers,
/Fuad


I'm having the same problem. Is X just misreporting the DPI or is there something I'm missing?

---

### Post by RedSquirrel on 2007-05-01
I'm having the same problem.

My DisplaySize line in xorg.conf used to work fine with edgy, but with feisty I can't get it to work. This is on feisty server with xorg installed on top.

Running:
```
xdpyinfo | grep resolution
```
reports:

**resolution:    85x86 dots per inch**

And I know the DPI is wrong because it *looks* wrong.

---

### Post by RedSquirrel on 2007-05-01
Well, I fixed mine for the time being by creating the file ~/.Xresources and adding:

```
Xft.dpi: 96
```Seems OK. Perhaps the *DisplaySize* setting in xorg.conf is not supported anymore.

---

