---
title: "Problems after changing gdm to kdm"
date: 2010-10-07
forum: Desktop Environments
---

### Post by guimenez on 2010-10-07
I've changed my default login manager to kdm. Because gdm fails to unmount cifs shared folders and hang at logoff (this is a problem that is going with gdm for sometime).

Everything works fine at login, but when i logoff it goes to terminal and i need to put the command startx to go again to GUI mode.

Please, how can i fix that

thanks

---

### Post by glitch323 on 2010-10-07
> **guimenez said:**
> I've changed my default login manager to kdm. Because gdm fails to unmount cifs shared folders and hang at logoff (this is a problem that is going with gdm for sometime).

Everything works fine at login, but when i logoff it goes to terminal and i need to put the command startx to go again to GUI mode.

Please, how can i fix that

thanks

How did you change it from gdm to kdm?
Did you use this to change it?: $ sudo dpkg-reconfigure gdm
I would try that command first if you haven't already, maybe it will reconfigure everything.

---

### Post by guimenez on 2010-10-07
Thanks for replying. 
I used the command you mentioned above 
for changing the kdm. At login it works
Well but when close session it goes to terminal :(

Thanks

---

### Post by glitch323 on 2010-10-08
Hmmm, I'm not sure why it would do that...  How did you install the kdm login manager?  Was it part of the full kubuntu-desktop package?

I found this, are you running intel graphics drivers? [http://ubuntuforums.org/showthread.php?t=1205382](http://ubuntuforums.org/showthread.php?t=1205382)

---

### Post by glitch323 on 2010-10-08
This may help too: [http://kubuntuforums.net/forums/index.php?topic=3111707.0](http://kubuntuforums.net/forums/index.php?topic=3111707.0)  
Seems to talk about the same thing.

---

### Post by guimenez on 2010-10-09
Many thanks

i will look at and hope find the solution.

thanks

---

