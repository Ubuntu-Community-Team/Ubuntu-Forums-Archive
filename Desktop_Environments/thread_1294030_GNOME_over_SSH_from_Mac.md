---
title: "GNOME over SSH from Mac"
date: 2009-10-17
forum: Desktop Environments
---

### Post by brennon80 on 2009-10-17
Hi all,

I know this has been asked about a lot, but I've gone through all sorts of posts and just can't seem to figure this out.

I'm running Ubuntu 8.10 on a server on the other side of the world, and would like to forward a desktop manager over SSH to my Mac on this side of the world.  I've been following the instructions here:

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

I've installed GNOME on my Mac, and am trying the following:

1. From the Mac terminal, run xinit.
2. At the xterm, run "ssh -X [email]username@remote.machine.com[/email]"
3. Once connected, run gnome-desktop.

Upon running gnome-desktop, I get the following error:

** (gnome-session:6019): WARNING **: Cannot open display:

Searching for this error message turned up a lot, but nothing that seemed to help.  The last thing I tried was setting the DISPLAY envar explicitly before running gnome-desktop.  I've tried:

export $DISPLAY=my.ip.address:0.0

When I then run gnome-desktop, no error is produced, but GNOME never appears, either.  The same thing also happens with xclock, etc.  I'd appreciate any help I can get.

Thanks!

---

### Post by zaksworld on 2009-10-17
I might be wrong (please correct me if I am) but isn't the Ubuntu Server Edition only a command line?

If that's true then I don't think it would be able to give you a display (or run GNOME for that matter), since it doesn't have a Desktop

Of course, if the Server Edition can have a desktop, this could be wrong.

---

### Post by brennon80 on 2009-10-17
I'm not running Ubuntu Server Edition...just running Ubuntu on a server...

---

