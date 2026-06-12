---
title: "Headless VNC using GDM"
date: 2008-12-11
forum: General Help
---

### Post by slapnutz on 2008-12-11
Hello,

I currently have a headless ubuntu rig setup (Hardy) currently acting as a fileserver. I also want to end up using it as a media center of sorts, but for now I just want to get VNC working remotely.

I currently do have a working VNC setup, but it goes into fluxbox instead of GDM, which is exactly what the tut I read intended. 

However, I would much rather just have a gdm session as it is easier to navigate, at least for me. 

If setting this up would involve attaching a monitor to the computer at some point, I can do that, but preferably as a one time thing as I do down the server occasionally when its not going to be accessed for a long time. 

I've read through many different tutorials on getting VNC to work on a headless server, but none of them have been for GDM, or the ones that were for GDM weren't for ubuntu, or there was some other minor detail that I couldn't work around. If anyone has any suggestions on how to work towards getting this to work I would greatly appreciate it.

Thanks,
~Mike

---

### Post by albinootje on 2008-12-11
I prefer using FreeNX over VNC, and FreeNX can use xdm, and probably gdm too.
It is a bit harder to set up than VNC, but not so difficult as it used to be years ago.

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by mattyB on 2008-12-11
Another possible solution that you might look into is !machine.  I've had good luck with their solution in the past.
[http://www.nomachine.com/](http://www.nomachine.com/)

Yet another VNC over ssh solution (this is one that I use) that you might also look into is [http://ubuntuforums.org/showthread.php?t=795036](http://ubuntuforums.org/showthread.php?t=795036).

Cheers,

mattyB

---

### Post by slapnutz on 2008-12-12
Thank you both.

So far I'm going to try FreeNX (Which I think is a variant of NoMachine aka !Machine). I followed the guide and have gotten to the connection point, and once I get authenticated it flashes a screen with the !M logo and then it disappears.

The output when I click details is:
```

Info: Display running with pid '5408' and handler '0x2b019e'.

NXPROXY - Version 3.3.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '5576'.
Session: Starting session at 'Fri Dec 12 12:39:11 2008'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Fri Dec 12 12:39:11 2008'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Fri Dec 12 12:39:12 2008'.
Session: Session terminated at 'Fri Dec 12 12:39:12 2008'.
```

I've tried with all of the options for the type of window manager. I am currently googling for a way to solve this, but I figured I post here to see if anyone knew.

Thanks for any help, and I'll post if I figure it out.

---

### Post by albinootje on 2008-12-12
This might help :
[http://openfacts2.berlios.de/wikien/index.php/BerliosProject:FreeNX_-_FAQ](http://openfacts2.berlios.de/wikien/index.php/BerliosProject:FreeNX_-_FAQ)

It's also a good idea to first use "ssh -X" in a terminal, and then test that.
And check the logfiles on the server, like /var/log/auth.log


I'm using FreeNX server on Intrepid, connecting with Intrepid as client.
The only problem i had so far was a keyboard problem (there was a bug-report for that already) with the arrow-keys, which is now solved.

---

### Post by HermanAB on 2008-12-12
One word: OpenSSH

Millions of headless Google servers can't be wrong.

---

### Post by Peter09 on 2008-12-12
FreeNx uses ssh.

Test your connection first using

```
ssh -X <username>@<servername> xterm
```

---

### Post by slapnutz on 2008-12-12
Yea I already have SSH working. Thats how I got it setup to work with fluxbox initially. 

I'm connecting from XP with the server running ubuntu. I've tried the VNC with SSH link to no avail, but I'm going to try again later once I recoup from finals.

---

### Post by slapnutz on 2008-12-17
Figured it out...or at least found something that when changed caused it to work.

For whatever reason, my .Xauthority file keeps getting its ownership changed from my username to root. I simply changed it from root to my name and poof it worked...in fact a lot of things started working. Now I just need to figure out A. why it keeps changing to root and B. How to prevent such behavior.

PS: After 5 minutes of using FreeNX I am already a fan.

---

