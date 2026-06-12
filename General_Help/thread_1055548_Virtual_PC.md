---
title: "Virtual PC"
date: 2009-01-30
forum: General Help
---

### Post by RedSingularity on 2009-01-30
I have been looking for an answer to this for an hour now and i cant find it.  I am running Ubuntu with VirtualBox installed.  Inside virtualBox i am running vista.  How can i get a network connection within vista though?

---

### Post by easybake on 2009-01-30
Did you try this? [http://forums.virtualbox.org/viewtopic.php?p=9546&sid=defe2536ec81f81c0c30aed70f1e2b95]("http://forums.virtualbox.org/viewtopic.php?p=9546&sid=defe2536ec81f81c0c30aed70f1e2b95")

---

### Post by RedSingularity on 2009-01-30
Yea but that doesnt seem to work.

---

### Post by RedSingularity on 2009-02-01
Nevermind, got it.

---

### Post by easybake on 2009-02-01
> **Shadow121 said:**
> Nevermind, got it.

It would be good to post what you did in case anyone else had the same problem.

Edit: mark this thread as solved in the 'thread tools' menu

---

### Post by RedSingularity on 2009-02-02
Well in Windows it seems you need to get Network Drivers before you can use the NAT to connect.  The proper driver is found here [http://www.microsoft.com/downloads/details.aspx?familyid=DC8332D6-565F-4A57-BE8C-1D4718D3AF65&displaylang=en]("http://www.microsoft.com/downloads/details.aspx?familyid=DC8332D6-565F-4A57-BE8C-1D4718D3AF65&displaylang=en").  One I saved it to my desktop and mounted the ISO image into the Virtual Machine it booted in windows with a setup prompt.  When your done with the setup the drivers will be installed and you can connect to your network within the Virtual Machine.

---

