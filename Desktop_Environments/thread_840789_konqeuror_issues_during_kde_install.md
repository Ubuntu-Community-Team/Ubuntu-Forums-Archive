---
title: "konqeuror issues during kde install"
date: 2008-06-25
forum: Desktop Environments
---

### Post by dan93z28 on 2008-06-25
I have been having some issues while installing kde.  I have installed it in the past, but i removed it to save space. now that i have more space i would like to install it again.  I have been trying to install it via synaptic, but every time it comes with an error involving konqueror.

```
E: /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.2_i386.deb: trying to overwrite `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', which is also in package kio-umountwrapper
```

Afterwards, kde runs. but is unstable. the first time i installed kde i didnt use synaptic, and had some problems removing it. one involved "kio-unmountwrapper" but it appeared to resolve itself during an update.

i am running hardy on an HP dv6000 laptop. with intel processor and graphics card.

Any suggestions greatly appreciated.

---

### Post by dan93z28 on 2008-06-25
apparently its a bug. i think i may have solved my problem with the help given here.

[https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729)

---

