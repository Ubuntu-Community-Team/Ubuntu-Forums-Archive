---
title: "Removing Windows Network from Thunar file manager"
date: 2020-03-21
forum: Desktop Environments
---

### Post by cyb3rtux on 2020-03-21
Hi!

Because newer windows operating systems no longer use NetBios/smb1 protocol, I want to remove "Windows Network" shortcut from network browsing panel in Thunar file browser.
Is there an way to do that?

---

### Post by him610 on 2020-03-21
> Because newer windows operating systems no longer use NetBios/smb1 protocol...
I was not aware of that.
What network protocol does Windows use now for LANs?

---

### Post by Morbius1 on 2020-03-22
> I want to remove "Windows Network" shortcut from network browsing panel in Thunar file browser.
Is there an way to do that?                 
I don't think so. You can remove Browse Network from the side panel but that would disable any visible SSH , FTP, SMB, Samba, etc.. multicast registered hosts on your network as well.
>  What network protocol does Windows use now for LANs?         
It uses the same protocol just a different dialect ( smb2 ... smb3 ). Win10 disables the smb1 dialect from both client and server but NetBIOS is dependent on smb1 so host discovery and name resolution using that is disabled.  Besides it now uses WS-Discovery for host discovery. 

Windows 10 does speak mDNS however so you can access a WIn10 server from Linux using it [highlight]smb://win10-host-name.local[/highlight] and Win10 can access a Linux server that way [highlight]\\linux-host-name.local[/highlight]. What Win10 cannot do is register or "broadcast" its mDNS presence the way Linux and MacOS can do by default so you have to access it explicitly.

---

### Post by cyb3rtux on 2020-03-22
Newer Windows uses WSD protocol for network neighborhood discovery. Windows clients can discover perfectly the samba server by installing wsdd daemon on the server.

I dont want to remove the entire Browse Network side panel from left side in thunar, only the pre-installed "windows network" shortcut within the Browse Network side panel, because it is unused. I think it is for automount with old Netbios/smb1 protocol, not for WSD or Zeroconf/Avahi protocol.

I think my probelem is about gvfs or fuse, because the situation is the same in Ubuntu and Nautilus.

Altough, if I install the Nautilus on my Xubuntu, the "Windows Network" shortcut does not appear within browse network side panel...

---

