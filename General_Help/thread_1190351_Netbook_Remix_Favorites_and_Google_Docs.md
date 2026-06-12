---
title: "Netbook Remix Favorites and Google Docs"
date: 2009-06-17
forum: General Help
---

### Post by WaRrK on 2009-06-17
Hi,

I've installed a fresh copy of 9.04 Ubuntu Netbook Remix today. I've installed Google Gears to allow me to use Google Docs off-line in firefox and doing this has created an icon in my Desktop folder.

I've been trying to get that icon into my favorites section on the netbook launcher pannel thingy but haven't had much luck. The icon is called "Google Docs.desktop" and when I open it in a text editor it has the shebang line of #!/usr/bin/env xdg-open 

How do I get this into my favorites?

Cheers
Ash

---

### Post by WaRrK on 2009-06-19
I'll answer my own question given I've found how to do it!

1) Let Gears create the link on your desktop
2) Copy this link to /user/share/applications (NB you'll probably need to sudo it)
3) This will now appear in the "Other" section in the launch manager
4) Go to Preferences > Main Menu in the launcher
5) Move the link to Google Docs from Other to Office
6) Untick or delete the option in Other
7) From the Launcher drag the icon to your favourites!

-Ash

---

