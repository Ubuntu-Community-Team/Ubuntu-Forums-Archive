---
title: "LInux/Windows Bittorrent comparison:"
date: 2006-01-07
forum: General Help
---

### Post by klepto on 2006-01-07
I've disabled the firewall in iptables and started downloading a torrent.
Knowing full well how bittorrent works but I see that in linux it will
start to download at 2kb/s then maybe 30kb/s then drop to 1kb/s 
and it will stall for a while.

In windows it starts slow and then I get speeds up to 300-400kb/s.
I am behind a linksys router have the ports forwarded to this machine.
I can't for the life of me figure out the problem.

---

### Post by Asraniel on 2006-01-07
try to use azureus as a bittorent client

---

### Post by kairu0 on 2006-01-07
[QUOTE=klepto]I can't for the life of me figure out the problem.[/QUOTE]

What client are you using?

---

### Post by klepto on 2006-01-07
i've used rufus and azureus.
Both have shown the same problem.
The linksys router uses nat and otherwise
all the ports are forwarded to this machine.
Bittorrent seems to be the only problem I am
having, but not when I boot into windows.

---

### Post by ace2005 on 2006-01-07
Try using Firestarter as the firewall, it will take over from iptables, and use Azureus.

This is the best method i have found to download torrent files on Linux

---

### Post by klepto on 2006-01-08
Thanks everyone for your input on this. I have solved the problem.
The problem is that the linksys router has forward options either tcp/udp or both
but if you set the port forwarding for both neither works. You have to make 2 entries for the tcp and the udp forwarding. Now I have green lights on azureus and all is well. 

Thanks, now the only reason I need to boot into windows is to move my backups to my usb 2.0 seagate
hard drive which is formatted in ntfs =(.

---

