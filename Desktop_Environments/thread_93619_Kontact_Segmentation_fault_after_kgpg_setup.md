---
title: "Kontact Segmentation fault after kgpg setup"
date: 2005-11-22
forum: Desktop Environments
---

### Post by lorenco on 2005-11-22
I configured encryption / signing of my mail via kGpg now I get Segmentaion Fault:

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1240213280 (LWP 21705)]
0xb66dca70 in ?? () from /usr/lib/libkabc.so.1 

The above I get if i do "gdb kontact"  I get that for starting all kmail / korganizer / or kgpg... HELP!!!!:confused: :confused: :confused: :confused: 

To test this I mail a signed / encryted mail to myself... I have even tried to mv my .kde/apps/shared/kmail .... and various others to .old but it still fails ... HELP!

I need to get my mail ....

---

### Post by lorenco on 2005-11-22
This seems not have something to do with kgpg ???

I created a complete new home/myname and started KDE again...

It Still fails even with vinilla KDE startup (no GPG or Mail in kmail folder ... ):confused: :confused:

Might have updated something ??

---

### Post by lorenco on 2005-11-23
Hmmm...

I updated the kernel to 2.6.12-10-686... and t now works... Twiddled a lot but now working...

---

