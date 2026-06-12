---
title: "Trash or Deleted Items?"
date: 2009-03-06
forum: Desktop Environments
---

### Post by Jack Harkness on 2009-03-06
Earlier this week, I had to reformat my laptop and I installed Kubuntu Hardy (KDE 3.5).  It's working beautifully, but there's one odd thing that happened.

Originally the Trash was called "Trash" everywhere.  When you hovered over the icon in the kicker, it said "Trash".  When you right-clicked a file, it said "Move to Trash".  

After a couple of days, however, I noticed that it had renamed itself "Deleted Items".  When you hover, right-click a file, etc, "Deleted Items" has replaced "Trash" everywhere but in Dolphin.  It's still titled "Trash" there.  And if you click the Kicker icon and tell it to open in a window, it goes to the trash folder.

The actual folder is still named "Trash".  It just seems to be changed in KDE. 

Anyone have this happen to them?  Any idea why?

---

### Post by hatalar205 on 2009-03-06
I'm not sure. But &#305; think you should click right and change the desktop view to folder view. It is KDE4's new feature. When you change to folder view you will see home folder, trash(which is working well) and caffeine .... The trash you see is just a widget not the real one. And it isn't working well.

---

### Post by Jack Harkness on 2009-03-06
Thanks, but I'm actually running KDE 3.5!

Anyway, I figured this one out on my own finally (With a little help from a post on another forum). 

It's related to the Region and Languages setting.  I'm Scottish, but I live in the US.  When I installed, it installed US English as the default language.  I had changed it to UK English because that's what I'm used to.  Apparently when you do that, the folder stays named Trash, but the Kicker applet and Konqueror links change to "Deleted Items" or "Deleted Items Folder", and the Kicker app itself is renamed the "Wastebin".

The only thing immune to this is Dolphin.  It stayed "Trash" in the side menu.

Anyway, I changed the languages back to see, and it's all named "Trash" once again!

---

