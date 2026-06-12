---
title: "No Automount in KDE installed in Ubuntu, how to enable?"
date: 2005-07-05
forum: Desktop Environments
---

### Post by preptheshipfortakeoff on 2005-07-05
**No Automount in KDE installed in Ubuntu, how to enable?** 

Hello fellow Ubuntu & Kubuntu users. I hope this message reaches you well. Let me start this post with a thank you for your time in reading this message.

I have installed Ubuntu Hoary Hedgehog 5.04 and followed the installation with downloading and installing KDE through the Synaptic program. I enjoy loading Gnome and KDE and other window managers. My problem is when I login to KDE it does not want to automount CD or DVD drives, but Gnome does.

What are the instructions please on setting KDE to automount CD and DVD drives automatically so I do not have to manually mount the drives each time I login and desire to use these devices?

I am not using Kubuntu and switching is not possible at the moment with a slow modem. Please help me I thank you kindly for your attention to this message and my plea.

---

### Post by ltmon on 2005-07-05
Did you install the "kde" package from synaptic or the "kubuntu-desktop" package.  If install "kde" you may be missing some settings that come with "kubuntu-desktop".  

I'm not sure of this, but just a thought.

Try:

> sudo apt-get install kubuntu-desktop

if you haven't already installed it.

L.

---

### Post by aragorn2909 on 2005-07-05
On my Kubuntu only system, the only cd/dvd devices that are automounted are those containing dvd media and k3b data disks.  Everything else I mount through Konquerer.  I suppose you could install the autofs package through synaptic, or the gnome-volume-manager package for automount and autorun features, although I have not tried either.

---

### Post by ltmon on 2005-07-05
[QUOTE=aragorn2909]On my Kubuntu only system, the only cd/dvd devices that are automounted are those containing dvd media and k3b data disks.  Everything else I mount through Konquerer.  I suppose you could install the autofs package through synaptic, or the gnome-volume-manager package for automount and autorun features, although I have not tried either.[/QUOTE]

gnome-volume-manager will be no help for kubuntu.  Also I don't have autofs installed, and everything works.

Weird though... all my stuff (camera's, cd/dvd, usb storage) automounts with no tweaking.

Reading up on the KDE wiki the relevant technologies seem to be HAL and D-BUS.  Make sure the following are installed

sudo apt-get install hal
sudo apt-get install dbus

If there's nothing still appearing on your desktop, make sure you check the "Storage Media" entry in the System menu (next to the K menu), or simply type "media:/" into the konqueror address bar.

L.

---

### Post by DarkMind on 2005-07-06
[QUOTE=ltmon]gnome-volume-manager will be no help for kubuntu.  Also I don't have autofs installed, and everything works.

Weird though... all my stuff (camera's, cd/dvd, usb storage) automounts with no tweaking.

Reading up on the KDE wiki the relevant technologies seem to be HAL and D-BUS.  Make sure the following are installed

sudo apt-get install hal
sudo apt-get install dbus

If there's nothing still appearing on your desktop, make sure you check the "Storage Media" entry in the System menu (next to the K menu), or simply type "media:/" into the konqueror address bar.

L.[/QUOTE]
 install ivman it's a great automount, not need configuration, it' very easy to install :)

---

### Post by varunus on 2005-07-07
You said you had both KDE and gnome installed?  well, you can then set KDE up to load "gnome-volume-manager" as a startup program.  It works exactly the same way in KDE as it does in GNOME (I've done it before).  Your drives will be automounted the same way.  (This isn't the *right* way to do this, but it'll work.)

---

