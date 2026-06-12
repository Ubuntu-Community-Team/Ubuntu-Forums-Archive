---
title: "Help, lost shutdown option on logout (due to Beryl?)"
date: 2006-12-30
forum: Desktop Environments
---

### Post by mgrusin on 2006-12-30
Hi, at some point, maybe when I installed Beryl (successfully AFAICT), the logout panel lost the option to shutdown the computer.  It still has suspend and resume (which don't work yet but that's another thread).  I'm sure shutdown used to be there.  Is there an easy way to add it back in?

Edgy 6.10.  Thanks, -MG.

---

### Post by Didius on 2006-12-30
You can log-out and shutdown then.
Or you can type in the terminal 

sudo shutdown-r now

(or make a shortcut in the gnomepanel with this command
gksudo shutdown -r now )

---

### Post by jjross on 2006-12-30
There are a lot of threads about this, do a search and check them out.
What worked for me was to go into Synaptic Package Manager and reinstall gdm.
Try this at your own risk and please do read the other posts concerning this.
Good luck

---

### Post by mgrusin on 2006-12-30
Thanks for the replies, I'll look again for other threads.

-MG.

---

### Post by mgrusin on 2006-12-30
Resolved with help from [this thread]("http://www.ubuntuforums.org/showthread.php?t=244662").  Thanks all!

-MG.

---

