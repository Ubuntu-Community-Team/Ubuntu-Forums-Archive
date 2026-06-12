---
title: "How do i get the window buttons on the left in lucid?"
date: 2010-05-06
forum: Desktop Environments
---

### Post by Mr_VeRiTy on 2010-05-06
Hi, I recently upgraded to lucid lynx via the update manager, but the window buttons did not switch to the left side, or install a theme that has the window buttons on the left side, how do I get them on the left side, or what theme do I download?

---

### Post by Ugluk on 2010-05-06
In Metacity settings.

---

### Post by Mr_VeRiTy on 2010-05-06
Which setting in metacity?

---

### Post by Mr_VeRiTy on 2010-05-06
*bump*

---

### Post by eltonw on 2010-05-06
> **Mr_VeRiTy said:**
> Hi, I recently upgraded to lucid lynx via the update manager, but the window buttons did not switch to the left side, or install a theme that has the window buttons on the left side, how do I get them on the left side, or what theme do I download?

Go to System ==> Appearance ==> Theme 
and configure the desktop appearance to your liking.

---

### Post by Mr_VeRiTy on 2010-05-06
but which theme has the window buttons on the left side?

---

### Post by sakisds on 2010-05-06
I think changing the theme/controls once will put the buttons to the right, just play a bit with the themes.

---

### Post by Mr_VeRiTy on 2010-05-06
I don't understand what you mean, i just want to know which theme has the window buttons on the right, and i'm also sorta new to ubuntu. :D

---

### Post by Mr_VeRiTy on 2010-05-06
*bump*

---

### Post by Mr_VeRiTy on 2010-05-06
*bump*

---

### Post by Labus on 2010-05-06
Doesn't you notice when you try different themes? I think Ambience and Radience have the buttons to the left.The other have them to the right. Otherwise can you use Ubuntu tweak and change the buttons however you want, even remove them completely.

---

### Post by Mr_VeRiTy on 2010-05-06
I dont have ambience or radience in my appearence preferences

---

### Post by jr3us on 2010-05-06
Install ubuntu-tweak, and in the Windows section, select the buttons to be on the right and thats it.

---

### Post by eltonw on 2010-05-06
> **Mr_VeRiTy said:**
> I don't understand what you mean, i just want to know which theme has the window buttons on the right, and i'm also sorta new to ubuntu. :D

[http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#mwbuttons]("http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide#mwbuttons")
[FONT="Tahoma"]**Windows Buttons Order**

A lot of users complain that the new place for the minize - maximize - close window buttons isn't good. Mwbuttons is a script that allows you to easily change the place the buttons place from left to right. To install and run it type:
 wget [http://launchpad.net/mwbuttons/trunk/v0.2/+download/mwbuttons](http://launchpad.net/mwbuttons/trunk/v0.2/+download/mwbuttons)
chmod +x mwbuttons
./mwbuttons[/FONT]

The above is taken from *a very useful link* for [COLOR="Sienna"][SIZE="2"]post-install tweakings of LUCID[/SIZE][/COLOR]:

[SIZE="3"][COLOR="Green"][CENTER]Ubuntu Lucid Lynx 10.04 Post Installation Guide[/CENTER][/COLOR][/SIZE]
[CENTER][http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide]("http://www.my-guides.net/en/guides/linux/193-ubuntu-lucid-lynx-1004-post-installation-guide")[/CENTER]

(If you use a Macintosh as I do, you would find that the default button placement in LUCID is similar to that of OSX.)

---

### Post by user333 on 2010-05-06
I think I have an idea :) (I do some metacity-theming so I know a little about it)

you need to open gedit first, and then you need to find /usr/share/themes/[theme-name]/

if you can't find it there, look in /home/[your-user-name]/.themes/[theme-name]/
open the index.theme file.

you should see a line that says ButtonLayout=, or maybe there isn't one. Just add it in this case. 

Maybe it says:
```
ButtonLayout=:minimize,maximize,close
```All you have to do is change the position of the ":" to the right to make the buttons go on the left, or on the right to make the buttons go on the left (who made it like that anyway? :confused: ) 

And to change the button layout, just switch the order of the words, like in this example from the dust theme:
```
ButtonLayout=maximize,minimize,close:
```I believe this only works in lucid.

hope this answers your question!

---

### Post by n.l.o on 2010-06-21
> 
Maybe it says:
```
ButtonLayout=:minimize,maximize,close
```All you have to do is change the position of the ":" to the right to make the buttons go on the left, or on the right to make the buttons go on the left (who made it like that anyway? :confused: ) 

And to change the button layout, just switch the order of the words, like in this example from the dust theme:
```
ButtonLayout=maximize,minimize,close:
```I believe this only works in lucid.


This sure helped me out... Although I changed it in gconf (Applications>Metacity>General = the "button_layout" string)
Thanks :KS

---

