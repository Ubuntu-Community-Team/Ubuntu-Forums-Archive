---
title: "Emeral Themes Problem"
date: 2008-04-01
forum: Desktop Environments
---

### Post by dlovley on 2008-04-01
I have Hardy Heron Beta installed. I had to disable xgl-server to stop gnome from crashing. I still have compiz cube working etc. My emeral themes wont work at all unless I use 'emerald --replace'. When I enter the cmd in the terminal the theme I selected will appear and looks great but will be gone the next time I log in. Do I need to install some other package or enter a cmd in terminal to fix this? Does emeral themes rely on xgl-server?

---

### Post by justsomedude on 2008-04-01
Install the compizconfig-settings-manager, if you haven't done so already.

Open it, and navigate to Effects --> Window Decoration (make sure it's enabled) --> Command and enter

```
emerald --replace
```

in the box.

---

### Post by dlovley on 2008-04-01
> **justsomedude said:**
> Install the compizconfig-settings-manager, if you haven't done so already.

Open it, and navigate to Effects --> Window Decoration (make sure it's enabled) --> Command and enter

```
emerald --replace
```

in the box.

Compiz config setting manager is installed and I have window decoration activated. I get a little red glow around the windows so I assume windows decorations are on. When I enter 'emerald --replace' in the console it works and my theme shows up instantly. When I log out and then back in my theme is gone. If I click on the theme in emerald nothing happens at all. I can only activate the theme on a temporary basis by using the console and entering emerald --replace. Before I upgraded to 8.10 beta I could activate the theme by clicking on it in emerald themes and then restarting via log out. The theme would remain intact after that. What I'm looking for is a way to make the theme stick.

BTW Thank you very much for your reply I was starting to get complex around here =D>

---

### Post by dlovley on 2008-04-01
I tried using fusion icon to make the theme remain. When I ran it in console this information came up maybe somebody can make sense of this.

 * Detected Session: gnome
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz.real --replace --sm-disable --ignore-desktop-hints ccp
compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
Starting gtk-window-decorator
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/expo/allscreens/options/expo_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by benerivo on 2008-04-01
justsomedude means that you have to put emerald --replace in the Window Decoration options window of the Compiz Settings Manager, rather than in a console window.

---

### Post by dlovley on 2008-04-01
> **benerivo said:**
> justsomedude means that you have to put emerald --replace in the Window Decoration options window of the Compiz Settings Manager, rather than in a console window.


Thank You!

I understand now, and that worked perfectly. Thank you all for your patience I wont be a newb forever.

---

