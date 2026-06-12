---
title: "icons to display the current network connecting status?"
date: 2008-07-29
forum: Desktop Environments
---

### Post by chunchengch on 2008-07-29
I notice that no matter what icon theme I install, the network manager applet (nm-applet) icon always remains the same without changing different icon with different network connecting status. 

I can find icons of network-offline.png, network-idle.png, network-receive.png and network-transmit.png etc in the theme, but it seems that only the network-idle.png icon is used, so I wonder if there is any way to use all these icons to display the current network connecting status?

Thanks for reply.


[ATTACH]79309[/ATTACH]

[ATTACH]79310[/ATTACH] [ATTACH]79311[/ATTACH] [ATTACH]79312[/ATTACH] [ATTACH]79313[/ATTACH]

---

### Post by nikgare on 2008-07-29
You need to add **Network Monitor** to the Panel

---

### Post by chunchengch on 2008-07-29
> **nikgare said:**
> You need to add **Network Monitor** to the Panel

Thanks for reply, 

I know this applet, but my question is the default nm-applet (version 0.6.6) in Hardy does not indicate the network connection status, can this be fixed? I don't want to have two network applets on the panel.

---

### Post by NilsE on 2008-07-29
The icons used by nm-applet is in the following folder (substitute ThemName for the name of the icon theme you are using

/usr/share/icons/ThemeName/24x24/status

or

/usr/share/icons/ThemeName/scalable/status

The can also be in you home directory .icons depending on how you installed them.

I believe they are the ones starting with nm-signal or gnome-netstatus but I the sure the nm- ones are correct

Here are the scalable ones I created

---

### Post by nikgare on 2008-07-29
Now I understand your question - but I have no idea!

Presumably it could be done, because when it shows a wireless connection, it changes according to the streangth of the signal.
Maybe you could try reporting this as a bug or request in launchpad?

---

### Post by chunchengch on 2008-07-29
> **NilsE said:**
> The icons used by nm-applet is in the following folder (substitute ThemName for the name of the icon theme you are using

/usr/share/icons/ThemeName/24x24/status

or

/usr/share/icons/ThemeName/scalable/status

The can also be in you home directory .icons depending on how you installed them.

I believe they are the ones starting with nm-signal or gnome-netstatus but I the sure the nm- ones are correct

Here are the scalable ones I created


yes, there are gnome-netstatus-xxx icons in the ~/.icon/ThemeName/24x24/status, and you can find some of these icons in my first post.

---

### Post by chunchengch on 2008-07-29
> **nikgare said:**
> Now I understand your question - but I have no idea!

Presumably it could be done, because when it shows a wireless connection, it changes according to the streangth of the signal.
Maybe you could try reporting this as a bug or request in launchpad?

That is what I am wondering why the applet indicates real-time status of wireless connection, but does not in wired connection?

I had reported this bug in Gnome launchpad just couple of minutes ago.

---

### Post by NilsE on 2008-07-29
> **chunchengch said:**
> That is what I am wondering why the applet indicates real-time status of wireless connection, but does not in wired connection?

I had reported this bug in Gnome launchpad just couple of minutes ago.
I have to learn to read better in the mornings HaHa

I thought you said the wireless ones were not changing.  I think you bug will come back as a dup since I know there are others on this from when I looked at it way back when.

---

