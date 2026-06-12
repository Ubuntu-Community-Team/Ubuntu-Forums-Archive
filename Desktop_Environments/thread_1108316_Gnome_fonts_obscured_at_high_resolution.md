---
title: "Gnome fonts obscured at high resolution"
date: 2009-03-27
forum: Desktop Environments
---

### Post by nfnaaron on 2009-03-27
See attached screenClip.png.

Installed 8.10 (gnome), all looks great, except my laptop screen and my external screen are tied together.

Untied them using System/.../Screen Resolution, looks great-ish, but both screens are at 1024x768.

Used System/.../Screen Resolution to set both screens to their maximum:
LVDS: 1280x800 (laptop)
VGA: 1680x1050 (external LCD)

Looks great for awhile but then progressively deteriorates as shown in attached screenClip.png.

Note that for every obscured character, almost all instances of that character are obscured, and in exactly the same pattern.

And the longer you go, the more characters will be obscured.

Also if you go long enough the text in the menus in the panel will virtually disappear (can still faintly see them as ghostly grey/white), but will come back visible but still disfigured if you click on the menu. Same for menu sub-items.

Although it's not shown here, text within a web page IS affected.

Also, I'm pretty sure that text within a terminal window is NOT affected, but that's a three in the morning type of observation, and I'm on WinXP at the moment.

This does not happen in Kubuntu or Xubuntu, only Ubuntu. I'm not sure if dual screen is relevant, or if it's just high-resolution.

I also installed Fedora 10 in gnome and kde versions, and got the same results on Fedora gnome except worse and quicker.

No version of KDE, or Xubuntu, shows this problem with font degradation. Unfortunately I can't get dual screens working in [X|K]ubuntu.

None of the subpixel smoothing type of suggestions (fiddling with setting values) has any effect.

Here's what I have (info from WinXP System info):
Compaq Presario V6000 laptop.
Chip Type: Mobile Intel(R) 965 Exress Chipset family.
Memory Size: 128 MB
Adapter String: Mobile Intel(R) GMA X3100.
Bios Information: Intel Video BIOS.

External Monitor: Samsung SyncMaster 2053BW.

Laptop and External are both 32 bit color.

I would like to solve this but I have no idea where to look, I'm not familiar with Linux architecture.

Suggestions or pointers on how to solve or where to look? thanks.

---

### Post by nfnaaron on 2009-03-28
K', I still don't know what the cause of this is, but the solution is to upgrade to 9.04. I've been running the beta for a couple hours with high resolution dual monitors, and no blotchy fonts.

yay.

---

