---
title: "Casting your desktop to a LG webOS TV"
date: 2024-06-16
forum: Desktop Environments
---

### Post by makem2 on 2024-06-16
I have a [LG] webOS TV in the same room as my xubuntu desktop computer and router.

I have installed Gnome Network Displays on the PC and both machines are on the same 5G network.

When I connect the PC to the TV via wifi the TV puts up a 'cancel' option and no option to connect. The Network display app only has an option to 'Return' which closes the connection.

If I do nothing and wait the connection times out and returns to the TV program. The TV is obviously waiting for permission to connect.

I cannot see any way to 'accept' the connection via the TV remote.

I appreciate this is a TV problem but wonder if anyone has come across the same or similar problem as most smart tvs are similar in operation. In the meantime I will try to find an LG TV forum.

---

### Post by currentshaft on 2024-06-16
I would not use webOS for this and I absolutely wouldn't connect a "smart" TV to the Internet.

Why not just connect your Ubuntu PC to the TV via HDMI? If you need to control it remotely, use a second computer with VNC.

---

### Post by makem2 on 2024-06-16
The tv and computer are on opposite side of the room! I don't need to control the tv, just cast to it, eg. movies, photos etc.

---

### Post by Claus7 on 2024-06-16
Hello,

as far as I can see gnome network displays is an experimental endeavor. Not much help to your issue, yet I remember, a long time ago, using chrome to connect ubuntu to miracast or something similar, so you could search that as an alternative. I expect a more experienced member to give you the answer you are seeking.

Regards!

---

### Post by makem2 on 2024-06-17
> **Claus7 said:**
> Hello,

as far as I can see gnome network displays is an experimental endeavor. Not much help to your issue, yet I remember, a long time ago, using chrome to connect ubuntu to miracast or something similar, so you could search that as an alternative. I expect a more experienced member to give you the answer you are seeking.

Regards!

Thank you. I do feel the problem is with the TV end and just wondered if anyone had found a solution. Gnome Network Display seems to work correctly.

I am attempting to find a solution via a TV forum and suppliers in the meantime.

It has been suggested I need an Android emulator to get Linux to talk to an Android TV.

---

### Post by Holger_Gehrke on 2024-06-18
A lot of "Smart" TVs can act as clients for various streaming servers e.g. DLNA servers. So I'd consult the manual of the TV and take a hard look at the options for that. Alternatively I've seen the option to connect to a Windows network share to play media files located on that share on some TVs.

Holger

---

### Post by ActionParsnip on 2024-06-20
If you want to access the media on the TV then setup something like Plex or a simple Samba share (Or whatever technology the TV can connect to). Much easier

---

### Post by makem2 on 2024-06-25
I ended up finding Jellyfin which I can use on my pc until I get a NAS.

---

