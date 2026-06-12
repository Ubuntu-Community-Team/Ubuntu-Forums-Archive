---
title: "xauthority issue?"
date: 2010-07-31
forum: Desktop Environments
---

### Post by Keinan on 2010-07-31
I purchased a dedicated box the day before yesterday on which I supposedly have Ubuntu 9.10 server running, when I look up my distro from the command terminal however it seems I'm running 10.4 lucid...perhaps that's just for the GUI...

AMD dual core 2.8ghz


I'm logging onto the box via my Windows XP machine using PuTTY to tunnel, and a tightVNC server/client.



Earlier today I installed ubuntu desktop, and a LAMP server. I checked the Apache2 server in Firefox, no problems there.


I then was trying to test my PHP, and needed to use gksudo gedit when I received the following error:


[I]Xlib: extension "RANDR" missing on display ":3.0".

Error copying '/home/user/.Xauthority' to '/tmp/libgksu-wodlbR' permissiondenieduser@ubuntu:
[/I]

Does anyone know how to fix this issue, and if so would they be so kind as to walk me through it?  Thank you in advance!

I'm relatively new to Ubuntu. I tested it out on my home PC using WUBI and was able to install LAMP and use all the terminal commands with no trouble. It was a very pleasant experience which is why I chose it as the linux flavor for the dedicated box.

---

### Post by Keinan on 2010-08-01
I was wondering if alternatively, I could change permissions to all directories and files on the computer? 

In this way I may be able to edit all of the files (like .ini files) from the desktop without having to use the terminal (and thus bypass the RANDR issue)?

---

