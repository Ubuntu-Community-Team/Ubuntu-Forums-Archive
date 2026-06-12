---
title: "Customise Netbook Remix Launcher Interface"
date: 2008-08-03
forum: Desktop Environments
---

### Post by elaverick on 2008-08-03
Does anyone know if it's possible to customize the folder shortcuts on the right hand side of the netbook remix launcher?  I notice it picks up hotplug drives such as card readers or usb pen drives, it would be nice to be able to add links to my videos or my upnp share from my Vista machine.

---

### Post by Krydahl on 2008-09-28
Did you ever find an answer to this? 

Somehow I don't think I'm going to be storing many videos on my eee. I thought deleting the directory would remove the shortcut, but no such luck.

---

### Post by glombo on 2008-11-15
As far as I am aware, the location links on the right hand side of the launcher are the same as those seen in Nautilus.
So to change the launchers, simply go into the file manager and:

To remove the netbook-launcher, right click on the same launcher in the left had side of the file manager and click remove.
[IMG]http://glombek.co.uk/joe/remove-launcher.jpg[/IMG]

To add a location to the netbook-launcher, drag and drop a file or folder over to the left hand pannel.
[IMG]http://glombek.co.uk/joe/add-launcher.jpg[/IMG]

It's that simple, I think!

You may have to log out and back in again for the changes to take effect or at least restart netbook-launcher.

Hope it helps!

Glombo

---

### Post by milko on 2008-12-02
It wasn't quite so simple for me, I wanted rid of the Pictures shortcut (since another app had created a Photos one I preferred to use). Although it wasn't in the places tab it still appeared in the launcher. I got it in the Bookmarks menu though, still in Nautilus.

---

### Post by tamias on 2009-01-19
Milko: You can edit .gtk-bookmarks in your home directory to remove references to entries which shouldn't be in there. It's a known bug ([https://bugs.launchpad.net/netbook-remix-launcher/+bug/310743/]("https://bugs.launchpad.net/netbook-remix-launcher/+bug/310743/")) which should hopefully be fixed soon.

---

### Post by viewfrom102 on 2009-05-27
On a similar note, does anyone know how to move/remove the other preset locations in this part of the launcher?

Typically this is the "Home", Desktop" and "Network" links. The fixes outlined above only deal with the bookmarks below them (and any mounted drives).

---

