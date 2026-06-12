---
title: "Automounter problems in KDE"
date: 2008-06-18
forum: Desktop Environments
---

### Post by charstar on 2008-06-18
Hi, I am having a problem with the automounter when i use KDE.  I installed Xubuntu and then decided i wanted to use KDE.  I installed the KDE package in the synaptic manager.  Now when i am in a kde session cd's nor usb keys will automount.  /var/log/messages shows no errors and the devices are detected properly but no mounting is attempted.  I can also mount them manually withought problem.  If i log into the Xfce session everything works perfectly.  Cd's and usb keys are detected and mounted automaticly.

I suspect that either something needs to be installed or that something is not being started.  Anyone have any ideas?  I know very little about the automount process.

Thanks.

---

### Post by diaa on 2008-06-26
Unfortunately there are some automounting problems with KDE, you should install *pmount*, *hal* and *dbus*, if any is installed I suggest that you reinstall it
I was having some problems but fortunately they are now less severe.

tell me if this helps

---

