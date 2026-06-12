---
title: "IPP and HPLIP"
date: 2005-12-16
forum: Desktop Environments
---

### Post by eeclark on 2005-12-16
When you enter a URI during the creation of the printer, it appears all well and good. For example, if you put in hp:/net/psc_2500_series?ip=192.168.1.97 in the IPP field, it will appear as you typed it. BUT IF YOU SAVE YOUR CHANGES (click close) and then GO BACK to view the connection properties, ipp:// is now inserted in front of the hp:/ .

In other words, when I create a printer and enter the URI...the system wants to insert a prefix of ipp:// in front of hp:/

I guess the thing to do is to find out what is generating the "ipp://" and take that out...but that is beyond me.

Could this be a Gnome Desktop issue?

---

### Post by eeclark on 2005-12-16
I also noticed that if the printer is created in the CUPS interface ([http://localhost:631](http://localhost:631)) you do not see the problem of autopopulating IPP.

It only happens in the gnome-cups-manager.

---

### Post by hajk on 2005-12-16
I've experienced similar problems, and sometimes I could install my printer the Ubuntu way via System/Administration/Printing, and sometimes I couldn't. So, just to make sure that I'm giving you correct advice, I deleted my printer and tried to install it anew via System/Administration/Printing. And sure enough, it would not install, insisting on putting an extra "ipp://" in front of my special
hp:/net/deskjet... URI, just like you experienced.

Now, I'm happy to say that the following DID work to circumvent the Ubuntu setup:

1. Edit /etc/cups/cupsd.conf and comment out the two lines
    "AuthType Basic'' and "AuthClass System'' near the end of the file.
2. Run the command "sudo /etc/init.d/cupsys restart".
3. Log in to [http://localhost:631](http://localhost:631) (you don't need a password).
4. Install the printer: give it a name; choose AppSocket/HPJetDirect and
    enter your special hp:/net/... URI; choose manufacturer HP (HPLIP), 
    select your printer from the list, and accept the recommended driver.

The printer is now installed, but you may have to "configure" it (choosing paper size, etc). Printing a Test Page should now be OK (it was for me).

Finally, log out of [http://localhost:631](http://localhost:631) and (possibly) reverse the changes to /etc/cups/cupsd.conf (and restart cupsys).

I hope it works for you. :D

---

