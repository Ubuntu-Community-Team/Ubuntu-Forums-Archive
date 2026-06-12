---
title: "a few compiz &quot;stumpers&quot;"
date: 2009-03-11
forum: Desktop Environments
---

### Post by frogotronic on 2009-03-11
Hello,

I must be retarded bcs I cannot get XGL to install with FGLRX on the same computer and have actual compiz working.

I have Hardy 8.04.2 and an ATI x2300 Mobility Radeon card.

ATI FGLRX Catalyst 9.1 driver is install and works perfectly.

When I choose COMPIZ as window manager, I cannot use "Direct Rendering" - that option is greyed out.  Running compiz --version gives the following:

```
$ compiz --version
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7188 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.6
```

Here's my question, how do I get XGL installed?  If I add it via the Synaptic repos (xserver-xgl) I can't use compiz at all - the entire X server turns to garbled goo...

This one has me beat.  Any suggestions welcomed...

- CH    :popcorn:

---

