---
title: "Network Manager applet icon file location?"
date: 2009-12-14
forum: Desktop Environments
---

### Post by lee.colby on 2009-12-14
Being the customization junkie I am, I love tweaking my desktop in every aspect possible. I just recently began diving into icon customization, and love the humanity panel icons. I have customized most of my icons to display the humanity panel icons, even though I am using a different icon set (Simply Grey). My problem is with the network manager applet. I have tried countless times to locate the original icon file to override it with a humanity style icon, but can't seem to find it. I have managed to change the loading icon to humanity (the spinning circle), but not the ethernet connected or disconnected icon. I have searched endlessly in the hicolor icon folder for the corresponding icons, but no luck. I am inserting a screenshot of my desktop, and the icon I am referring to is on the top right corner of the screen, and its the white ethernet port with the blue cable. If anyone can give me some advice as to where to find the little bugger, I would greatly appreciate it. 
[IMG]http://i121.photobucket.com/albums/o212/leecolby/Screenshot.png[/IMG]

---

### Post by redman5087 on 2009-12-23
> **lee.colby said:**
> Being the customization junkie I am, I love tweaking my desktop in every aspect possible. I just recently began diving into icon customization, and love the humanity panel icons. I have customized most of my icons to display the humanity panel icons, even though I am using a different icon set (Simply Grey). My problem is with the network manager applet. I have tried countless times to locate the original icon file to override it with a humanity style icon, but can't seem to find it. I have managed to change the loading icon to humanity (the spinning circle), but not the ethernet connected or disconnected icon. I have searched endlessly in the hicolor icon folder for the corresponding icons, but no luck. I am inserting a screenshot of my desktop, and the icon I am referring to is on the top right corner of the screen, and its the white ethernet port with the blue cable. If anyone can give me some advice as to where to find the little bugger, I would greatly appreciate it. 
[IMG]http://i121.photobucket.com/albums/o212/leecolby/Screenshot.png[/IMG]
Also using the Simply Grey Icon.
Just the same problem, also trying to customize the icon.
Can not solve the problem, this look like a bug.

Any help, please

---

### Post by redman5087 on 2009-12-23
> **redman5087 said:**
> Also using the Simply Grey Icon.
Just the same problem, also trying to customize the icon.
Can not solve the problem, this look like a bug.

Any help, please
Possibly this could be fixed by adding nm dailies ppa: [https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

Upgrading to the latest network-manager solves the problem

---

### Post by redman5087 on 2009-12-26
> **redman5087 said:**
> Possibly this could be fixed by adding nm dailies ppa: [https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

Upgrading to the latest network-manager solves the problem

****, it brakes my internet connection, and when restarting , the icon problem is back

---

### Post by redman5087 on 2009-12-29
Seems impossible to fix,

Any help please

---

### Post by redman5087 on 2009-12-29
> **redman5087 said:**
> Seems impossible to fix,

Any help please

I copied all the icons from Humanity theme that are used for the network manager to the simply grey icon theme but it just won't work

---

### Post by redman5087 on 2009-12-30
Ha, Got it, it's within directory "devices" you need to change the icons

---

### Post by Ginsu543 on 2010-01-18
> **redman5087 said:**
> Ha, Got it, it's within directory "devices" you need to change the iconsI've been trying to solve the same problem. Could you tell me exactly which "devices" directory you're referring to? I'm using Mac4Lin icons and there are several "devices" folders inside the .icons folder Mac4Lin resides in. Any help would be much appreciated.

---

