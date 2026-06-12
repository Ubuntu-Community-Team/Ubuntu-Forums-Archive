---
title: "new updates for compiz fusion..how safe?"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by bigbrovar on 2007-08-28
just got notification that new updates are avialable for compiz fusion..how safe is it to install..? am scared nowadays of updates the last one was cool but i can still rememer the time when things went heywire.any way is it safe?

---

### Post by Magneticgravity on 2007-08-28
Well i just installed them, and Ubuntu kept freezing, lol.

---

### Post by -SpaZ on 2007-08-28
My general rule is that I wait a week to install updates for my apps unless they are just security updates.  That way I can see what everyone thinks and see if there are any problems with the update.

---

### Post by michael37 on 2007-08-28
Upgrade to 0.5.5 broke window decorations for me.  Just FYI

---

### Post by bigbrovar on 2007-08-29
well i guess i will just have to wait...just so annoying when the notificatiom pops-up everytime i do a restart..grrrhhh

---

### Post by cudaman73 on 2007-08-29
Supposedly, the way to get 0.5.5 working properly is to do a complete uninstall and reinstall.

Claims have been made that some of the old config settings is what is breaking the new compiz, but I have no idea whether or not that's true.

EDIT: Also, you can disable your compiz repos after you get everything installed and working to get rid of the annoying 'there are updates available' popup. Just FYI.

---

### Post by bigbrovar on 2007-08-29
> **cudaman73 said:**
> Supposedly, the way to get 0.5.5 working properly is to do a complete uninstall and reinstall.

Claims have been made that some of the old config settings is what is breaking the new compiz, but I have no idea whether or not that's true.

EDIT: Also, you can disable your compiz repos after you get everything installed and working to get rid of the annoying 'there are updates available' popup. Just FYI.

thanks man..i have heard the same uninstall and reinstall claim. but am not down with all that stress..i will just keep ignoring the pop up...

---

### Post by jhernandez1270 on 2007-08-29
I've got the latest version from Trevinos repo installed (no more pop-ups) and it fixed pretty much everything that was screwed up on my laptop. (ie 3D window, cube, settings in CCSM, etc.)

BTW the version I have is 0.5.2 in CCSM Click Preferences -> About CCSM...  to get the version you are running.

---

### Post by AndrewGene on 2007-08-29
The newest update recieved made my windows very transparent (not my menus though).  I tried clicking on them, holding alt and scrolling up (to make them less transparent) but it doesn't work.

---

### Post by Inxsible on 2007-08-29
> **cudaman73 said:**
> Supposedly, the way to get 0.5.5 working properly is to do a complete uninstall and reinstall.

Claims have been made that some of the old config settings is what is breaking the new compiz, [COLOR=Red]but I have no idea whether or not that's true.[/COLOR]

EDIT: Also, you can disable your compiz repos after you get everything installed and working to get rid of the annoying 'there are updates available' popup. Just FYI.
Oh its true alright !!

until 0.5.2 compiz settings were stored in /home/.compizconfig. From 0.5.5 they are now stored in /home/.config/compiz. also not all packages were updated to use the 0.5.5 and so there was a mish mash of packages - some trying to look for settings in .compizconfig and other trying to look in .config/compiz leading to all the hassle.

So yes, a complete uninstall (including removing all traces) and then a re-install does help.

I use 0.5.5 using Trevino's repos and have no issues now.

---

