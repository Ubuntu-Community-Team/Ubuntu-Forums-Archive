---
title: "Can't read Ubuntu partition from Windows since upgrade to 8.10"
date: 2009-03-02
forum: General Help
---

### Post by nandotron on 2009-03-02
Hi,

I've had a look around but can't find an answer to this question.  In the previous versions of ubuntu I had used ext2IFS to be able to read and write to the ubuntu partition of my dual boot system from windows.

With Intrepid and the updating of the filesystem, no dice.  Is there a driver available that will do this for me?

Thanks,
Nando

---

### Post by bluelamp999 on 2009-03-02
Hi there,

This worked for me [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)

Good luck

---

### Post by nandotron on 2009-03-02
hey, thanks for getting back to me.  yeah i tried that too, but right after i install it and try to access the ubuntu partition, Windows asks if i want to format the partition...

---

### Post by Rallg on 2009-03-02
Hmm, the program worked for me. But I didn't upgrade to 8.10, I had 8.10 installed first, before I added ext2fsd. Maybe the ext2fsd is storing some information that has changed, in the Windows registry?

Try complete uninstall of ext2fsd from Windows. Then, if you are confident in using the Windows registry editor with the usual warnings, see if anything is stored (it would probably be in a System Internals folder). Also, in your Documents and Settings, make hidden files visible, and delete any folder that is storing settings for the ext2fsd program. Then, re-install the program.

---

### Post by nandotron on 2009-03-03
hey thanks a lot, i uninstalled and then re-installed and it works a charm.

---

