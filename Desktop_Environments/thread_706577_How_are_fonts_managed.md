---
title: "How are fonts managed?"
date: 2008-02-24
forum: Desktop Environments
---

### Post by explainer on 2008-02-24
I have a lot of fonts loaded that I suspect I will never use, so how can I remove selected fonts from my system?:confused:

---

### Post by stuartwood89 on 2008-02-24
I'm not sure on how to get to the fonts folder, but what I do is right-click on the desktop, select '[COLOR="Red"]Change Desktop Background[/COLOR]', then Select the '[COLOR="Red"]Fonts[/COLOR]' tab.  Click '[COLOR="Red"]Details[/COLOR]' at the bottom and then '[COLOR="Red"]Go to Fonts Folder[/COLOR]', also at the bottom.

When you've got that, just delete the ones you don't want.

A bit long-winded, I know.  The location is '///fonts' I think, but that means nothing to me :confused:

---

### Post by benerivo on 2008-02-24
The location is
fonts:///
But this may not let you delete all the ones you want, as I think this only displays user fonts (not the system fonts). You could also try```
gksudo nautilus
```and then go to the fonts folder. You will now be able to delete them, but be careful not to delete anything you need. I don't know for sure, but deleting some system fonts may break the desktop.

EDIT -  The location of user fonts is also available at /home/YOURNAME/.fonts

---

### Post by ejket on 2008-02-24
It's not useful to delete fonts except where you manually added them to your ~/.fonts directory or otherwise explicitly installed them.  Fonts installed by packages will be replaced when the package is upgraded.  In the case where these packages are dependencies, they stay.  If you installed font packages yourself that aren't dependencies, you can remove the package, but you can't cherry pick the fonts you want to keep.

---

### Post by stuartwood89 on 2008-02-25
Why would you want to remove fonts anyway?  The don't take up much space.  benerivo is right though, if you delete system fonts, you'll probably have trouble with fonts on the desktop/window headers etc.  Another thing is that, although you may never use the font yourself (eg, in an OpenOffice document) some web pages will.  So you could have some display problems when using the internet.

---

