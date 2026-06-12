---
title: "Mail Reader main menu entry missing icon"
date: 2012-03-24
forum: Desktop Environments
---

### Post by ccrs8 on 2012-03-24
I'm running Xubuntu 11.10 and loving it (didn't like Unity).  I've gotten XFCE working just like Gnome2.  I have one super-minor nagging issue that I'd love to get fixed.  In the Appearance settings section, I'm using the "Xfce" style with the "Humanity" icons.  I chose this set of icons because it is the only set of icons that I could find that would visually tell me that I was logged on to my company's VPN (using openconnect) via the network manager icon.  But this set of icons has no icon for the "Mail Reader" main menu entry, so it just uses the black box with the crossed out red cirlcle as the icon for that.  Other icon sets (Tango, elementary) have icons for the Mail Reader.  Any suggestions on how I could use an icon from a different icon set to be used for the Mail Reader main menu entry?

---

### Post by Frogs Hair on 2012-03-24
One possibility would be to copy an icon from another set to home, rename it if needed, and place it in the folder of the icon set being used . I would suggest using an icon from the scalable folder if applicable .

The edit menu configuration is different in Ubuntu or Gnome than XFCE , so the Ubuntu solutions probably won't apply . The link may be helpful .  [http://forum.xfce.org/viewtopic.php?id=6689](http://forum.xfce.org/viewtopic.php?id=6689)

---

### Post by ccrs8 on 2012-03-24
Your suggestion and the link you provided really helped out a lot.  I ended up copying an icon from the Elementary icon set (your suggestion) and putting it in the /usr/share/pixmaps directory (info from link).  Now when I pick an icon set from the appearance settings that has its own mail reader icon, that icon is used.  When I pick one without its own reader, the icon I put in /usr/share/pixmaps is used.

Thanks!

---

### Post by Frogs Hair on 2012-03-25
Glad it worked ! I totally forgot about Pixmaps .

---

