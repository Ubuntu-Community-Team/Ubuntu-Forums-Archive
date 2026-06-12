---
title: "No printing after deleting /var/spool*"
date: 2006-04-02
forum: Desktop Environments
---

### Post by chris_andrew on 2006-04-02
Hi,

I sent a print job from Gimp, and my printer HPDeskjet 610C just kept doing line feeds and sending 100's of pages of blank paper through the printer.  I was completely unable to stop it.  After half an hour, I *su -* , then deleted */var/spool/** , thinking that the *cups* directory would be re-created on the next print job.  Unfortunately, this doesn't happen, and now I can't print.

Can anybody help me get my printing working?

Many thanks,

Chris.

---

### Post by WickedImp on 2006-04-02
wow! that's rough, man. hmmm... first thoughts are to reinstall cups or first try dpkg-reconfigure. maybe this will recreate your directories. but I think that's not enough. other programs use the spool directory, also. if you encounter problems: try to reconfigure or reinstall.

---

### Post by chris_andrew on 2006-04-02
Used Synaptic to mark CUPSYS for re-installation, and it created the directory with good permissions.  Sorted :-)

---

