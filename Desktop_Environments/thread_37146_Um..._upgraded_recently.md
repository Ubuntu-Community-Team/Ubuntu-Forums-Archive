---
title: "Um... upgraded recently?"
date: 2005-05-26
forum: Desktop Environments
---

### Post by philipacamaniac on 2005-05-26
Okay, I've been trying to defend the Kubuntu devels quite a bit on these forums. But I can't anymore, I don't think.

I just upgraded to the latest Hoary bugfixes/security updates (I presume, because I don't have Breezy/Marillat/Backports enabled). The knetworkconf package won't install (I already filed a bug), and when I logged back in, the K-Menu looked funny! It lost all of its top-level menu icons, and two new menus appeared: Information and Settings (I think it was Settings - I already deleted it, so I can't remember). No prob, I just went through and reassociated various icons.

But then I opened the Control Center, and someone thought it would be funny to reorganize it!! Again here, the top-level menu icons are gone, and it is now organized like so (I'm not making this up, folks!):

Accessibility
Components
Desktop
LookNFeel (sic)
Network
Peripherals
PowerControl
Security
Sound
System

I FEEL LIKE I'M TAKING CRAZY PILLS! Seriously, I only have Hoary, updates and security (main restricted universe multiverse) enabled. So this came from our friendly neighborhood Kubuntu packagers... what are they smoking? You can't change the heirarchy of something as important a control panel, especially mid-release. 

Seriously, that *really* should have waited until Breezy and/or KDE 3.5.
</soapbox> ](*,)

EDIT: Ehh.... the Info Center doesn't work anymore! (/usr/bin/kinfocenter)
EDIT AGAIN: Reinstalling kdebase will fix kinfocenter...sigh...

---

### Post by philipacamaniac on 2005-05-26
It should be noted that I still support the Kubuntu effort...

---

### Post by philipacamaniac on 2005-05-26
Okay, forget everything I said. Once I reinstalled kdebase, the Control Center and Info Center went back to normal. And that was AFTER I removed Backports and Marillat repos.

I don't know where the disheveled Control Center came from, but I'm still investigating. Sorry for freaking out, and all...

---

