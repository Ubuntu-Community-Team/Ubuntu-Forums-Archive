---
title: "No &quot;Visual Effects Tab&quot; Preferences&gt;Appearance"
date: 2009-02-14
forum: General Help
---

### Post by YWELLC on 2009-02-14
Recent purchase of Dell mini pre-loaded with 8.04.  I am, like everyone else, trying to enable the compiz effects.

I discovered that under System>Preferences>Appearance I do not have a "Visual Effects" tab which would allow me to enable the custom setting (I think I have all the other requisite packages to do so).

These are the tabs available in that context menu: Theme, Background, Fonts, Interface.  

On my desktop running 8.04, the tab is there and everything is working flawlessly.  I have searched and read the FAQ about desktop effects but can't seem to find anyone reporting the tab completely missing.

Any help would be greatly appreciated!

---

### Post by YWELLC on 2009-02-17
Bump...

Still no ideas :(

---

### Post by Slim Odds on 2009-02-17
You need to use proprietary drivers to get the "special effects".

Look under: System>Administration>Hardware Drivers

---

### Post by Therion on 2009-02-17
Open Synaptic Package Manager
Search on, and install, **compizconfig-settings-manager** 
CCSM will be located under System/Preferences/Advanced Desktop Settings

Or you can use the Terminal:```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by YWELLC on 2009-02-17
Checked on the proprietary drivers - already enabled (came that way from Dell).

Also, I have the newest version of compizconfig-settings-manager.  The computer came out of the box with it installed.  The tab was no there, so I also installed the simplecompiz config setting manger, required in 8.04 to enable the "custom" setting in the visual appearances tab.

Still the tab just isn't there, but thank you for the responses!

---

### Post by dcstar on 2009-02-17
> **YWELLC said:**
> Checked on the proprietary drivers - already enabled (came that way from Dell).

Also, I have the newest version of compizconfig-settings-manager.  The computer came out of the box with it installed.  The tab was no there, so I also installed the simplecompiz config setting manger, required in 8.04 to enable the "custom" setting in the visual appearances tab.

Still the tab just isn't there, but thank you for the responses!

And of course, all the required compiz packages are actually installed?

---

### Post by YWELLC on 2009-02-18
From what I've read elsewhere I believe so.  Though it wouldn't be unreasonable to assume whom/whatever did my install didn't get all the dependencies.  

Do you have/can you point me to a list of them so I can check off what I have - or do you think I would be better off removing all of the compiz packages completely and re-install manually?

It seems everything else is setup to work properly, just can pinpoint what I need to get the tab in there.  I was thinking perhaps it could be hardware related, maybe the video card isn't up to snuff?

---

### Post by philinux on 2009-02-18
Dell probably installed a customised Ubuntu. The missing tab maybe means the graphics card can't do compiz.

---

### Post by YWELLC on 2009-02-23
Still having the same problem, I'm going to post this to the Dell forums.

Thanks for the help.

---

### Post by soaham on 2009-02-23
I just talked with Dell support and was told that the Version of OS installed on the Mini is customized by canonical and will not give us the "Visual Effects" tab.  
This sucks !  I have installed compiz-* and the fusion-icon* still no luck :(

I get System --> Preferenes --> Advanced Desktop Visual Effects" but nothing changes... the Appearance tab still does not have visual effects.

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Slim Odds on 2009-02-23
Have you checked this out?

[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

