---
title: "Torrents on Ubuntu"
date: 2009-01-24
forum: General Help
---

### Post by Shady3D on 2009-01-24
hi, i am new to linux and i seek help so plz be patient on me.

the Problem :
torrents are not working as they supposed to work some torrents work amazing and some don't exceed 1 kb/s and also they suck the bandwidth from Firefox so i thought its from torrent but no, when i boot to windows and open that torrent it goes with 25kb/s on uTorrent (my max is 25) 

what i did:
i made some searches on torrent clients and i found 4 client was the best (Transmission, Deluge, Ktorrent, Vuse [Azuras]), so i tried all of them and looked on how to tweak every one but the problem remains the same.

the main thing to tweak torrent i did
1. forward port through firewall and the router >> so allowed the port on router and firewall and tested it and its opened (i check from a website & through torrent clients)
2. set upload & download limit >>  so i made speed test and made my upload 5 kb/s and download 25 kb/s
3. set maximum peers overall to 200, per torrent 50 
4. enable encryption
5. use UPnP or NAT-PMP

what i need:
so plz can any one tell me what is the problem, or how to tweak any bt client (even if its out of the 4 i mentioned earlier) so i can get 25 kb/s as in windows, because i hate to switch to windows.

another thing:
will it make any difference if i run uTorrent on Virtual Machine or Wine

more info:
OS: i use ubuntu 8.10 64
firewall: Firestarter (before) and now Gufw

---

### Post by diablo75 on 2009-01-24
If you've configured your router for port forwarding you should not use UPnP or NAT-PMP as you've listed in item 5.  And running a torrent client inside a VM will get you nowhere unless you were to port forward from Ubuntu to the VM (somehow??).

---

### Post by Shady3D on 2009-01-24
ok i removed UPnP or NAT-PMP but still the same

---

### Post by deltaromeo on 2009-01-24
> **diablo75 said:**
> ... running a torrent client inside a VM will get you nowhere unless you were to port forward from Ubuntu to the VM (somehow??).

This is not true.  THE OS running in the VM would get it's own LAN IP address (which the router can be configured to forward to).  The VM torrent client configuration would not involve any extra steps than that of the torrent client in Ubuntu.

Still, it's not the ideal solution.

---

