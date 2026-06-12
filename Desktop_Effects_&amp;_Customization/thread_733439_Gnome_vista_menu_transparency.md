---
title: "Gnome vista menu transparency?"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by kdarkentity on 2008-03-23
What i want to do is make the gnome vista menu that i got from gnome-look.org transparent. If i mouse over it and hold alt and then dosen'tme scroll it will become transparent since i am using compiz fuison, but it doesn't stay that way permanently obviously, I know that under the general options tab under opacity you can add in opacity settings to the gnome panel and to the main menu, i simply just don't know what to call the vista menu to apply the opacity setting to it under the compiz fusion settings.

[Gnome Vista menu]("http://www.gnome-look.org/content/show.php/Vista+Start+Menu+for+Gnome+Panel?content=71425")

---

### Post by chewearn on 2008-03-24
Is it called dropdownmenu?

---

### Post by kdarkentity on 2008-03-24
well i have it on a panel that is positioned at the bottom of my screen so i figured that it would be popupmemu, but i could try that anyways.

---

### Post by QB89Dragon on 2008-05-01
This is done through the compizconfig settings manager "advanced desktop effects settings". This is not done through the menu.
Don't change the alpha transparency of the menu theme. To change this download the advanced desktop effects settings for compiz, and go in there and go to general options (the first one), then "opacity settings" (tab along the top), and add these two lines:
class=Gnome-panel to 80
class=Vista_Menu.py to 90

you may also want to configure gaussian alpha blur so that text is easier to read on the menu.

---

### Post by vikasvishnu on 2008-05-02
> **kdarkentity said:**
> well i have it on a panel that is positioned at the bottom of my screen so i figured that it would be popupmemu, but i could try that anyways.

Hmm.. have you tried ubuntu-tweeks package? It lets you make the menu bars transparent along with many other options for modifying your desktop. 

Check out [[COLOR="Red"][COLOR="DarkOrange"]this theme[/COLOR][/COLOR]]("http://www.gnome-look.org/content/preview.php?preview=1&id=66389&file1=66389-1.jpg&file2=&file3=&name=MidnightBluePlastic") from Gnome-look.org. You will see what I mean. The menu bar is transparent with the use of ubuntu-tweek. 

Adjusting the CCSM might also work, but I havent tried that yet. 

-:Vikas:-

---

### Post by kdarkentity on 2008-05-04
> **vikasvishnu said:**
> Hmm.. have you tried ubuntu-tweeks package? It lets you make the menu bars transparent along with many other options for modifying your desktop. 

Check out [[COLOR="Red"][COLOR="DarkOrange"]this theme[/COLOR][/COLOR]]("http://www.gnome-look.org/content/preview.php?preview=1&id=66389&file1=66389-1.jpg&file2=&file3=&name=MidnightBluePlastic") from Gnome-look.org. You will see what I mean. The menu bar is transparent with the use of ubuntu-tweek. 

Adjusting the CCSM might also work, but I havent tried that yet. 

-:Vikas:-

Wow that is a really nice theme, but i have already managed to solve the menu transparency issue, thanks.

---

### Post by OzzyFrank on 2008-07-15
For anyone looking for "ubuntu-tweek", it's actually called "**ubuntu-tweak**", and is worth installing.

---

