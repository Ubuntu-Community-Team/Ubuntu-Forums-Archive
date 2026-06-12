---
title: "Editing the look of Firefox running on Ubuntu"
date: 2009-03-09
forum: Desktop Environments
---

### Post by vanattab on 2009-03-09
I very much dislike how large the toolbars and menus are in firefox when running on ubuntu. I was able to follow [this]("http://http://ubuntuforums.org/showthread.php?p=5380788#post5380788") post to edit my userChrome.css file to resize the menu bar and default toolbars but I can't figure out how to adjust the Delicious Toolbar. I am guessing by reading the userChrome.css file that there is some unique name for the toolbar, for example it appears that the edit the menu bar you use   ```
/* Menu Bar - Shrink and Fade Text */
#navigator-toolbox .menubar-text {
	font-size: 70% !important;
	color: #999 !important;
	}
```
Does any one know what the equivalent of ```
#navigator-toolbox .menubar-text
``` would be for the Delicious Toolbar?

---

### Post by blacksm1th on 2009-04-01
I don't know the name but you can install 2 addons temporarily and see it by yourself. The names of addons are "DOM inspector" and "inspector widget". After install and restart of FF click RMB somewhere on toolbars then Customize... and then drag blue magnifying glass icon close to forward/back buttons for example. After that click on the glass and then click on Delicious Toolbar. The new window will came up and on the right pane you will see name of element.

---

### Post by ninjapirate89 on 2009-04-01
I'm not sure what exactly you are trying to accomplish but here is a screenshot of how I have my menus in firefox set up.

---

### Post by blacksm1th on 2009-04-01
You asking about name of Delicious Toolbar? I can't see it on sceenshot :). I use dom edit extension to learn names of chrome components. 
[IMG]http://img406.imageshack.us/img406/6756/screenshotz.png[/IMG]

---

### Post by ninjapirate89 on 2009-04-02
Oh okay I understand what they are wanting now. I never use the delicious toolbar so I have no idea how to edit its appearance. I like my toolbars to take up as little space as possible so I hide all unnecessary toolbars and use small icons. I also use an addon to hide the menu bar.

---

### Post by blacksm1th on 2009-04-02
This screenshot is from Dom inspector addon:
[[IMG]http://img511.imageshack.us/img511/7629/screenshotseu.th.png[/IMG]](http://img511.imageshack.us/my.php?image=screenshotseu.png)
With Dom inspector you can learn the "names" of all visible FF components including the one that interested you. Just with two mouse clicks (first click is on blue magnifying glass, second is on chosen element of FF). In screenshot i click on magnifying glass and then in urlbar - in the  right pane next to "id" is the name of component. In this case this name is "urlbar". When you finish with addons you can uninstall them. You need them only to see "names" - then uninstall.

---

