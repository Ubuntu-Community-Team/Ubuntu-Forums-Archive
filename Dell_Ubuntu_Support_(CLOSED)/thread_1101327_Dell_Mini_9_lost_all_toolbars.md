---
title: "Dell Mini 9 lost all toolbars"
date: 2009-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by merriww on 2009-03-20
I have managed to lose all my toolbars on my Dell Mini 9 running Intrepid.  I was switching between the default Ubuntu Gnome desktop and Ubuntu Netbook Remix when this problem occurred using the Desktop switcher app.  All my desktop shows right now is the my deskop icons with the default Intrepid desktop background.  No toolbars at all are available so I can't reboot or shutdown via mouse or start any programs. I'm sure there is a way to start terminal via key sequence but I don't know what that is.  Can anyone provide guidance on how to proceed?

Thank you
Wayne

---

### Post by jespdj on 2009-03-20
With Alt + F2 you can run a command. To start a terminal, type Alt + F2 and run the command **gnome-terminal**.

Maybe you can right-click on the desktop to add a new GNOME panel. Then right-click on the panel to add stuff like the menu, notification area etc.

---

### Post by jaqrah on 2009-03-20
merriww

I could point you to various threads where people were using Desktop Switcher app on their Mini 9 in conjuction with Netbook Remix.

I had one of those threads.  I lost my entire desktop and despite many different attempts to recover it.  I eventually did a clean install because I needed my mini for a trip.

Try the following link.  It explains how to reset your Xorg.  Note, this fix did not work for me or a couple other people.

[http://www.ubuntumini.com/2009/02/repair-broken-xorg-file.html](http://www.ubuntumini.com/2009/02/repair-broken-xorg-file.html)

good luck

---

### Post by Ryback on 2009-03-21
This also happened to me, but while running Dell's supplied version of Hardy - I had to recreate all my taskbars from scratch after applying the desktop switcher.  I think at the moment (as my mini 9 is my only comp, as I'm on the road) it's just a matter of picking either the Netbook Remix desktop, or the regular, and sticking with it.  But I'm glad to see this isn't just a problem with Dell's distro - now there's an even greater chance of it being fixed!

Unfortunately I don't have access to a clean testing environment at the moment, but if someone else does a bug at [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) would be a good start.

---

