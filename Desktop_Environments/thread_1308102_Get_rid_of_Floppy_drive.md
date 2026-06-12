---
title: "Get rid of Floppy drive"
date: 2009-10-31
forum: Desktop Environments
---

### Post by s.dalas on 2009-10-31
Hi all,
i installed 9.10 without any problems (in fresh install, couldn't upgrade).
My problem is..
While i don't have a floppy disk it shows up a floppy under Places and Computer. 
How can i get rid of this??

---

### Post by braete on 2009-10-31
disable floppy from the bios

---

### Post by s.dalas on 2009-10-31
this is not solves the problem.
just changed the name of "Floppy" to "floppy0"...

thanks anyway

---

### Post by sillyfofilly on 2009-11-01
I'm seeing this, too.

I disabled the floppy in the BIOS, and it doesn't show up anymore in System->Administration->Disk Utility, but when I open the Places menu, it still shows "floppy0"

EDIT: I just found this thread: [http://ubuntuforums.org/showthread.php?t=591420]("http://ubuntuforums.org/showthread.php?t=591420") and it fixed it for me

---

### Post by s.dalas on 2009-11-01
i see this but this is not working for me... 
how exactly have you comment on the line?

I have to disable it from bios too??

---

### Post by s.dalas on 2009-11-01
ok. i was commenting in fstab but it was still there cause i had it on in bios. 

So disable it from bios and commenting in the floppy line in etc/fstab solves it.
As it shows here [http://ubuntuforums.org/showthread.php?t=591420]("http://ubuntuforums.org/showthread.php?t=591420")

THANKS!

---

