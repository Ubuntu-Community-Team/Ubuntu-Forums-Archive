---
title: "strange things with files on a shared ntfs data disk on a dual boot system"
date: 2011-06-20
forum: Desktop Environments
---

### Post by wbloos on 2011-06-20
When i work in Ubuntu on a dual boot system with a shared NTFS data-partition where Windows is hibernated, and then reboot and continue working in Windows from the hibernated sesion, strange things happen.

Files disappear, files that i worked on suddenly have the content of another file.

It is not very surprising to me that this might go wrong. Just be warned.
Maybe there is even a way to reproduce this properly and fix it.

---

### Post by Mark Phelps on 2011-06-21
I believe that what happens, when you Hibernate MS Windows, is it makes a copy of stuff and saves it -- so it can restore the state of the machine when it "wakes up".

If that is true, changes you make to the files while Windows is hibernated are likely to be undone when it returns.

---

### Post by buckeyered80 on 2011-06-21
That is odd. How does it stay in hibernation when you boot into Ubuntu? Usually I have to restart Windows to get to my grub screen and boot into Ubuntu, so Windows is not able to be in hibernation while I am in Ubuntu. How does that work for you?

---

### Post by FormatSeize on 2011-06-21
> **buckeyered80 said:**
> How does that work for you?
This is the same thing I was wondering. I always thought when you reboot, the whole disk goes down and comes back up.

---

### Post by wbloos on 2011-06-27
I use windows xp professional.
Maybe you [that's asking how does it reboot into ubuntu] are using a different version of windows?
There's nothing particular to it. I just reboot, and grub shows.

cheers

---

### Post by wbloos on 2011-06-27
> **Mark Phelps said:**
> I believe that what happens, when you Hibernate MS Windows, is it makes a copy of stuff and saves it -- so it can restore the state of the machine when it "wakes up".

If that is true, changes you make to the files while Windows is hibernated are likely to be undone when it returns.

Well, that would be half as bad.
I think i corrupted my NTFS File Table with this.
I did a scandisk and lost a couple of files and a directory. I think i was lucky.

---

