---
title: "Firestarter Issues"
date: 2005-04-05
forum: Desktop Environments
---

### Post by pruett57 on 2005-04-05
Okay, I've read all the How To's and double checked and I'm still having issues.
I can get it installed without an issue. I can get it to start without a 'root' prompt and start minimized. My problem is that although it does all these things I still get the unable to start Firestarter you need root privs...but the thing is started.


In sessions I do have the gksudo path

Here is the info I followed:
[http://www.ubuntuforums.org/showthread.php?t=7812&page=2&pp=10&highlight=firewall](http://www.ubuntuforums.org/showthread.php?t=7812&page=2&pp=10&highlight=firewall)

Also, if I remove it from the Sessions (Startup) panel I still get that silly error.

Thanks,

jp

---

### Post by ubuntu_demon on 2005-04-09
the second post of that thread says this :

> 
When you log in you should find that the Firestarter program is already running. Adding it to the Panel is superfluous after the initial setup. Thereafter you can change firewall parameters from the Root Terminal.


And he is absolutely right. Just start the firestarter gui when you want to make changes. It is always running in the background unless you do the command "sudo firestarter -p" or use the gui to stop the firewall.

---

