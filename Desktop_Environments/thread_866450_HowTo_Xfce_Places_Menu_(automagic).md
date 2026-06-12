---
title: "HowTo: Xfce Places Menu (automagic)"
date: 2008-07-21
forum: Desktop Environments
---

### Post by dbbolton on 2008-07-21
This tutorial will help you automagically create a Places menu for the Xfce panel. It is intended for Debian Etch or pre-Gutsy Ubuntu, but should work on any distro that doesn't supply the Xfce places plugin. 

It includes some important system locations, picks up your bookmarks, and adds themable icons. The end result looks something like this:

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/xfce-places.png[/IMG]

1.  Download, this script (use at your own risk)
                    [http://envyouraudience.googlepages.com/xfcemenu.py](http://envyouraudience.googlepages.com/xfcemenu.py)

    Make executable:
```

chmod +x xfcemenu.py

```    Run:
```

./xfcemenu.py

```2. Right-click on your Xfce panel of choice > Add new item > Xfce menu

3. In the properties dialog, under Menu File, choose "Use custom menu file" and kindly point it to ~/.config/xfce4/desktop/places-menu.xml

4. Enjoy.

If you have any problems let me know.

---

### Post by jpeddicord on 2008-07-25
Moved from Tutorials to Desktop Environments: is a script, not a tutorial

---

### Post by denham2010 on 2008-07-25
Hi,

No need to download this script. Places menu functionality already exists. Right click the Xfce panel, click add new item, the plugin is called "Places"

Cheers.

---

### Post by dbbolton on 2008-07-27
> **jacobmp92 said:**
> Moved from Tutorials to Desktop Environments: is a script, not a tutorial

It was intended as a tutorial, but whatever.

> **denham2010 said:**
> Hi,

No need to download this script. Places menu functionality already exists. Right click the Xfce panel, click add new item, the plugin is called "Places"

Cheers.
As I mentioned, this script is intended for distros without the places plugin. I think it came out in gutsy.

---

