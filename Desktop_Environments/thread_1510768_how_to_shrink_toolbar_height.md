---
title: "how to shrink toolbar height?"
date: 2010-06-16
forum: Desktop Environments
---

### Post by cometdog on 2010-06-16
My toolbars and tabs (at the top of gedit, for example) seem to have a lot of wasted vertical space, but I can't figure out how to shrink them.

I've seen some posts on making Ambiance and Radiance themes take up a little less real estate.  Generally the instructions involve something like
```
gksudo gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
```
and modifying some of these kinds of settings
```
gtk-icon-sizes="\
    gtk-menu=16,16:\
    gtk-button=16,16:\
    gtk-small-toolbar=16,16:\
    gtk-large-toolbar=16,16:\
    gtk-dnd=16,16:\
    panel-menu=16,16:\
    panel=16,16:\
    gtk-dialog=16,16\
"
```

I have looked around in that gtkrc file and tried to change about everything I can find, but nothing seems to actually shrink the toolbar.  I can make the icons in the toolbar ridiculously tiny, or closer together.  But then I just have tiny little icons in a vast wasteland of toolbar space.

Does anyone know how to accomplish this?

---

