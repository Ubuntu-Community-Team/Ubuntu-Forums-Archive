---
title: "Ubuntu now has Xubuntu shutdown screen"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Zill on 2006-09-08
I recently installed Xubuntu in addition to Ubuntu.  This changed the logon screen to default to Xubuntu but I changed that back to Ubuntu via the Admin Login Window menu.
However, on shutdown Ubuntu goes into the blue Xubuntu shutdown screen and logo.  Which file do I need to edit, or GUI menu item, to always default to the Ubuntu shutdown screen?
I don't want to uninstall Xubunu, just to keep it as an option to Gnome :-)
Many thanks.

---

### Post by orb9220 on 2006-09-08
No prob just open a term and

sudo update-alternatives --config usplash-artwork.so

and chose

---

### Post by Zill on 2006-09-10
Many thanks Orb - it worked like a charm :-)
Now please let me in on the secret - how does it work and where is it documented?
Thanks again.

---

### Post by elettronicha on 2006-09-10
> **Zill said:**
> how does it work and where is it documented?
Thanks again.
```
man update-alternatives
```

So you tell the system which splash-screen the symbolic link usplash-artwork.so points to. ;)

---

### Post by oswaldkelso on 2006-09-10
Thankyou I needed that info too.

---

### Post by Zill on 2006-09-10
Many thanks for the info.  I have been using Mandriva and Ubuntu for a few years now and know about the Man pages but still have trouble finding info on some of the more "obscure" commands.  It isn't always clear exactly what apps are in use and what commands need to be looked up.
Anyway, this is another one for my logbook and I really appreciate the help from all you gurus out there.  Please keep up the good work :-)
Best wishes.

---

### Post by sshahir on 2006-09-10
Can you please let me know more about Xubuntu?

Should I down load it?

When I try the following command, a message says 

>[COLOR="Blue"]sudo update-alternatives --config usplash-artwork.so[/COLOR]
>[COLOR="Red"]There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.[/COLOR]

---

### Post by Zill on 2006-09-10
[http://www.xubuntu.org/](http://www.xubuntu.org/)
Xubuntu is aimed at improving the performance of old or low-end machines.  You decide if you need it!  If you want to try it then install xubuntu-desktop (and related files) via (for example) the Synaptic package manager.
Be warned that this will change your default start up logon screen and shutdown screens from Ubuntu to Xubuntu.  The logon screens can be easily changed back via the Ubuntu menu option System, Admin, Login Window.  The shutdown screens can be changed back via the instructions kindly supplied in this thread.
Hope this helps.

---

