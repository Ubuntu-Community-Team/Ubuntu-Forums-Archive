---
title: "quake 2 in 8.04"
date: 2008-04-26
forum: Gaming &amp; Leisure
---

### Post by nutpants on 2008-04-26
yes im mostly a linux noob

and yes i have RTFM

but i have this error trying to get quake 2 to go in my frest install of Ubuntu 8.04

 quake2
/usr/local/bin/quake2: 50: Bad substitution
dirname: missing operand
Try `dirname --help' for more information.
Error loading new keyboard description
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.300, Green  1.300, Blue  1.300
/usr/local/bin/quake2: 64: ./sdlquake2: not found
-> Red  1.300, Green  1.300, Blue  1.300
<- Red  1.000, Green  1.000, Blue  1.000


after i had the error  
Uncompressing Quake II 3.21+r0.16.1 Installer.....................................................................

Gdk-WARNING **: locale not supported by C library

that i fixed (i think) with help from this page..

[http://ubuntuforums.org/showthread.php?t=325102&highlight=locale+error](http://ubuntuforums.org/showthread.php?t=325102&highlight=locale+error)

but i cannot find anything to get me past the new error..

any help or pointers to a new build of quake 2 for linux

nutz

---

### Post by rajeev1204 on 2008-04-27
did u try the quake 2 installer from synaptic?

---

### Post by eragon100 on 2008-04-27
how do you use that installer, typing in quake2-data in the terminal doesn't do anything, and this is also strange:

eragon@Asgard:~$ q
qpdldecode      quote           quote_readline  
eragon@Asgard:~$ q

I pressed tab to see all  known command starting with q, which was the first letter of quake the last time I checked :lolflag:

:confused:

---

### Post by nutpants on 2008-04-27
> **rajeev1204 said:**
> did u try the quake 2 installer from synaptic?

yes..
all i got from that was the data files of my cd into ubuntu..

nothing to run ..
ie..

no executable  quake2.


so i tired the installer from here
[http://www.liflg.org/?catid=6&gameid=55](http://www.liflg.org/?catid=6&gameid=55)


its been year but i want to play quake 2 to the finish again..

nutz

---

### Post by rajeev1204 on 2008-04-28
ok u r right.

I just checked and there is no installer for quake 2. Hmm it was there in feisty.


Maybe use the feisty installer package from website ? 

[http://packages.ubuntu.com/feisty/quake2](http://packages.ubuntu.com/feisty/quake2)



Ok i have quake 2 so iam gonna install and try.


Will let u know.

---

### Post by eragon100 on 2008-04-28
Simply install the windows version from the cd with wine. It works perfectly without any modification or tricks required :)

---

### Post by nutpants on 2008-04-28
> **rajeev1204 said:**
> ok u r right.

I just checked and there is no installer for quake 2. Hmm it was there in feisty.


Maybe use the feisty installer package from website ? 

[http://packages.ubuntu.com/feisty/quake2](http://packages.ubuntu.com/feisty/quake2)



Ok i have quake 2 so iam gonna install and try.


Will let u know.

thanks for a point in the right direction...
now it runs, all i need now is sound
------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.

got it.. to fix sound start quake2 
quake2.real +set snddriver ao +set snddevice oss

nutz..

---

### Post by PrimoTurbo on 2008-04-28
I highly suggest to use wine to run Quake2, it runs very well. The linux versions of Quake2 are all buggy and have so many problems related to sound and video, etc. With wine you are able to run nocheat.exe and many other Quake2 engines.

---

### Post by nutpants on 2008-04-28
> **PrimoTurbo said:**
> I highly suggest to use wine to run Quake2, it runs very well. The linux versions of Quake2 are all buggy and have so many problems related to sound and video, etc. With wine you are able to run nocheat.exe and many other Quake2 engines.

thats what i heard about windows, but i prefer to run it natively
so far now its working it seems fine.


nutz

---

