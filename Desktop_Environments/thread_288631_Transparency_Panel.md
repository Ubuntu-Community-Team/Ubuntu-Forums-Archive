---
title: "Transparency Panel"
date: 2006-10-30
forum: Desktop Environments
---

### Post by Belgatom on 2006-10-30
Bit of a beginner here.

Just fooling around with the desktop and I saw in the gallery [this ]("http://ubuntuforums.org/gallery/showphoto.php?photo=3889&size=big&cat=2")screenshot. 

How can I make the different parts also get transparency. The panel itself is transparent but the date, workspace selector, deskbar and so on aren't.

While I am here: how do I install the Gdesklet? The site seems to be down, so don't know where to find the info.

---

### Post by Jussi Kukkonen on 2006-10-30
Installing gdesklets should happen just like installing anything else: use Synaptic or aptitude: [https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware). 

Only use software downloaded from other places if you are sure that the one in repository isn't what you want and if you are sure that it won't hose your operating system -- a lot of the problems people have when upgrading the OS comes from installing third party software...

---

### Post by jr.gotti on 2006-10-30
The complete panel transparency may have been done using compiz, by holding alt and scrolling the scrollwheel while mouseover on the panel. (This works on any window)

---

### Post by jgcamp99 on 2006-10-30
Follow these instructions, the principles are there, don't worry about deleting anything, just change the properties, the key is how you handle the background properites of the panel itself

[http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)

Let's begin with the bottom panel. Our aim is to have a panel which contains only application launchers. The first step is to remove all the other elements from the panel. In default ubuntu installation there are Recycle bin, Taskbar, desktop switcher and show desktop -button. These are added later to the top panel so don't worry. You won't lose them forever! You can remove these elements by clicking right mouse-button on them and selecting "Remove from panel" from pop-up menu. Now you have empty gray panel. Next click right mouse-button on the empty panel and select "Properties". Change the Size of the panel to 50 and remove all the ticks form the selectionboxes (See screenshot). Then change to Background tab and select "Solid color". Change the Color to white, if it's not already, and move "Style" slider like in this screenshot. Now the panel is ready. Next we just add icons (application launchers) to it. You can simply drag and drop the icons from the desktop. Another way is to click right mouse-button on the panel and select "Add to panel...". Select "Custom application launcher" from the window and fill Name, Command and select some beatiful icon. You can also write a short comment about the program, if you will. (See screenshot) 

There is also a very nice new dock-application called cairo-dock. It's in very early stage of developement, but it looks really promising project. It doesn't support PNG icons yet and there not really a lot of OSX looking SVG icons, so it's probably not the best option yet, but I suggest you to stay tuned. It will be great!

---

