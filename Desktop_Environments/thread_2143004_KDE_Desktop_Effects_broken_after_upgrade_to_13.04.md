---
title: "KDE Desktop Effects broken after upgrade to 13.04"
date: 2013-05-07
forum: Desktop Environments
---

### Post by UrbanSlayer on 2013-05-07
So, my upgrade to 13.04 hasn't exactly gone to plan.

Desktop Effects within KDE are not working since the upgrade, and I am not able to activate them from System Settings.  I have tried to change the Compositing type to OpenGL, but with no luck.

I have an nVidia graphics card (8800) and the effects were fine on 12.10.  I have tried both nVidia drivers - 304 and 310.

My pastebin of the following command - *qdbus org.kde.kwin /KWin org.kde.KWin.supportInformation* - [http://pastebin.com/WpziwA7L](http://pastebin.com/WpziwA7L)

Also, my pastebin of the Xorg.0.Log - [http://pastebin.com/WpziwA7L](http://pastebin.com/WpziwA7L)

I did select to allow the updater to replace my kwinrc file, although I have since restored a backup - this has also not helped.

Can anyone shed any light?

Thanks!

---

