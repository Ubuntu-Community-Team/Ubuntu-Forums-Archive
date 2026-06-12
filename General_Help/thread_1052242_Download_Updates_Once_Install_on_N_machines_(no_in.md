---
title: "Download Updates Once Install on N machines (no internet)"
date: 2009-01-27
forum: General Help
---

### Post by UranUtan on 2009-01-27
Hi,

Is there any way to download all the updates and store them on an external USB drive.

Then each time I install Ubuntu 8.10 on a new machine, I just run the updates locally without waiting 2+ hours for the online update?

Thanks in advance for any help.

---

### Post by Coreigh on 2009-01-27
You would essentially be creating an unofficial mirror of the repos. I know that the install CD is used as a repo sometimes so it should be a matter of editing the sources.list file to tell it where to look.

If you are running a network of a number of ubuntu computers (all the same version with all the same software) you could set the primary (server, gateway, most powerful whatever) as a mirror. If I understand correctly the repos are basically a specialized web site for hosting the packages.

---

### Post by UranUtan on 2009-01-27
I am very novice in Ubuntu. Can you describe in more details? Where to click, what to edit, what to configure, etc.

May be there is a documentation somewhere. I would appreciate some pointers.

I hope I am not the only one in the world to attempt such an operation.

---

