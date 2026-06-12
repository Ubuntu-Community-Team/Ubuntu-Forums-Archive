---
title: "How to remove network manager icon??"
date: 2007-05-01
forum: Desktop Environments
---

### Post by Turin Turambar on 2007-05-01
The network manager icon in the systray is useless for me and quite annoying (taking some precious space)... How can I remove it? I'm using feisty.

Thanks!

---

### Post by jerrylamos on 2007-05-01
System, Administration, Synaptic Package manager, then search for Network Manager.  The menu will let you delete the package from Feisty Fawn 7.04.  That deletes the icon from the screen.

Now in my case, that wasn't any good, since during boot Network Manager disables my network card even when the Network Manager package is removed.  Then to activate the network card I have to bring up a terminal and do sudo dhclient, then enter the password.  If I leave the icon on the screen I click on it, then click on wired network, and it activates my card.  The same one it inactivated on boot....

Cheers, Jerry

---

### Post by JerseyShoreComputer on 2007-05-01
Jerry is correct. You cannot simply remove just the icon, you need to remove the entire package and I think that would do more harm than good. But I agree that it is annoying, and I have found it totally useless. I am still doing manual configs for the networks and have found decent results with that, I was able to connect at work today for the first time.

---

### Post by Turin Turambar on 2007-05-02
Thanks guys. I disabled the network service with sysv-rc-conf tool. It removed the icon without removing the entire package. :)

---

### Post by Mujaheiden on 2007-05-31
which item is it then?

---

