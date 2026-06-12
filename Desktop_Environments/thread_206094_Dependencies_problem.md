---
title: "Dependencies problem"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Trelo on 2006-06-29
Hi all :)

I am having a dependencies problem when I try to install Listen.

First I updated my sources.list with *deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./*

Then apt-get update and apt-get install listen... but listen depends on python2.4-ctypes.

On synaptic, I tried then to install python2.4-ctypes, but it depends on libffi4, which depends on gcc-4.0-base, which is already installed.

How do I solve this mess?

Thanks!

---

### Post by Trelo on 2006-06-29
Bump.

---

### Post by ColinG on 2006-06-29
Strange, I downloaded the deb from the Listen site and installed it with the automatic installer and all was well - except that it does not recognise my Ipod 30 gig jobbie. Apart from that it looks excellent.

Back to Gtkpod for me

---

### Post by ayoli on 2006-06-29
[QUOTE=ColinG]Strange, I downloaded the deb from the Listen site and installed it with the automatic installer and all was well - except that it does not recognise my Ipod 30 gig jobbie. Apart from that it looks excellent.

Back to Gtkpod for me[/QUOTE]
maybe you need to install [that]("http://sourceforge.net/project/showfiles.php?group_id=161415&package_id=182276&release_id=404917") for ipod
regards

---

### Post by ColinG on 2006-06-29
It says I have a later version og Libgpod0 installed but libgpod-dev and python won't install as Lobgpod0 is not there :confused:

---

### Post by Trelo on 2006-07-10
Bump

---

### Post by Trelo on 2006-07-10
Anyone? :(  I'm having a hard time with Ubuntu and dependencies, not only in this case with Listen.  Many times I try to install something and I just can't.  Synaptic is supposed to be an easy system to install stuff in your computer, but it's not really useful when (at least for me) most of the times I can't because the file depends on x y z files that I can install either because themselves depend on r s t files which, again, I can't install.

I have the impression of having a mess on the OS when in reality I didn't install almost anything and I'm running an almost out of the box installation.

Could someone explain what's the deal with dependencies and what to do when I come across them?

Thanks in advance :)

---

### Post by lamego on 2006-07-10
Dependencie problems are only common when you use the non official ubuntu repositories. For such applications you should try to compile from the source instead.

---

