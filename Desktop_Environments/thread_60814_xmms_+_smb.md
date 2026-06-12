---
title: "xmms + smb"
date: 2005-08-29
forum: Desktop Environments
---

### Post by srv on 2005-08-29
Hi

I can't play music with xmms over smb. I can however play the music with totem  :-? 

Any suggestions ???

TIA

---

### Post by grim42 on 2005-08-29
XMMS doesn't use GNOME's VFS , so it can't access SMB shares the same way GNOME programs can.

You will need to mount the Windows share manually (with the mount command) and then access it via the mount point.

---

### Post by srv on 2005-08-29
Thank U so very much... Works great!  :)

---

### Post by batty505 on 2006-03-06
Hey Folks
Noob over here..<blush>

I have ubuntu client and M$ servers. I can connect to them, browse and view the netshares via smb.

problem occurs when I try to play the mp3's via xmms and netshares.

if I open xmms and try to browse all I see are local drives.
If I go to my netshares and right click and play with xmms nothing happens?

I dont know if its permissions or syntax? for me to try and play them via my ubuntu box.

I either have to browse up the tree and see the folder, from xmms?
or get the right syntax to open the folder with the app.

If someone has specific instructions I would appreciate it.
Incidentally, I am able to view, and copy and paste the mp3's to a local folder and run them from there, only on the netshares cant I not do this.

I will continue to  google. 

Please advise.
Mike

---

