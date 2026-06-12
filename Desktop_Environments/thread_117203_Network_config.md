---
title: "Network config"
date: 2006-01-14
forum: Desktop Environments
---

### Post by meimato on 2006-01-14
I installed kubuntu-desktop on my ubuntu linux, so now I've got bot desktop environment.
I experience some problems with network settings: if - under KDE - I set the IP address with the KDE control center the net doesn't work; but it - remaining under KDE - I use the gnome app to config IP everything works.
Now: it's not a problem using one app instead of the other, but why one should work while the other not?

---

### Post by Navyblue on 2006-01-14
The KDE control panel has been working that way since I begin using Kubuntu. And now I don't bother to use the Control Panel for real any network related settings.

Welcome to Kubuntu. :D

---

### Post by GeneralZod on 2006-01-14
There's a bug in the KDE network configuration app that doesn't save the "gateway" entry, which (I think!) is necessary for setting a static IP.  It's been fixed for Dapper, but I'm not sure if it will be backported to Breezy.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=9871](http://bugzilla.ubuntu.com/show_bug.cgi?id=9871)

---

### Post by zachariah on 2006-01-18
Ahhh, thankyou! I have been trying to get my Kubuntu box working with a static IP off and on for a while and this is probably why it never works, but DHCP always does...

Is it best to manually edit the /etc/network/interfaces file yourself or is there another tool to do this?

PS [General Zod for president!]("http://www.zod2008.com")

---

### Post by Ruskie on 2006-01-18
It's a text file, you can do that yourself. :)

---

### Post by zachariah on 2006-01-18
Yup, just made the changes to the file and it's all working smoothly now.

This bug should be a bit more widely known...Maybe there aren't that many Kubuntu users out there who need static IPs. Oh well.

---

