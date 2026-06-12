---
title: "Flash Player Firefox Plug-in install help"
date: 2009-04-15
forum: General Help
---

### Post by U-Bom-2 on 2009-04-15
Hi im trying to install the plug in for Firefox to see youtube videos and this is what i do
1) i go to get.adobe...ect and select .deb file for ubuntu 8.04+ (im using 8.04)
2) Download it and save it on my Desktop
3) Double click on it
4) a new window appear and is tell me the following error
   Status: Error: Dependency is not satisfiable: libpango1.0-0

After that i googled How to instal Flash player plugin in ubuntu and all this stuff, followed what the ppl sayd but none help me out. I think i have the default that you get with Ubuntu but it dont seems to work.

I apresiate any hjelp
Thanks

---

### Post by sahabcse on 2009-04-15
HI

type the following command in terminal

sudo apt-get install flashplugin-nonfree

Also You have to enable all the repositories in /etc/sources.list or synaptic package manager for solving dependency issue. Please refer following links for package management

[http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html](http://sahabm.blogspot.com/2009/01/package-management-debian-and-ubuntu.html)

---

### Post by Grievous on 2009-04-15
When I try the:
> **sahabcse said:**
> 
sudo apt-get install flashplugin-nonfree
, it says that newest version is already installed

But when I go to sites that requires flash player it still is saying that I need to download the latest version of flash player.

---

### Post by Grievous on 2009-04-15
I just downloaded the tar.gz file from adobe site and restarted my computer. After that it now works.  :lolflag:

---

### Post by Michael.Godawski on 2009-04-15
[CENTER][LEFT]hi,

taken from [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
perhaps it will work.

Once I had issues with flash I just fired up the first code line and it helped.
[/LEFT]
[SIZE=3][B][COLOR=DarkRed]
ADOBE FLASH PLAYER[/COLOR][/B][/SIZE][/CENTER]


On occasion, installing Adobe Flash Player and/or watching online Flash streams successfully isn't as simple as it might ordinarily be. If you have tried installing it already, and are having issues, read on. First of all, please disable any ad-blocking Firefox extensions you have installed, such as Adblock Plus, as they can sometimes interfere with the Flash content you actually want to see. If you are still having issues after disabling the extension(s), you should now completely purge Adobe Flash Player from your system, along with any other packages which may be interfering with it, reinstall only Adobe Flash Player, restart your web browser, and then test Flash performance again. Will both 32-bit and 64-bit users copy and paste this command into the terminal:

**sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree**

Still no joy? I would suggest following the instructions below for your particular Ubuntu version and architecture.


[CENTER]**[COLOR=DarkRed]UBUNTU FAMILY 8.04+ USERS ONLY[/COLOR]**[/CENTER]


**[COLOR=DarkRed]Note:[/COLOR]** You can safely install the Ubuntu package (flashplugin-nonfree), or a Deb archive over the top of the Tar installation method at a later date - I've tested it several times. There's absolutely no need to remove any of the manually installed files, as they will simply be overwritten.

First of all, copy and paste the following command into the terminal and remove the package installed by Ubuntu:

**sudo apt-get purge flashplugin-nonfree**

**[COLOR=DarkRed]32-Bit Users Only:[/COLOR]** Those of you running the 32-bit version of Ubuntu can install the Flash Player plug-in by selecting and downloading the Deb archive in the drop-down menu on [this page]("http://get.adobe.com/flashplayer/") of Adobe's site, then executing it and entering your root password when prompted.

**[COLOR=DarkRed]32/64-bit Users:[/COLOR]** Alternatively, 32-bit users can download the Tar archive from the [same link]("http://get.adobe.com/flashplayer/") provided above and follow my instructions below. If you're a 64-bit Ubuntu user, download the Tar archive of the 64-bit Flash Player plug-in from the bottom of [this page]("http://labs.adobe.com/downloads/flashplayer10.html") to your desktop.

Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then both 32-bit and 64-bit users execute the following command in the terminal:

**sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin && sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplayer-alternative.so**

You may now restart your web browser and use the plugin.

---

### Post by U-Bom-2 on 2009-04-15
> **Grievous said:**
> When I try the:
, it says that newest version is already installed

But when I go to sites that requires flash player it still is saying that I need to download the latest version of flash player.

Exactly that is what happen to me

I will try what Michael.Godawski say. and the i will post

---

### Post by U-Bom-2 on 2009-04-15
> **Michael.Godawski said:**
> [CENTER][LEFT]hi,

taken from [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
perhaps it will work.

Once I had issues with flash I just fired up the first code line and it helped.
[/LEFT]
[SIZE=3][B][COLOR=DarkRed]
ADOBE FLASH PLAYER[/COLOR][/B][/SIZE][/CENTER]


On occasion, installing Adobe Flash P.....

It don't help me :\
And i do everithing like here sayd

---

### Post by Michael.Godawski on 2009-04-15
Which version is shown when you type:

```
about:plugins
```

into the Firefox address bar?

---

### Post by U-Bom-2 on 2009-04-15
> **Michael.Godawski said:**
> Which version is shown when you type:

```
about:plugins
```

into the Firefox address bar?

Does not appear Adobe Flash Player plugin

---

### Post by nebileix on 2009-04-15
Try out this link.

[http://ubuntuforums.org/showthread.php?t=1123496&page=1]("http://ubuntuforums.org/showthread.php?t=1123496&page=1")

For ease of mind, please enable those third-party and restricted/non-free respository thru System-->Administration-->Software sources.

Gd luck.

---

