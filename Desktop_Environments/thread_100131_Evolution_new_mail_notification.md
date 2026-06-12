---
title: "Evolution new mail notification"
date: 2005-12-06
forum: Desktop Environments
---

### Post by gregh on 2005-12-06
I came accross this panel-applet called em-panel-notify 
[http://www.warma.dk/ubuntu/em-panel-applet/em-panel-applet_0.2-2_i386.deb](http://www.warma.dk/ubuntu/em-panel-applet/em-panel-applet_0.2-2_i386.deb)

That will not install on Breezy as it complain about missing libdbus-1.so.0
(I created a symlink from libdbus-1.so.1 but that did not work)

This panel applet appears to be a method to get Evolution notify you when it receives email via dbus in much the same way outlook notifyds in the system tray in windows.

The mail-notify program in the repositories is not really what I am after as its a seperate application and I would rather something intergrated to Evolution (using the dbus system)

Anyone throw any more light onto this?

-Greg

---

### Post by santo on 2005-12-19
I'm interested in this as well.
Maybe we should just compile the sources ourselves ?

they can be found right here: [http://mail.gnome.org/archives/evolution-hackers/2005-April/msg00044.html](http://mail.gnome.org/archives/evolution-hackers/2005-April/msg00044.html)

---

### Post by santo on 2005-12-19
hmmm, I just tried to get those sources installed, but they too complain about a wrong version of dbus.

after I told it to use my currently installed dbus version (0.36.2-0ubuntu7), it complained about "DBUS_INTERFACE_ORG_FREEDESKTOP_LOCAL":

> 
em-panel-applet.c:55: error: &#8216;DBUS_INTERFACE_ORG_FREEDESKTOP_LOCAL&#8217; undeclared (first use in this function)


it appears this was available in an older version of dbus but not the more recent ones (which is used in Breezy) :-(

---

