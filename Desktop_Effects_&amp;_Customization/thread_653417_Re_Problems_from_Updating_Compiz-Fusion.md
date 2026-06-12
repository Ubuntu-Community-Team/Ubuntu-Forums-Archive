---
title: "Re: Problems from Updating Compiz-Fusion"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by InfraredAnt on 2007-12-29
Hey [Lightangel]("http://ubuntuforums.org/showthread.php?t=653362"),

I too am having a similar problems...

If anyone can help, I would be most grateful. This is what basically happened...

Two new updates were made available for Compiz manager, which I was warned would not be supported...

I continued nonetheless and now I can't even get into the custom setting for visual effects :(

I tried to uninstall the program via add/remove and it did so without any problems...

Then I tried reinstalling through the same method, and it refused to install without the two "new" updates.

So now its back on Ubuntu 7.10 but I still have no visual effects whatsoever. :confused:

---

### Post by Sef on 2007-12-29
Moved to its own thread.

---

### Post by Sef on 2007-12-29
> Two new updates were made available for Compiz manager, which I was warned would not be supported...


How did you install those two updates?

---

### Post by InfraredAnt on 2007-12-30
Well... The two updates were installed through the update manager.

see the screenshots for package details etc.

If I try to download the packages instead. I get a notification of a failed installation.

---

### Post by Ub1476 on 2007-12-30
I guess you installed Compiz-Fusion 0.62 from backports. The first thing you do is to go into System>Administration>Software Sources and uncheck "backports". After that is done, open Synaptic, System>Administration>Synaptic packagemanager, and search for compiz. Uncheck those which are version 0.62 (compiz and compiz-fusion-plugins-extra I believe), and uninstall them. Finally, open a terminal and "repair" Compiz-Fusion by reinstalling ubuntu-desktop:

```
sudo apt-get install ubuntu-desktop --reinstall
```

---

### Post by Forlong on 2007-12-30
If it's still not working, post your /etc/apt/sources.list
You may have sources for feisty in there.

---

### Post by InfraredAnt on 2007-12-31
Thanks for the help guys,

but I still have had no luck... 

I did what you said Ub1476, and by also removing third party sources.

e.g.
[http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb)

Compiz Manager was able to reappear when I had reinstalled it... However, all I got was an empty window. (see screenshot).

Even so, when I try to use these sources, compiz manager doesn't respond at all... 

I presume I need the sources for gutsy gibbon...

Anyhows, Forlong, here is my sources list also as requested.

---

### Post by Forlong on 2007-12-31
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)


P.S. please don't upload any text documents with outputs in the future - particularly no doc files.
You can either post long outputs here using the CODE tags or a service like [http://pastebin.com](http://pastebin.com)

---

### Post by InfraredAnt on 2007-12-31
Hi Forlong,

Sorry about that, I'm a bit new to forums.

Anyhows, here is the output

```
rc  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1  OpenGL window and compositing manager - GNOM
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  libcompizconfig-backend-gconf              0.6.0~git20071003+3v1ubuntu0         GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings

```

many thanks

---

### Post by InfraredAnt on 2008-01-01
thanks forlong... 

I checked out your blog and appears that something has worked....

compiz is working again... but not as ccsm but as advanced desktop effects settings..

I will take that as an equivalant... and it works just as well...

---

