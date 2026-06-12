---
title: "Remote Desktop not allowing computer to be connected to!!"
date: 2009-04-18
forum: General Help
---

### Post by s3a on 2009-04-18
When the Ubuntu 8.10 installation on my mother's computer was a fresh installation, I could connect from my Debian computers to help her out from a distance if she needed help but now it doesn't even work! It doesn't work on her account as well as my account on that computer! It's not a problem with the Debian computer because I can connect to another computer with it. I'm sure it would make a difference to know that when I try to connect, it does ask me for the password and that occasionally it has almost connected in the sense that, it started to show the screen but then just had weird colours that almost look like the screen of the computer I am trying to view. 

I would like to avoid a fresh install so if anyone has any ideas on how to solve this, please tell me! Any help would be greatly appreciated!

Thanks in advance!

---

### Post by justin_guerin on 2009-04-18
What programs are you using to share the desktop on your mother's computer?  What client program are you using on your Debian computer to connect?  What options are you using to connect?

It may also be helpful to know what changed since the last successful connection.  Did you upgrade your computer?  Did your mom's computer get upgraded?  Were any settings changed on the router / firewall she's using?

Be aware that most remote desktop software will use a smaller color palette than the actual desktop, so if the colors are slightly off, but the desktop otherwise looks fine, you're probably OK and connected to your mother's desktop.

---

### Post by s3a on 2009-04-19
I am using **Remote Desktop Viewer** and **Remote Desktop** from **Applications-->Internet** and **System-->Preferences** respectively. I am using the exact same programs on my Debian Lenny, Debian Squeeze and Ubuntu 8.10 systems.

As for the colours, I meant, you can't make off anything at all, like it's a complete blurr but I just recognize the colours but you can't actually see anything. The only thing I could think of that could have damaged anything is using the update manager to update my mother's applications on Ubuntu 8.10 but I am not sure if that is the exact cause.

Thanks!

---

### Post by justin_guerin on 2009-04-19
Some folks have reported problems that sound similar to yours when they have Compiz / Beryl enabled on the server machine.  You may want to check if turning it off on your mother's machine fixes the problem.

[http://ubuntuforums.org/showthread.php?t=411135](http://ubuntuforums.org/showthread.php?t=411135)

---

