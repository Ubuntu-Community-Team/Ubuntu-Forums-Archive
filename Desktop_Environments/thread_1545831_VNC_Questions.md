---
title: "VNC Questions"
date: 2010-08-04
forum: Desktop Environments
---

### Post by pittmantechno on 2010-08-04
Hello ! 

I have a few Ubuntu Server's and Desktops, And i would like to be able to VNC into them more effectively. 

From what I can tell it is not possible to start a VNC session, unless the system has been physically logged in to a User's Desktop environment.  

in other words, if the computer is sitting at the login screen - I am unable to Remote control it.

So I have to physically go to the machine and log in to the desktop environment, then go back to my computer for VNC connection to it - lot of running around ( putting a damper on my experiments =)
total pain in the **** if I ever need to restart. 

dose anyone know a way around this problem ?

I am quite a bit more Mac savvy - so forgive me if this is a silly question

---

### Post by Zorgoth on 2010-08-04
I think you should be able to ssh in and run the command
'vncserver' -

If you need to configure any graphical stuff, you can use ssh -X as well as VNC - more secure, but you will have to use screen or & to keep something running after you quit your ssh session.

(and VNC is for sissies - ssh + screen ftw!)

---

### Post by kr651129 on 2010-08-04
> **Zorgoth said:**
> I think you should be able to ssh in and run the command
'vncserver' -

If you need to configure any graphical stuff, you can use ssh -X as well as VNC - more secure, but you will have to use screen or & to keep something running after you quit your ssh session.

(and VNC is for sissies - ssh + screen ftw!)

Don't forget it you are going to do that to make sure you have the ssh server daemon up and running on your server and that the firewall isnt blocking it

---

### Post by pipemartinm on 2010-08-05
Follow the instructions here: [http://ubuntuforums.org/showthread.php?t=122402&page=61](http://ubuntuforums.org/showthread.php?t=122402&page=61)

---

### Post by raysolomon on 2010-08-06
Or... use NoMachine NX instead of VNC
I found it to be quite better than vnc

[http://ubuntuforums.org/showthread.php?t=1546856](http://ubuntuforums.org/showthread.php?t=1546856)

---

