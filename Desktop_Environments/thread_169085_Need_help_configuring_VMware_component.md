---
title: "Need help configuring VMware component"
date: 2006-05-01
forum: Desktop Environments
---

### Post by _Chris_ on 2006-05-01
I have successfully installed VMware Server Beta on Ubuntu 5.10.  

Unfortunately, the program will not allow me to input the serial number.  The error I get is "Unknown error entering serial number: no permission to perform this operation".  

I found some info regarding the need to install xlibs, or libx11 (has something to do with password storage?).  I installed xlibs from Synaptec Package Manager, but it did not help.  

Has anyone experienced a similar situation, or have any suggestions?  

Thanks in advance. 
Chris

---

### Post by chriscando on 2006-05-02
Can you do it as root (or use sudo)? This may not be a perfect solution but it would at least tell you if its just a permission problem and that its something your missing.

---

### Post by _Chris_ on 2006-05-02
[QUOTE=chriscando]Can you do it as root (or use sudo)? This may not be a perfect solution but it would at least tell you if its just a permission problem and that its something your missing.[/QUOTE]

Thanks for the advice!  I executed VMwre from the terminal, as a root user.  Unfortuantely, that did not work either.  I think i'ts time to hit the manual again to look for anything I may have missed. 
Thanks, 
Chris

---

### Post by _Chris_ on 2006-05-03
Seems that it was a permission problem.  I was able to run 'root vmware', and then enter the serial.  I'm not sure why it didn't work the first time (I typed sudo -i, then ran vmware).  Is that different than the former?

---

### Post by TWFJR on 2006-05-03
May 2006 Linux Magazine, A Trio of Linux Tricks by Jason Perlow. Trick Three:  Getting VMWare Products to Work in Ubuntu (and Debian.)

---

### Post by _Chris_ on 2006-05-03
[QUOTE=TWFJR]May 2006 Linux Magazine, A Trio of Linux Tricks by Jason Perlow. Trick Three:  Getting VMWare Products to Work in Ubuntu (and Debian.)[/QUOTE]

Thanks for the info; I'm definitely going to look into that.  VMware has proven quite tricky so far, but I have finally gotten it working (to some degree).

---

