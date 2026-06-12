---
title: "Enabling floppy drive B?"
date: 2006-10-10
forum: Desktop Environments
---

### Post by wkulecz on 2006-10-10
I need legacy floppy support.  Floppy A: (1.44MB) works as expected as fd0, but floppy B: (1.2MB 5") doesn't.

I created an fd1 entry in /etc/fstab but it doesn't work since /dev/fd0 exists but /dev/fd1 does not!

I haven't a clue as to what majic numbers to feed to mknod to create it and am not ever sure that is the propper way to do it any more on "modern" linux systems.

Automagic is great when it works but leaves one toally lost when it doesn't!

I do see a Floppy 2 entry on the tree view "Places" in Nautilus if I open a "Computer" file browser.  I've no idea where it came from.

--wally.

---

### Post by Jussi Kukkonen on 2006-10-10
The device will quite probably be something else than */dev/fd1*, like */dev/fd1h1200*. Not sure if that'll help though.

---

### Post by wkulecz on 2006-10-10
It might help if there were any entries in /dev for other than fd0.

--wally.

---

### Post by wkulecz on 2006-10-11
If I put the 1.2MB floppy as A: and set the BIOS to 1.2MB floppy the kernel detects it as 1.2MB but Nautilus won't mount it. 

However mtools does read it fine,  The 1.44MB on B: is now inaccessable via both mtools and Nautilus.

If I swap the cable (so B: becomes A:) Nautilus can now mount the 1.44 floppy on A: but B: is still inaccessible by either method.

Mtools is all I really need, I think I just need the magic numbers for mknod to create /dev/fd1

--wally.

---

### Post by Jasper Houtman on 2008-04-30
There is no fd1 in /dev, does anyone know how to create it?

---

### Post by Jasper Houtman on 2008-04-30
*bump* anyone? how do i add an additional drive (floppy) to hardy? And why is fd1 removed from hardy. I still use and need two floppy drives. Did it really take up that much space that it had to be removed?

---

### Post by wkulecz on 2008-06-03
Double bump.  While I rarely use floppies any more, the ability to recover old data on 3.5 and 5" floppies still occasionally makes me a hero, as long as my floppy drives still work, I'd like to maintain the ability to use both.

--wally.

---

