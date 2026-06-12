---
title: "stack effect in cairo dock"
date: 2008-02-01
forum: Desktop Effects &amp; Customization
---

### Post by kjk85 on 2008-02-01
anyone has any idea on how to make the stack effect like this [cairo-dock stack](http://www.youtube.com/watch?v=_F2tAMeTKqI) where the sub dock appear in the curve motion. thanks

---

### Post by kjk85 on 2008-02-02
anyone ?

---

### Post by wingnux on 2008-04-10
I have the same question...

---

### Post by overdrank on 2008-04-10
> **wingnux said:**
> I have the same question...

HI and I don't understand. I have all the effects except for the second icon from the left in the video. Is that what you are asking?

---

### Post by Genius314 on 2008-04-10
You need to install the plugin package (should be on the Cairo site), then go to Configure for Cairo-Dock, the Applets tab, and the second list should have a "rendering" plugin. Enable it.
Now go to the views tab and change the Sub-docks to "Parabolic." :)

---

### Post by wingnux on 2008-04-11
Everything's set as you said but I really can't get the "sub-dock" thing and the cairo-wiki ([https://help.ubuntu.com/community/CairoDock#head-e32e81d6528271cc9fe23ca55369e4d0dfe0bd5f](https://help.ubuntu.com/community/CairoDock#head-e32e81d6528271cc9fe23ca55369e4d0dfe0bd5f)) doesn't help either...

Could you please explain how sub-docks work?

EDIT:

Here are some examples from the cairo-dock website

[http://developer.berlios.de/dbimage.php?id=3819](http://developer.berlios.de/dbimage.php?id=3819)
[http://developer.berlios.de/dbimage.php?id=3716](http://developer.berlios.de/dbimage.php?id=3716)

Btw, it says here [http://www.cairo-dock.org/ww_page.php?p=Launchers&lang=en](http://www.cairo-dock.org/ww_page.php?p=Launchers&lang=en) that when you modify a launcher you get some options and the last one is "A box to tick specifies if that icon should be a container or just be a simple launcher. If it is to be a Container then the field containing the command to execute is not used. (see [WWW] Add containers in "Tips and Tricks" section) "

As you can see on the attached screenshot I don't have that box and yes, I'm running the latest version of cairo-dock... :confused:

---

### Post by kawaji on 2008-04-11
if you are using the latest cairo-dock,

To make a new container, 
Select ' **Add a sub-dock** ' from context-menu of cairo-dock, 
then a ' **Fill this launcher** ' titled dialog window will be pop-upped.  
Edit Launcher's name in the dialog, which will be a new container name. e.g. **wingnux**
After that, Click  '**Extra parameters**' to expand it.
Choose ' **Parabolic**' from '**Name of the view used for the sub-dock**' drop-down list.

To add a launcher to the container as sub-dock,
Right click on a launcher you want to add to the container. 
Select ' **Modifiy this launcher** ' from menu.
Click '**Extra parameters**' to expand it.
In ' **Name of the container it belongs to :** ' , 
you will find **wingnux** ,the container name, in drop-down list.
Choose it and then click ' OK ' to close the dialog.

After adding some launchers to the container by the above way, 
Click the container icon , you can see stack effect.

also it would be better to enable 'Animate sub-dock when they appear? ' option, 
and set some seconds for delay to display sub-dock in Cairo-dock advanced settings -> System tab -> Sub-docks section.

---

### Post by wingnux on 2008-04-11
Cool, it works!

There's some weird bug that makes the Parabolic view the only option that doesn't work but any other view works just fine and it's enough for me =)

Thank you very much!

---

