---
title: "Flash plugin - version confusion"
date: 2009-06-09
forum: General Help
---

### Post by Frogbarf on 2009-06-09
I'm having trouble with the Flash plug-in in Firefox. If I go into about:plugins, it says the Shockwave Flash plugin is version 9.0 r159, but in point of fact I have installed version 10 of Flash from the Adobe website at least twice. During the second install, the system remarked that I already had that version installed.

I'm trying to get a widget that depends on Flash and the Javascript evidently checks the Flash version and sees v.9..0.159. Also, if I right click a flash video it says v.9.0.159, and so does the Adobe website.

Checking in add/remove applications, I see Flash v.10 is installed, but I also see the installer for v.9

To summarize: I've installed Flash v.10 twice, but the system is still stuck on Flash 9. What to do?

Ubuntu 8.04
Firefox 3.0.10
Flash - two versions

---

### Post by michy99 on 2009-06-09
Have you rebooted? Sometimes firefox doesn't register changes until you do.

---

### Post by Frogbarf on 2009-06-09
Yes, I've repeatedly rebooted. Just tried a third install of Flash 10 making sure that no other user was logged on; same result.

And was very careful to shut down Firefox before installing the .deb package so no Flash was running on the system.

---

### Post by michy99 on 2009-06-09
If you put ```
about:plugins
``` in the url bar in firefox and press enter, what version of flash does it show?

---

### Post by Mirge on 2009-06-09
> **michy99 said:**
> If you put ```
about:plugins
``` in the url bar in firefox and press enter, what version of flash does it show?

Try about:robots

Sorry, couldn't resist :).

---

### Post by CaptainEvilStomper on 2009-06-09
Uninstall any Flash plugins you have installed, including the official Adobe ones. Once you've completely removed all your current Flash plugins, download the official Flash 10 .deb package from Adobe's site (if you haven't already) and install it. For some reason Firefox sometimes refuses to use the offical Flash 10 plugin if you have any other Flash plugins installed alongside it, so once you get rid of all the other ones it should work.

---

### Post by Frogbarf on 2009-06-09
> **michy99 said:**
> If you put ```
about:plugins
``` in the url bar in firefox and press enter, what version of flash does it show?

Shockwave Flash 9.0 r159

I'd already checked that.

Clearly there is version information stored in at least two different places. The installer thinks Flash 10 is already installed, but everything else thinks that Flash 9 is what I have. When I say "everything else", that includes Flash itself.

---

### Post by Frogbarf on 2009-06-09
> **CaptainEvilStomper said:**
> Uninstall any Flash plugins you have installed, including the official Adobe ones.

How do you uninstall Flash plugins?

Please be detailed: I don't do administrative work on my machine very often so I don't understand shorthand and technical terms.

---

### Post by Therion on 2009-06-09
Don't confuse Shockwave Player with Flash Player. 

To (ugh...) quote the horses mouth:

> Flash and Shockwave Players are both free web Players from Adobe. Together, they bring you the best rich media content on the Internet. Each has a distinct purpose. 
[B]
Flash Player[/B] delivers fast loading front-end web applications, high-impact web site user interaction, interactive online advertising, and short to medium form animation.

**Shockwave Player** displays destination web content such as interactive multimedia product demos and training, e-merchandising applications, and rich-media multi-user games. Through Xtras, Shockwave Player is also extendable to playback custom-built applications.

---

### Post by michy99 on 2009-06-09
> **Frogbarf said:**
> How do you uninstall Flash plugins?

Please be detailed: I don't do administrative work on my machine very often so I don't understand shorthand and technical terms.

From a terminal enter```
sudo apt-get remove adobe-flashplugin flashplugin-nonfree flashplugin-installer
```

---

### Post by Frogbarf on 2009-06-09
> **michy99 said:**
> From a terminal enter```
sudo apt-get remove adobe-flashplugin flashplugin-nonfree flashplugin-installer
```

I think I'm there. That sudo command got an error that it couldn't fint "flashplugin-installer", so I used the Synaptic package manager to sniff for all flash stuff.

Then reinstalled (fifth time now!) from the Adobe .deb file, fired up Firefox, checked about:plugins, and voila!

Thanks guys for your help.

---

### Post by CaptainEvilStomper on 2009-06-09
Or just open Synaptic (System > Administration > Synaptic Package Manager), type flash into the search bar, and hit enter. It'll list any packages with names that contain "flash" and in the description column it'll tell you whether they're Flash plugins or not. Uninstall anything that has a green box next to it (right-click, Mark for Removal). Once you've gotten rid of all of them, install the Flash 10 player from the offical deb file and see if it works.

EDIT: Never mind, looks like you figured it out.

---

