---
title: "No opera icon in panel"
date: 2005-10-19
forum: Desktop Environments
---

### Post by PtS on 2005-10-19
I've installed opera from a .deb file and have it working now... The only problem is that my starter in the panel hasn't got any icon... I've tried to add an icon but it isn't in the list and when i try browse for it and try to choose the .png file i've downloaded... the .png file is grey and i can't choose it! If somebody could help me, I'd be grateful.

---

### Post by kperkins on 2005-10-19
I've noticed the same behavior with other apps.  If you want to switch panel icons, and it's not in the default folder (or the folder where the icon was before the upgrade) then you can't choose any icons--what's up with this?

---

### Post by kabus on 2005-10-19
Open the Properties of your Opera launcher, click on the icon button and  when the "Browse Icons" window opens paste this in there :

/usr/share/opera/images/opera_48x48.png

---

### Post by stuporglue on 2005-10-19
Could it be grey because you don't have the right permissions on it? If adding it like the parent poster said, check it's permissions.

---

### Post by kperkins on 2005-10-19
Why would permissions change between Hoary and my breezy upgrade?
(and I already checked 755 for the folders 644 for the icons--the same as in the pixmaps folder)
It only doesn't let you change the icon if you browse to a different folder than the one in which the icon you are already using is in.

---

