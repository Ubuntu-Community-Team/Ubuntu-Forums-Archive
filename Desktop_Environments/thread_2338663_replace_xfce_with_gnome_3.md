---
title: "replace xfce with gnome 3"
date: 2016-09-30
forum: Desktop Environments
---

### Post by windowsfree on 2016-09-30
Hello,

Is it possible to replace the xfce environment in Xubuntu 16.04 with Gnome 3 environment?

Can you show me where to do this?

Thanks.

---

### Post by Frogs Hair on 2016-09-30
Gnome 3 could mean the gnome-shell , gnome (full desktop environment), gnome-session-flashback.

It's possible to add and remove additional  desktop environments from the repository though I've never removed the native DE. The synaptic package manager is the best tool I know of for adding and removing desktop environments though I'm not sure you can remove xfce without affecting the Xubuntu desktop.

---

### Post by windowsfree on 2016-09-30
Thank you for the quick reply,  I will try this after generating an image of my HD as it is.
:)

---

### Post by ajgreeny on 2016-09-30
In general terms it is not so much a replacement as an additional DE that is added to the system.

Totally removing a DE is not such a simple act as perhaps you think it is, but adding **ubuntu-gnome**, which is just a metapackage which pulls in everything needed for ubuntu-gnome, should be easy in 16.04 using whatever package management you normally use; I would suggest you use synaptic for maximum detail on everything that will be installed alongside the **ubuntu-gnome** package.

You can remove **xubuntu-desktop** package, another metapackage, with synaptic as well but it will not remove all the packages that make up xubuntu as it just pulls in everything needed for xubuntu but does not remove them when you remove it.

There is some info at [http://www.psychocats.net/ubuntucat/tag/pure-ubuntu/](http://www.psychocats.net/ubuntucat/tag/pure-ubuntu/) for removal of full DEs from systems leaving another pure DE system, but I have never used it and it is not yet updated for 16.04 as far as I can see.

---

### Post by vasa1 on 2016-09-30
> **ajgreeny said:**
> ...

There is some info at [http://www.psychocats.net/ubuntucat/tag/pure-ubuntu/](http://www.psychocats.net/ubuntucat/tag/pure-ubuntu/) for removal of full DEs from systems leaving another pure DE system, but I have never used it and it is not yet updated for 16.04 as far as I can see.A quote from ubuntuforums.org/showthread.php?t=416802&p=12695426 
> ... Truth be told, I may not do many updates at all in the future. I had grand plans to keep this up indefinitely, but things have been getting busier at work ...

---

### Post by windowsfree on 2016-10-04
Thanks for the replies, I have added the Gnome 3 desktop successfully.  I will keep both DE as there appears to be no issue and I can just choose at login.

Thank you.

---

### Post by windowsfree on 2016-10-05
I installed gnome 3 and all seemed well for a few days.  Not I am getting an error when logging in.  I sent in the error as prompted. Is there an issue with XFCE and Gnome 3 being installed on same computer.  I could understand conflicts if using KDE, but don't understand why these can't work side by side.
There are 2 users on the computer.  User 1 gets the error when logging into XFCE.  User 2 gets the error when logging into Gnome3.  User 1 tried logging into Gnome 3 and error pops up again.

Any suggestions, other than removing Gnome 3 ?

---

### Post by Frogs Hair on 2016-10-05
Does the Apport/error reporting system open at each login ? If you have reported the error you can check a box to ignore the same error in the future. Persistent errors are addressed by developers if enough user are affected.

---

### Post by windowsfree on 2016-10-12
Reinstalled OS, dual booting Xubuntu and Manjaro Gnome.   all is good.

---

