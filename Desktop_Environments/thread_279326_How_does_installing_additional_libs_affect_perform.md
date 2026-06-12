---
title: "How does installing additional libs affect performanc on my desktop environment?"
date: 2006-10-17
forum: Desktop Environments
---

### Post by gctaylor1 on 2006-10-17
Hi,

I was reading a forum post here on ubuntuforums and the author suggested not to install gnome-cups-manager because it would pull in other dependency **libs** and thus slow down the system.  I've been thinking about that statement and wondering how this could be.  For example I'm using the xfce DE on xubuntu and if I pull in other libs how would it slow down the DE?  I can understand it will add files to the file system and use disk space, but generally it won't slow down the system so it's noticeable.  It might add longer to a find command and it might take a second longer to traverse a path, but what about the DE?  How could I measure this?  I'm coming from a source based distribution and I liked the perception that I was only installing what I wanted and I would like to keep my xubuntu installation pristine as much as I can.  Any thoughts?

Thanks,
Gary

---

### Post by az on 2006-10-17
> **gctaylor1 said:**
> I'm coming from a source based distribution and I liked the perception that I was only installing what I wanted and I would like to keep my xubuntu installation pristine as much as I can.  Any thoughts?



Whether you are running souce-based or binary packages, it mostly comes down to what the code was written to do.  In a source-based install, you may have fewer applications lying around which may allow you to save a few hunded megs of disk space (notwithstanding the few gigs of source code you have) but the applications will not be able to share libraries in any finer-grained way that with a binary package.  That's because the interface that the different applications have with each other is the same.

Some funky technologies such as autopackage rewrite some low-level libraries and allow for run-time interfacing between applications, but until all the unix developers on the planet aggree to one set of standards, we are not there yet.

So, if you are running XFCE, it uses the GTK2 libraries and will not be able to run without them in memory.  Whether you have other libraries lying around on your hard drive or not will not make any difference unless you run something that requires those libs - they are not loaded into memory otherwise.

Yes, if you have XFCE installed and then run a gnome application, the needed gnome libraries will be loaded into memory so that it can run.  Once you end the application, the memory will be freed when more ram is needed for something else.  If the app is still running, you will not be able to use that ram.

---

### Post by gctaylor1 on 2006-10-18
Azz, 
Thanks for taking the time to reply, that's an explanation I can understand.

Gary

---

