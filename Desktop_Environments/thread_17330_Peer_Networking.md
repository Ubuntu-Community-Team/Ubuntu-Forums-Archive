---
title: "Peer Networking?"
date: 2005-02-27
forum: Desktop Environments
---

### Post by mark on 2005-02-27
(Mods - if I'm in the wrong place, please move & advise me where.)

I'm really exposing my ignorance of Linux networking here, so don't laugh.  (Oh, okay - go ahead and laugh...)

I want to do file & printer sharing between my desktop and laptop PCs.  My desktop runs Ubuntu (Warty & Hoary), my laptop Ubuntu (Warty) and Windows XP.  I don't want to set up a server, if I don't have to.

Ideally, I would plug my laptop into my router (NetGear RP-614) and have it see my desktop (and vice-versa).

As I mentioned, I'm really clueless re: *nix networking - the last *nix "network" I had anything to do with was a bunch of PCs running terminal emulation software, connecting to a XENIX server over tty (serial) lines.

Can somebody point me in the right direction?

*Thanks!*

---

### Post by RichardA on 2005-02-28
Here's a start:

If one of the clients is Windows, you'll want to run the Samba daemon on the desktop PC and share out a folder. Edit /etc/samba/smb.conf and then do '/etc/init.d/samba restart' to apply changes.

Either browse to it from the client or add a line in /etc/fstab to mount it on boot (or map a drive when in Windows).

Not sure about printing. I think you set up a printer on the client that prints to the IP address of the desktop.

---

### Post by mark on 2005-03-09
[QUOTE=RichardA]Here's a start:

If one of the clients is Windows, you'll want to run the Samba daemon on the desktop PC and share out a folder. Edit /etc/samba/smb.conf and then do '/etc/init.d/samba restart' to apply changes.

Either browse to it from the client or add a line in /etc/fstab to mount it on boot (or map a drive when in Windows).

Not sure about printing. I think you set up a printer on the client that prints to the IP address of the desktop.[/QUOTE]Richard, thanks very much for the reply.  Sorry for the ACK delay, I've been having fun with pneumonia here lately...as one of the aliens on *Babylon 5* once said to Sheridan: > "We all heard you were dead!" Sheridan: > "Yes, but I'm much better now..." 

Thanks again!

---

