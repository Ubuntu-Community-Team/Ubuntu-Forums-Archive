---
title: "compiz window border loss"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by hollowhead on 2007-11-12
This problem has come up before, but when I have run compiz I lose my window borders.  I have tried various suggestions.  What is the fix?  Note not using Nvidia card.  All other effects work ok including the "cube".  Ta.

---

### Post by Zorael on 2007-11-12
You need to run a window decorator, if you aren't already. The normal window manager isn't OpenGL-aware, see.


Enable the Window Decoration plugin (under Effects), and it might solve itself.

If you're running Gnome, you need the compiz-gnome package installed to get the 'metacity' OpenGL window decorator. I believe compiz-gnome is included in the compiz package, so you should have it installed per default. Just enable the plugin.

If you're running KDE, you could try the compiz-kde package (not installed by default) to get 'kde-window-decorator'. Many, including myself, have had showstopper issues with this decorator, though.

The alternative to both metacity and kde-window-decorator (among others, I imagine?) is Emerald. For which you'll want to install the emerald package.

Make sure to set the Command field in the Window Decoration plugin to 'metacity --replace', 'kde-window-decorator --replace', and 'emerald --replace', depending on which one you choose.

There is no longer an emerald-themes package, but once you get the Emerald theme manager installed, you can download both GPL'd and Non-GPL'd themes through it. And there's more themes to be found on the Internet; likely on gnome-look.org and kde-look.org.

The emerald-themes package can be found [here](http://packages.ubuntu.com/feisty/x11/emerald-themes), if you really really want it. I'm not sure it's compatible with Gutsy and the Emerald version in its repositories, but I don't see why it shouldn't be.

---

### Post by hollowhead on 2007-11-12
Cheers mate.  I have had some success by unchecking "undirect fullscreen windows" in the general settings, this has partially solved the problem giving me borders in openoffice apps but not dia or firefox.  When I launch compiz from a terminal these are the messages 

compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

I don't know whether they are relevant.  Finally compiz-gnome package is installed how do I enable its plug-in?

---

### Post by Zorael on 2007-11-12
```
Starting gtk-window-decorator
```

My mistake, gtk-window-decorator is the OpenGL-aware decorator, not metacity. The Command field in your Window Decoration plugin (which you have enabled by now, I hope), should say 'gtk-window-decorator --replace'.

This could be an issue with videocard driver settings (much like you'd need to add the AllowGLXWithComposite option on Nvidia cards), and if you don't have an Nvidia one, I can't help.

For all I know, you have a non-OpenGL videocard; it certainly seems your current setup doesn't support direct rendering. If yours is an ATI, there's the option of changing drivers (alternatively install the xserver-xgl package, though I hear it's slow as heck).

Finally, as a troubleshooting procedure, you could try installing Emerald and see if it works better. If it does, you'll know the issue resides in gtk-window-decorator.

---

### Post by hollowhead on 2007-11-12
I've solved it- apologies.  In the uncategorized section I checked the place windows checkbox, the only app this doesn't solve it for is gnumeric.  But I can live with this.

---

