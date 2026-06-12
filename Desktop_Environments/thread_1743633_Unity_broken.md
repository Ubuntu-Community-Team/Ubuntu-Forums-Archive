---
title: "Unity broken"
date: 2011-04-29
forum: Desktop Environments
---

### Post by wazza75 on 2011-04-29
Unity in Ubuntu 11.04 is broken. When i log in to Unity, all I get is my desktop background, nothing else.

---

### Post by oldarney on 2011-04-29
you probably disabled the unity plugin in compiz. Try right clicking on the desktop, create a launcher to "gnome-panel" and access compiz using the old fashion menus to reenable Unity.

---

### Post by wazza75 on 2011-04-29
Thats exactly what I did. Thanks for that, all fixed now.

---

### Post by wazza75 on 2011-04-29
Actually I still have one problem. Now the workspace switcher doesn't work in Unity. Any ideas.

Thanks

---

### Post by Redbaron62 on 2011-04-29
Having the same problem.  did the same thing to cause it too.  Can somebody explain what is meant by "reenable Unity"

---

### Post by Krytarik on 2011-04-29
You both need either to enable the "Desktop Wall" plugin in "CompizConfig Settings Manager -> Desktop" or the "Desktop Cube" and "Rotate Cube" by following this post:
[http://ubuntuforums.org/showthread.php?p=10734118#post10734118](http://ubuntuforums.org/showthread.php?p=10734118#post10734118)
But the path to the Unity specific profile may be "/apps/compizconfig-1/profiles/unity/general/screen0/options", please give feedback on that.

Greetings.

---

### Post by wazza75 on 2011-04-29
The path is right. I did that, but the workspace switcher is still not working.

---

### Post by untenops on 2011-04-29
I still say unity is broken.  All I get is a wallpaper, and thats it.  if i right click on the desktop, I get a menu that flashed on for bout half a second then its gone then its back 5 seconds later, and gone again.

---

### Post by Krytarik on 2011-04-29
> **wazza75 said:**
> The path is right. I did that, but the workspace switcher is still not working.
You need to relogin after modifying the key, or at least restart Compiz by running "compiz --replace" via the Alt+F2 dialog.

Also, make sure that there is more than one workspace set in "CompizConfig Settings Manager -> General Options -> Desktop Size (tab)".

---

### Post by Krytarik on 2011-04-29
> **untenops said:**
> I still say unity is broken.  All I get is a wallpaper, and thats it.  if i right click on the desktop, I get a menu that flashed on for bout half a second then its gone then its back 5 seconds later, and gone again.
Could you run Compiz (desktop effects) in your previously used version?
How about "Ubuntu Classic" with Compiz?

---

### Post by Redbaron62 on 2011-04-29
Thanks for this, but for some reason there is no border on the windows; I can't drag it or anything.  I also can't close it unless it takes up the entire screen, so that the close button is on the panel. The workspace switcher isn't working either.

---

### Post by Krytarik on 2011-04-29
> **Redbaron62 said:**
> Thanks for this, but for some reason there is no border on the windows; I can't drag it or anything.  I also can't close it unless it takes up the entire screen, so that the close button is on the panel. The workspace switcher isn't working either.
The same what I wrote in post #9 applies to you.

As for the window decorations, please see this parallely running thread:
[http://ubuntuforums.org/showthread.php?t=1743724](http://ubuntuforums.org/showthread.php?t=1743724)

---

### Post by Redbaron62 on 2011-04-29
I now seem to have the workspace thing fixed, as well as the window border problem; now my only problem is that I get the same exact  thing when I go on regular ubuntu and classic.  Is there any way to remove unity from the ubuntu classic?

---

### Post by Krytarik on 2011-04-30
> **Redbaron62 said:**
> I now seem to have the workspace thing fixed, as well as the window border problem; now my only problem is that I get the same exact  thing when I go on regular ubuntu and classic.  Is there any way to remove unity from the ubuntu classic?
There are at least two sets of settings for Compiz in Gconf
(these are the paths to the 'active_plugins' keys):

- one that is meant as general settings, or usual Gnome:
"/apps/compiz-1/general/screen0/options"

- and one that is specifically set up for Unity:
"/apps/compizconfig-1/profiles/unity/general/screen0/options"

Also, make sure that in Unity's CCSM the profile "Unity" is selected in "CompizConfig Settings Manager -> Preferences (bottom left) -> Profile".

Please report if there is another profile in "/apps/compizconfig-1/profiles" and how it's called.

---

### Post by Henry-t on 2011-05-07
I got myself into the same trap after mucking around with CCSM.

The only way I found to resolve it was to create a launcher for ccsm - run it -> Select Preferences -> select the Default profile from the pulldown menu.  

Logged on and off again and desktop reset.

---

