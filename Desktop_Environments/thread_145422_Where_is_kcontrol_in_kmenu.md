---
title: "Where is kcontrol in kmenu?"
date: 2006-03-16
forum: Desktop Environments
---

### Post by MichaelZ on 2006-03-16
Hello,

Sorry for the stupid question, but I cannot find kcontrol in my KMenu :(. I have started it the first time from the terminal by using sudo kcontrol (it worked even if I got error about uid :-?), but I would like to start it without the terminal. The problem is that I cannot find it.

Could someone tell me under whixh submenu it should be located?

Thank you very much :).

Best wishes,
Michael

---

### Post by Jucato on 2006-03-16
3 ways to run KControl without the terminal:
1. enter kcontrol in a Run command dialog box (Alt+F2); or
2. Add a K Menu entry for KControl (run kmenuedit); or
3. In the System Settings, choose the Panel under the Personal Group. Look for the Menus tab, and under the Optional Menus, check on Settings. This option will add a "Settings" group in the K Menu, where you can either launch the whole KControl or just the individual modules.

Just for added info. KControl (the official KDE Control Panel) was replaced by System Settings (the Kubuntu control panel project) as the default in Kubuntu.

---

### Post by MichaelZ on 2006-03-16
Hello,

Thank you very much :D. I will give it a try.

Best wishes,
Michael

---

### Post by treris on 2006-03-16
I'm actually still using kcontrol more than system settings,
there's just a whole lot of stuff missing from system settings, which, to me, makes it a lot less usefull than kcontrol

does anybody know whether system settings will ever have all the options of kcontrol??

---

### Post by Jucato on 2006-03-16
I have no idea either. For now, System Settings and Adept have a lot of catching up to do if they want to be on the same level of usability as KControl and KPackage/Synaptic.

---

### Post by beforewisdom on 2006-03-17
Are "System settings" and "adept"  ubuntu products?  If not, why make new things when kcontrol, kpackage managers do a better job/

---

### Post by Jucato on 2006-03-17
Yep, System Settings and Adept are **K**ubuntu-only projects.
Why make new things? Because they want to and they can? :D
But seriously, they might have a vision of a neat control center and package manager. But implementing that vision is another story. Anyway, these two apps are still very young. I might give them a try sometime, when they get past version 3.0 or something. But as it stands now, they just suck :D

---

### Post by Q4U on 2006-03-23
Agreed. Adept keeps freezing on me as I search packages. The info on the packages is not a thorough as the one provided by synaptic, too. But the interface is not so bad, after a while I got used to it.

And KControl interface might be a little chaotic, but it does what is supposed to do. System Settings looks a little like the Control Centre in Windows, but definitely does not provide the same level of fine-grained controls as KC. Q

---

