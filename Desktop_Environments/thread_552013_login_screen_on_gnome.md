---
title: "login screen on gnome"
date: 2007-09-15
forum: Desktop Environments
---

### Post by Aramil Moonmist on 2007-09-15
ive been playing around with putting in a new login screen using the default login screen manager in the system>admin. it accepts the theme, however, on boot i complains about there being no data in the /usr/share/gdm/themes/LinuxTheme (which is what i have it set to)

the theme itself i pulled off of kde-look.org but looking at the files it should work for gnome too right?

things ive tried that havent worked:
changing the jpg to a png (and changing the name in the xml file too)
i noticed they were both executable so i turned that off

i used files from the "human" theme to kinda test it and found:
if i put the .desktop file in, it says theres no human.xml (thus its reading the right .desktop file)
if i put in the .xml file too it complains about not having certian images (which proves that the xml file is being read)

so i believe the problem is somewhere in the xml file (but i could be wrong). i obtained the tar.gz from [http://www.kde-look.org/content/show.php/KdmLinux+?content=55345](http://www.kde-look.org/content/show.php/KdmLinux+?content=55345)
could someone please look at it and tell me whats wrong? it looks really cool, and i want to try it out

thank in advance : )

---

### Post by Aramil Moonmist on 2007-09-30
sorry, but its been a while, bump

---

