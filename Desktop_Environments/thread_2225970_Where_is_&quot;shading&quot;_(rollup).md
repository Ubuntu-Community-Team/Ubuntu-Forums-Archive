---
title: "Where is &quot;shading&quot; (rollup)?"
date: 2014-05-24
forum: Desktop Environments
---

### Post by jamapii on 2014-05-24
Hi,

older versions of Linux window managers had a feature called "shading" that would roll up the window to only show its title bar. (sone supposedly more user-friendly environments called it roll-up) This way, one could quickly peek underneath a window, or quickly peek into a normally "shaded" window. This works because the titlebar is active, and the switch normal->shaded->normal is done with 2 doube-clicks in the same spot.

In default Ubuntu 14.04, I found a feature under the name of "shading" which is the same as minimize with an added animation that may rightfully be called shading. But nothing that is useful in any similar way.

Is the feature hidden somewhere, or has it been completely removed? The window manager seems to be compiz.

---

### Post by Frogs Hair on 2014-05-24
I know the feature is included in xfce and enlightenment (E16-19) when using a supported theme, but  haven't seen the feature in Ubuntu. Gnome 2 might have had it, but I don't remember.

---

### Post by deadflowr on 2014-05-24
I don't know how to set the mouse on it, but ctrl+alt+S, is the default keybinding to use shade.

---

### Post by jamapii on 2014-05-24
yes, AFAIK all major window managers used to have rollup-shading except compiz with unity, recent mac os x and windows.

I tried Ctrl-Alt-S, this "shaded" (as in minimize+animation) the current window. Then I tried the same to unshade. This shaded another window, then I dug through the panel to unshade them. I also tried once more to click the first shaded window and Ctrl-Alt-S to unshade, didn't work, found out that the window was gone.

It seems to be actually a bug: [https://bugs.launchpad.net/compiz/+bug/1023814](https://bugs.launchpad.net/compiz/+bug/1023814) - Titlebar disappears when shading.

Only the bug is fixed long ago, and a new bug with a similar symptom appeared.

And everybody thinks it's not a bug, because what happens meets the normal definition of the word "shading", but not the computer-related definition. Could this be possible?

---

### Post by jamapii on 2014-05-24
dup

---

### Post by grumblebum2 on 2014-05-24
Double click to shade a window can still be enabled with....
```
gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar toggle-shade
```

To reset to default (toggle-maximize)....
```
gsettings reset org.gnome.desktop.wm.preferences action-double-click-titlebar
```

Still functions in compiz but not when the unity plugin is enabled. Window disappears.

In 14.04 the unity plugin takes over the drawing of the decorations from the window decoration plugin,
to enable menus to be shown in the titlebar.
The window decoration plugin can't be enabled with unity enabled.

---

### Post by jamapii on 2014-05-27
> **grumblebum2 said:**
> In 14.04 the unity plugin takes over the drawing of the decorations from the window decoration plugin,
to enable menus to be shown in the titlebar.
The window decoration plugin can't be enabled with unity enabled.

So that means "shading" cannot work with unity enabled. Unless unity implements its own shading support.

---

### Post by grumblebum2 on 2014-05-27
True && fat chance.

Something you may not be aware of is you can now minimize by clicking on a launcher icon.
To enable...
```
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true
```

---

