---
title: "Can play mp3 from stream or local file but not from Windows server"
date: 2006-03-18
forum: Desktop Environments
---

### Post by Guyllfyre on 2006-03-18
OK, here's a problem that it seems I'm having only with Ubuntu Breezy.

_**Here's the situation:**_
I can play my mp3 files if I copy them off the server share to the Ubuntu box.

I can tune/listen in if I stream them using my Shoutcast server to stream.

I CAN NOT play my mp3s from the server share directly.  XMMS simply displays the filename and Totem gives me an error about not being able to play it back because it's an unknown format.

I have booted with the Kororaa LiveCD and *IT* can play the mp3s off the server.  So it's not a general Gnome/Linux issue.

I have updated smb and smbfs and attempted to configure the networking to see if it's some sort of authentication problem.

I have mounted the network share and tried, same result.

Any ideas?

Thanks,

Sean

---

### Post by stalefries on 2006-03-18
It may be an issue with GnomeVFS. Try looking into that.

---

### Post by nianhbg on 2006-03-19
[QUOTE=Guyllfyre]OK, here's a problem that it seems I'm having only with Ubuntu Breezy.

_**Here's the situation:**_
I can play my mp3 files if I copy them off the server share to the Ubuntu box.

I can tune/listen in if I stream them using my Shoutcast server to stream.

I CAN NOT play my mp3s from the server share directly.  XMMS simply displays the filename and Totem gives me an error about not being able to play it back because it's an unknown format.

I have booted with the Kororaa LiveCD and *IT* can play the mp3s off the server.  So it's not a general Gnome/Linux issue.

I have updated smb and smbfs and attempted to configure the networking to see if it's some sort of authentication problem.

I have mounted the network share and tried, same result.

Any ideas?

Thanks,

Sean[/QUOTE]

I had some simulare problems i just mounted the network share in my fstab file. And now its working like a charm.

---

