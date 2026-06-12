---
title: "Change Icon"
date: 2012-09-21
forum: Desktop Environments
---

### Post by neuman1812 on 2012-09-21
Running Ubuntu 12.04 64 bit with Gnome-Classic.

I have a Link to a shell script on my desktop.

I would like to change the icon but I see no option to do that.  If I right click on it, I have 3 tabs 

Basic
Permission
OpenWith

None of these tabs have an option to change Icon.

---

### Post by josephmills on 2012-09-21
could you paste the shell script here for us to see please 
and thanks

---

### Post by ajgreeny on 2012-09-21
Is the "link" a **.desktop** file?  Look in more detail at what you've got with ```
ls Desktop
```

Nautilus will show all .desktop files as **desktop configuration files**, and gives you no way to edit them as far as I can see. However, you can easily do so with command ```
gedit scriptname.desktop
``` and in the text file that appears you can edit the line ```
Icon=/path/to/chosen/image.png
```to point to the icon you want to use.

---

### Post by diesch on 2012-09-21
If your link is not a *.desktop* file you need to create one if you want to change the icon.

If you don't want to edit *.desktop* files with a text editor [Arronax](http://www.florian-diesch.de/software/arronax/) gives you a easy to use GUI.

---

### Post by neuman1812 on 2012-09-21
Its the Tor Browser Bundle Startup script.

the original script is here:

~/TorBundle/start-tor-browser

I clicked on that script and selected "Make Link"

I then took that file it created "Link to start-tor-browser"  and moved it to my desktop.


Im not sure what type of script it is.  Im not familiar enough yet to know this.

---

### Post by stinkeye on 2012-09-21
If it's just a link you should be able to click the image in the
Basic tab where you were looking before.

_**Bonus Tip of the Day:**_Dragging a file to the desktop with the middle mouse button gives you a popup where you can choose to...
[LIST]
[*]Move Here
[*]Copy Here
[*]Link Here
[/LIST]

---

### Post by neuman1812 on 2012-09-22
> **stinkeye said:**
> If it's just a link you should be able to click the image in the
Basic tab where you were looking before.

_**Bonus Tip of the Day:**_Dragging a file to the desktop with the middle mouse button gives you a popup where you can choose to...
[LIST]
[*]Move Here
[*]Copy Here
[*]Link Here
[/LIST]

That worked thanks!
Dont have a middle mouse button tho.

---

