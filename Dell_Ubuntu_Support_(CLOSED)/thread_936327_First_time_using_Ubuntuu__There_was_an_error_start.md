---
title: "First time using Ubuntuu : There was an error starting the GNOME settings Daemon"
date: 2008-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tikigod13 on 2008-10-02
Hello, I'm kinda a Linux Noob so if anyone can help me it would be much appreciated. I have the boot CD in my Dell inspirion 1100 and i get into the linux desktop but an error messege at the top left of the screen and i can't move the mouse. It says > There was an error starting the GNOME Settings Daemon.
Somethings, Such as themes, sounds, or background settings may not work correctly.

The last error messege was:

Did not recive a reply. Possible causes include: the remote application did not send a reply, the messege bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.


I wish I knew what this meant, but I'm afraid I don't hehehe. Does anyone know what I can do to get Linux to work?

---

### Post by shae on 2008-10-04
On occasion the Gnome settings manager will fail to start.  On later versions of gnome this almost never happens.  To fix it simply restart.  If you get this every time you restart, you are likely suffering from a corrupted install and should reinstall or you were messing with what services and things start up and disabled something important.

---

### Post by terry_gardener on 2008-10-04
quick fix for this is to restart x server, press ctrl+alt+backspace 
then logon. 

if this happens everytime you logon or bootup the system then the instructions in the following link. 

[http://ubuntuforums.org/showthread.php?t=395456](http://ubuntuforums.org/showthread.php?t=395456)

---

### Post by biggman100 on 2008-12-13
I tried ctrl+alt+backspace and nothing happened, so i hit ctrl+alt+f1 and watched it go through its load-up, and everything said ok, but it still gives me the same error everytime i start.

---

### Post by falcon61102 on 2008-12-15
You may have a corrupt CD.  Next time you boot from the CD, select Check CD and let it run the test on the CD.  If it somes back good and continues to give you that error, you can try starting up in a Safe mode.  Hit F4 at the CD boot screen and it will allow you to select a few options that may help.

---

### Post by mbert on 2008-12-20
I had the same issue with clean install of 8.04 this week. 

Turns out it was a networking error.  My firewall was supplying the wrong IP to my internat DNS server. 

Once I fixed the dns issue, the GNOME error disappeared.

---

