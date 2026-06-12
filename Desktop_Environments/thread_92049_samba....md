---
title: "samba..."
date: 2005-11-18
forum: Desktop Environments
---

### Post by akurashy on 2005-11-18
Ok I been trying to battle with this for some time now, i can't enter my brother's pc, when i see ubuntuguide it only says to share. i see his computer in the network servers folder. but i want to get some files off 

it tells me this message

The filename "DANNY" indicates that this file is of type "desktop configuration file". The contents of the file indicate that the file is of type "x-directory/smb-share". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "x-directory/smb-share", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by akurashy on 2005-11-18
giving a bump, i really need this fixed =/

---

### Post by MetalMusicAddict on 2005-11-18
Do you want to be able to mount a shared drive (at boot) from his machine or just browse and use his files causally? Were you tryin to open a WMV/A?

---

### Post by HermanAB on 2005-11-18
Here is some help:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman

---

### Post by akurashy on 2005-11-18
[quote=MetalMusicAddict]Do you want to be able to mount a shared drive (at boot) from his machine or just browse and use his files causally? Were you tryin to open a WMV/A?[/quote]

I'm trying to enter his machine to grab some files I need

---

### Post by j79zlr on 2005-11-26
I've had this problem intermittently on Linux/FreeBSD machines with nautilus for as long as I can remember, the only reliable way to view shares is to use the CLI.

smbclient -Uusername //computername/sharename

---

