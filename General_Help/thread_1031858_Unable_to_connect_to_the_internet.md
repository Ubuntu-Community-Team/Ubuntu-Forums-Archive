---
title: "Unable to connect to the internet"
date: 2009-01-05
forum: General Help
---

### Post by dragos240 on 2009-01-05
Hello, i just installed KDE via apt-get install and i don't know how to connect to a network in KDE. Someone help, becuase it looks nice.

---

### Post by Wolf-Ekkehard on 2009-01-07
What kind of network are you trying to connect to?  Did you install Samba (this is what you need to connect to a Microsoft workgroup)?

If you have everything you need installed, you can use Dolphin and click on the little "home" icon to select "Network" (quite obviously).

---

### Post by dragos240 on 2009-01-07
> **Wolf-Ekkehard said:**
> What kind of network are you trying to connect to?  Did you install Samba (this is what you need to connect to a Microsoft workgroup)?

If you have everything you need installed, you can use Dolphin and click on the little "home" icon to select "Network" (quite obviously).

Oh, becuase i just need to connect wirelessly to my linksys router.

---

### Post by Wolf-Ekkehard on 2009-01-09
Got it.

Usually, KDE takes care of these things when it boots up, unless of course, your wireless device isn't working.  Can you ping the router? (in KDE you use a "konsole" to type > ping 192.168.0.1 or whatever IP address your Linksys uses).

---

