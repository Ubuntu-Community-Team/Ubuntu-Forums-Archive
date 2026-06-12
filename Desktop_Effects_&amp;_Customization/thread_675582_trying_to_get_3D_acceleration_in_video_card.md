---
title: "trying to get 3D acceleration in video card"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by girtart3d on 2008-01-22
ok im following these instructions





1.

Install the xorg-driver-fglrx package from the Restricted repository (see Chapter 2, Adding, Removing and Updating Applications).
2.

You now need to configure the computer to use the new driver so run this command in a terminal:

sudo dpkg-reconfigure xserver-xorg

3.

When the dialogue appears and asks whether to do automatic detection of your video, pick Yes.
4.

When asked to select a driver, pick fglrx.
5.

Follow the remaining instructions as appropriate.
6.

Restart your machine for changes to take effect.



well i installed the driver from synaptic . and when i run the sudo dpkg-reconfigure xserver-xorg command. i get this error
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
i was able to access it before but after i installed the driver i got the message. i uninstalled it again but i still get the error. anyone know what it might be? im using xubuntu 7.10

---

### Post by girtart3d on 2008-01-23
well i fixed it. but when i change it to fglrx and restart it i get a seizuring black and white screen at start  up . and i tried all the different resolutions. and it only worked when i put it back to the original card thing wich is 'intl' or osmething. so il just forget about it.

---

