---
title: "Keyboard switcher gnome applet problem"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Invoker on 2006-09-21
Hey all. My problem is as follows:

I want to use a turkish keyboard as well as english. So I do the necessary font installations, keyboard configuration from gnome preferences and include the gnome keyboard indicator on my panel. However, when i switch my layout using this applet nothing happens except the indicator changes the country name it shows.

When I use setxkbmap tr/us from a terminal everything functions as expected and the indicator changes as well. However using the gnome switcher does nothing. Anyone can guess why? Help! :???: This is annoying as i just want to be able to shift+alt.

---

### Post by Invoker on 2006-09-22
Anyone?

---

### Post by flying_icarus on 2006-09-27
> **Invoker said:**
>  However, when i switch my layout using this applet nothing happens except the indicator changes the country name it shows.

When I use setxkbmap tr/us from a terminal everything functions as expected and the indicator changes as well. However using the gnome switcher does nothing. Anyone can guess why? Help! :???: This is annoying as i just want to be able to shift+alt.

Well, I was having the same problem (with croatian and us-english layouts), but I just discovered that this is a feature, not a bug. :)

Let me see if I can explain it properly. :) Right click the keyboard indicator (first change it to turkish)  and select "layout view". If I'm right, you will see the position of special characters written on the keys that should produce them. But! :) See what keyboard help says:
```

**Each key** in the diagram has up to **four characters**. These can be produced with different keyboard modifiers, as follows:

    * For the character shown in the *bottom left*, press the key alone.
    * For the character shown in the *top left*, press the key with Shift.
    * For the character shown in the *bottom right*, press the key with the **third level modifier**.
    * For the character shown in the *top right*, press the key with Shift and the **third level modifier**.
```

If I'm right, your special characters are shown in the right (top and bottom), so to access them you need the third level modifier. It's not set by default, so open keyboard preferences, go to "Layout options" tab and there you will find it on the list and be able to set it. Now with this third modifier (I chose AltGr, or right alt) you can type these characters.

My luck was that there is (among 4 layouts) a croatian layout which works "windows-like" in that the special characters are "shown on top and bottom left", so by switching to it there is no need for third modifier to type them.

I'm not sure if such "friendlier" layout is offered for turkish, but I guess it should work if you set the layouts and shortcuts for changing them in xorg.conf and forget about the keyboard switcher applet.

I must say that I have never ever in my life (~20 years computer experience) seen or heard about anyone using the other 3 offered croatian layouts, and that they are thoroughly confusing the hell out of me. :) In addition, the "one true layout" is labeled "croatian with guillemotes for quotes" which is completely and utterly undecipherable to me as a non-native english speaker and has turned out to be the last layout I would have thought to work. :)

Just my 2 cents, hope it works out for you...

---

