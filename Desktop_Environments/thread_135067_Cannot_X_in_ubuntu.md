---
title: "Cannot X in ubuntu"
date: 2006-02-23
forum: Desktop Environments
---

### Post by akdkumar on 2006-02-23
Hi

I have installed ubuntu 5.10 on my x86 PC and it is working fine. But I cannot access its desktop from another PC with windows. I am using Xmanager2.0 from NetSarang.

Is there any additional step I should take?...

---

### Post by gibson on 2006-02-23
[http://www.ubuntuforums.org/showthread.php?t=42941](http://www.ubuntuforums.org/showthread.php?t=42941)

[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

[http://www.ubuntuforums.org/showthread.php?t=135036](http://www.ubuntuforums.org/showthread.php?t=135036)

then get vnc client from realvnc

hth

---

### Post by lamego on 2006-02-23
I guess you want to connec remotly using an X session .
The default options for the X server started by gdm is **not ** to create the listener to accept remote X connections.

You can edit /etc/gdm/gdm.conf, remove the "-nolisten" option and then restart the X server .

---

### Post by akdkumar on 2006-02-24
Hi

I checked gdm.conf. there is no -nolisten option anywhere.

below [xdmcp] there is the entry Enable=false.
this I made true and restarted xdm . 
The screen goes blank after this.
infact this happens even when Enable=true.

---

### Post by lamego on 2006-02-24
I did the change myself, I apologise it must be on another config file which I don't remember right now. I will let you know if I can find it.
But I believe my analysisis of the problem is correct, there is a gdm or X related config option which is set "not to listen" for remote connections.
If you do a "ps -ef | grep X"
you should see the option on the X server command line.
I just don't remember from which config file does it come from...

---

### Post by akdkumar on 2006-03-01
Hi

I removed the option '-nolisten' by following method:

1. goto System>Administration>Login Screen Setup
2. choosing tab Security
3. unselect 'Deny TCP Connections to XServer'
4. Restart System

Now on the remote server ubuntu icon appears on remote machine.
I am able to supply login name and password. 
Thereafter screen goes blank.

---

### Post by akdkumar on 2006-03-02
Hi ALL

Finally I could connect remotely to my ubuntu machine via vncviewer.

Thanks everybody.

:-D

---

