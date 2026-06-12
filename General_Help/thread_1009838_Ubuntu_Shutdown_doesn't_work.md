---
title: "Ubuntu Shutdown doesn't work"
date: 2008-12-13
forum: General Help
---

### Post by hoboy on 2008-12-13
I have vista-ubuntu8.10 dual booting the problem is that I can't shutdown the computer from ubuntu-when I click on user/shutdown instead for the computer to shutdown totally it goes back to the dual booting--then I have to waite for window to start then I can shutdown the computer. 
I have installed ubuntu via wubi.

---

### Post by Jammanuser on 2008-12-13
> **hoboy said:**
> I have vista-ubuntu8.10 dual booting the problem is that I can't shutdown the computer from ubuntu-when I click on user/shutdown instead for the computer to shutdown totally it goes back to the dual booting--then I have to waite for window to start then I can shutdown the computer. 
I have installed ubuntu via wubi.

hmm...sounds like a weird problem! ;) Good luck with getting it fixed! ):P

Cheers! :popcorn:

Jam Man

:guitar:

---

### Post by solwic on 2008-12-14
> **hoboy said:**
> I have vista-ubuntu8.10 dual booting the problem is that I can't shutdown the computer from ubuntu-when I click on user/shutdown instead for the computer to shutdown totally it goes back to the dual booting--then I have to waite for window to start then I can shutdown the computer. 
I have installed ubuntu via wubi.

I've heard about lots of problems using Wubi with Vista.  

I'm not sure what's causing your problem...but my suggestion (helpful as it probably *isn't*) is to wipe the Wubi install and go with a traditional dual-boot (unless you're willing to take the plunge and go full Ubuntu :P).  

Best of luck!

---

### Post by Asgar on 2008-12-14
This happened to me a few times, pulling the power cable out fixed the problem

---

### Post by Jammanuser on 2008-12-14
> **Asgar said:**
> This happened to me a few times, pulling the power cable out fixed the problem

I hope u meant pulling it out while the computer was OFF! :D Pulling the power cord out of the socket while its still ON will most likely result in having a UNRECOVERABLE "crc error" while attempting to boot into the Wubi install! and that is something i can tell u right now u most **certainly ** do not want! ;) I had a "crc error" before, making my Wubi install effectively unbootable, and the only fix i found was simply **reinstall** Wubi, keeping the old root.disk, and then later replacing the new one with the old, so i would still have all my files and programs!

So just FYI...don't pull out the power cord while its still on! :p

Jam Man

:guitar:

---

### Post by ago on 2008-12-15
> **hoboy said:**
> I have vista-ubuntu8.10 dual booting the problem is that I can't shutdown the computer from ubuntu-when I click on user/shutdown instead for the computer to shutdown totally it goes back to the dual booting--then I have to waite for window to start then I can shutdown the computer. 
I have installed ubuntu via wubi.

Not likely to be a wubi related issue, might be due to acpi. Try to stop it from terminal using the command

sudo halt

---

### Post by Asgar on 2008-12-16
> **Jammanuser said:**
> I hope u meant pulling it out while the computer was OFF! :D Pulling the power cord out of the socket while its still ON will most likely result in having a UNRECOVERABLE "crc error" while attempting to boot into the Wubi install! and that is something i can tell u right now u most **certainly ** do not want! ;) I had a "crc error" before, making my Wubi install effectively unbootable, and the only fix i found was simply **reinstall** Wubi, keeping the old root.disk, and then later replacing the new one with the old, so i would still have all my files and programs!

So just FYI...don't pull out the power cord while its still on! :p

Jam Man

:guitar:

Yes i agree pulling out any sort of cable while you plugged in is a no no.

---

