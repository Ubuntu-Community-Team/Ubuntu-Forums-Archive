---
title: "make menu look like this"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by superbungalow on 2007-08-05
How do I make the menu look like this:

[http://www.gnome-look.org/content/preview.php?preview=1&id=63680&file1=63680-1.png&file2=63680-2.png&file3=63680-3.png&name=Light+N+Crispy+compiled+icon+theme](http://www.gnome-look.org/content/preview.php?preview=1&id=63680&file1=63680-1.png&file2=63680-2.png&file3=63680-3.png&name=Light+N+Crispy+compiled+icon+theme)

So it is all in one button. And also, how do I change the button?

---

### Post by z0phi3l on 2007-08-05
Right click your toolbar click on add to panel and add the Main Menu in the utilities section


If you choose to keep it, right click the other menu, and select remove from panel.


You can then move the new one by right clicking and selecting move, but you might need to uncheck lock to panel first.

---

### Post by superbungalow on 2007-08-05
How to I change the icon?

---

### Post by z0phi3l on 2007-08-05
Usually to change the icons you use an icon theme, or there is another way of just changing the menu icon, but I don't know exactly how to do that.

---

### Post by Deco_21 on 2007-08-05
this may help.

[HTML]http://ubuntuforums.org/showthread.php?t=505669&highlight=menu+icon[/HTML]

---

### Post by BOBSONATOR on 2007-08-05
Ok, here is where I do most of my business.

The icon is based of an icon in your icons directory named start-here.svg 

For ex. 

/usr/share/icons/Tango/scalable/places/start-here.svg 

Refers to the start icon for all the themes that rely on tango as a backup.

To change that icon, you need administrator rights like 

gksudo thunar

or 

gksudo nautilus

Simply copy your new icon over the previous icon that is there.

---

