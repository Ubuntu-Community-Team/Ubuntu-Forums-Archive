---
title: "A few questions regarding KDE4"
date: 2008-04-24
forum: Desktop Environments
---

### Post by reduxtion on 2008-04-24
I've recently upgraded to KDE4 and some things seemed to have changed so here it goes ...

1. Where do I go for manual network configuration? Clicking on "Manual Configuration" in KNetworkManager doesn't bring up anything.

2. What happened to the minimize all windows option? In the keyboard shortcuts, the only option is to minimize a single window.

3. How do I unlock the items in the panel so I can move them around?

That's it for now, I'm sure there are things I'll be back for.

Much thanks!

---

### Post by natman on 2008-04-24
1, for manual network config, after boot up to you notice a small icon ( like a white box with a thing at the corner - i know bad description ) in the taskbar near the clock, right click it and select manual config.

As for your other question, perhaps try "system setting"from the K menu.

---

### Post by onlinelli on 2008-04-24
2. What happened to the minimize all windows option? In the keyboard shortcuts, the only option is to minimize a single window.

It's afaik not implemented yet: But if you want to see what is on the Desktop, use the Strg+F12 shortcut to the dashboard. The way I've understood what plasma is going to be: They try to get rid of the Desktop as a pile of accumulating files and rather replace that space with an information management system. So there will be a widget showing "Desktop-Icons" for Quicklaunching, there'll be widgets showing folders (like the old desktop-concept) and widgets displaying any information you want: mail, dates, news, etc...
 
 3. How do I unlock the items in the panel so I can move them around?

That feature is also still missing. At the moment you just have to remove the item and then drag it from the "Add widget"  window to the place where you want it... But it should be implemented in KDE 4.1.

I hope it helped...

Cheers

---

### Post by reduxtion on 2008-04-24
Thanks for the replies guys.

> **natman said:**
> 1, for manual network config, after boot up to you notice a small icon ( like a white box with a thing at the corner - i know bad description ) in the taskbar near the clock, right click it and select manual config.

As for your other question, perhaps try "system setting"from the K menu.

Yeah, clicking on manual config doesn't seem to bring anything up. I'm guessing I'm missing a package to bring the config window up, but I have no idea what I'm missing,

Much thanks to both of you.

---

### Post by Nnexxus on 2008-04-27
Hi everybody !

I have the same problem here, about the network configuration tool.
I have just installed a Kubuntu 8.04 KDE4, from scratch, using the KDE4-only CD.
I can not access the network configuration tool. I can see the network icon in the panel, but when I click it and select 'manual configuration', nothing happens. It was the same when I tried the live-CD, I supposed it was because the system was not installed, but running it from the hard disk did not change anything.
I tried running Knetworkmanager from a console. When I click 'manual configuration', a message appears in the console : apparently, the system tries to run 'kcm_knetworkconfmodule' but this command does not exist.
I tried to manually download and install this package, from another computer : [http://packages.ubuntu.com/fr/hardy/kde/knetworkconf-kde4](http://packages.ubuntu.com/fr/hardy/kde/knetworkconf-kde4)
I installed it using dpkg, but nothing has changed.

As a desperate measure, I manually edited my /etc/network/interfaces, like on my good old debian, but it didn't work. I guess I did something wrong (my network config is pretty odd, as I'm behind a university proxy).

Do you have other suggestions ? Do you know how to manually run the knetworkconf-kde4 that I have just installed ?

Thanks, any help would be greatly appreciated.


:edit: I think I've found a quick'n dirty workaround : if you have access to the internet (via another computer, a dual boot...) you can download this package : [http://packages.ubuntu.com/fr/hardy/kde/knetworkconf](http://packages.ubuntu.com/fr/hardy/kde/knetworkconf)
It's the kde3.5 network configuration GUI. It seems that KDE4's Knetworkmanager is actually part of KDE3.5, and it tries to launch KDE3.5's network configuration GUI. At least, that's what I understood.

Once you have downloaded the .deb file and put it somewhere on your Kubuntu box, cd to the directory where you put the file and install it using 'sudo dpkg -i knetworkconf_3.5.9-0ubuntu5_i386.deb'. After that, you should be able to access the network config GUI. I have another problem past this point, but I think it's related to my network card.

---

### Post by maestrobwh1 on 2008-09-03
Knetworkmanager just seems fickle.

Install WICD...

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by super.rad on 2008-09-05
Since upgrading to 4.1.1 yesterday Knetworkmanager now works perfect for me (RT61 Wireless)
Also fixed a lot of other bugs I'd noticed such as trash widget not working.

---

