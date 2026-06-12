---
title: "Out of the box themes disappeared - Ubuntu 13.04 / Unity 7.0.0"
date: 2013-09-08
forum: Desktop Environments
---

### Post by n-damian on 2013-09-08
Hi guys.  Have just done a clean install of 13.04 which is running Unity 7.0.0 and been messing around with various tweak tools (Unity Tweak Tool & Ubuntu Tweak) and installing various downloaded themes.  I've unfortunately somehow lost all of the stock / out of the box themes (e.g. Ambiance, Radiance, etc) and now have old school window controls (and buttons) that I cant seem to get rid of.  I think I may have removed the themes when running copy and paste commands into the terminal like the noob I am!  Please help me restore.  Note I've already ran dconf reset -f /org/compiz/ to no avail.  Thanks!

---

### Post by Frogs Hair on 2013-09-08
Hello and Welcome


Select  the gear icon on the top right and then system settings . Open Appearance > Look  and try selecting Ambiance or Radiance from the drop down menu below the wall paper selections. If they don't appear in the list  try the following . ```
sudo apt-get install light-themes 
```

Be sure any themes you download are Gnome 3.6 /12.10 or 13.04 compatible or thy may may not display properly or not at all.

---

### Post by n-damian on 2013-09-09
That solved my issue.  Stock themes back.  Thanks Frogs Hair!

---

### Post by Frogs Hair on 2013-09-09
You're Welcome  ! ;)

---

