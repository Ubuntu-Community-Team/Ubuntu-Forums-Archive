---
title: "KDE newbie question"
date: 2006-02-17
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-02-17
Hi,

How can we see the network connection icon (which tells us what is the ip address, number of packers recieved etc) in KDE ? 

Gnome has easy options to see it. I heard KDE is more customizable then Gnome. Can you guys provide some quick tips as I just loaded KDE on my Ubuntu box.

Thanks

---

### Post by mmHg on 2006-02-17
Try [KNetDockApp]("http://www.kde-apps.org/content/show.php?content=29398").

---

### Post by krypto_wizard on 2006-02-17
Thanks, that is good one. Is there anything like one in Gnome. I like that very much.

[QUOTE=mmHg]Try [KNetDockApp]("http://www.kde-apps.org/content/show.php?content=29398").[/QUOTE]

---

### Post by mmHg on 2006-02-20
Maybe [WiFiradar?]("http://www.gnomefiles.org/app.php?soft_id=332")

---

### Post by infoseeker on 2006-03-15
Knetdockapp works fine but I have one issue with it:
I normally use 'DHCP' to assign an IP address but once I had to manually assign the address, mask, gateway and when reverting back to 'DHCP' , I am left with two (pairs of) indicators, both monitoring my eth0 (the only one I have).  On shutting down one of them, they both shut down.  On opening the app again, the two sets reappear :(.

Any solutions ?

EDIT : SORTED
edited '~/.kde/share/config/knetdockapprc' and removed second instance of interface.

---

