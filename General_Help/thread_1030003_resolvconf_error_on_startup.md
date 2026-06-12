---
title: "resolvconf error on startup"
date: 2009-01-04
forum: General Help
---

### Post by zorkerz on 2009-01-04
When my computer starts up the Ubuntu loading screen goes away and instead shows all the things its doing to startup in white letters on a black background (im not sure what this detailed view is called). Each startup I see this error.

> rm:cannot remove '/etc/resolveconf/run/interface/*' : read-only file system '/etc/rcS.d/S07resolveconf: 116 : cannot create /etc/resolveconf/run/enable-update read-only file system

I have tried to copy the error exactly but it only appears for a few seconds each startup. Is there a log file that would record it?

Is resolvconf installed by default or did I install it with something?

This does not appear to cause any problems besides switching startup from the ubuntu loading screen to the detailed view. I would however like to fix it.

---

### Post by dcstar on 2009-01-04
> **zorkerz said:**
> When my computer starts up the Ubuntu loading screen goes away and instead shows all the things its doing to startup in white letters on a black background (im not sure what this detailed view is called). Each startup I see this error.
........

Firstly, please do NOT quote blocks of data, use the "Code" function.

Secondly, if the Read-only filesystem message appears it means that your root filesystem is being mounted as R/O, and you probably need to do a fsck on it to fix it.

Boot off a Live CD and use the Partition Manager to fix your hard disk's root filesystem.

---

### Post by Mr Fredrick on 2009-02-26
I also have this error message on start-up including the line about "read-only file system".

Is it necessary that I run fsck to fix it, I don't have a LiveCD, so is it possible to do so without one. Also would reinstalling resolvconf help with this problem.

Thanks in advance;

MrFred.

I figured out how to force fsck on startup with:

sudo touch /forcefsck

It didn't seem to report any problems (although I couldn't read what it said as it continued the remainder of the boot sequence so quickly) But I still get exactly the same message in start-up.

---

### Post by zorkerz on 2009-02-27
Hmm somehow I missed you post dcstar. I currently don't have my computer but when I get it back I will be sure to look into this again. Also my apologies for the quoting but it seemed ambiguous to me. I was quoting an error message it was not any sort of code  that I had typed.

Is the distinction that you prefer to have anything written by a person in quote tags and anything written by the computer or written to be executed in the code tags?

Mr Fredric I hope we can figure this out.

---

