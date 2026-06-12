---
title: "Nautilus Scroll Bar size."
date: 2015-10-13
forum: Desktop Environments
---

### Post by Swagman on 2015-10-13
I've upgraded my monitor to a IIyama 28" 4k jobbie and obviously everything went to a miniscule size. I've been using **K**ubuntu for the passed few months and managed to adjust everything to my liking but alas Kubuntu got a Plasma desktop crash and I couldn't fix it so I Nuked it (it was 32 bit version anyway) and installed Ubuntu 15:04 fresh.

Ubuntu picked up most stuff straight off the bat with only minor tweaking needed  but the damned scroll bars in Nautilus just don't do *anything* and I can't find a setting to increase their size.

Please note.. I'm talking about **NAUTILUS** *NOT* programs.

**Yes** I can use the scroll wheel of my trackball but that's not ideal when you have a shedload of files to scroll through !

I've made a short vid capture to show what res I'm running at and the issue with the scroll bars (Vid is in HD)

[https://www.youtube.com/watch?v=5iYgn7zjj0w](https://www.youtube.com/watch?v=5iYgn7zjj0w)

How in the heck do I increase the size and actually make them work like they're supposed to ?

---

### Post by v3.xx on 2015-10-13
I do not know of a way to change just Nautilus, but you should be able to do this in the theme your using.

/usr/share/themes/[COLOR="#FF0000"]NAME-OF-THEME[/COLOR]/gtk-3.0/gtk-widgets.css

and about 3/4 of the way down

```
/************
* scrollbar *
*************/
.scrollbar
-GtkRange-slider-width:
```

May not be the fix your looking for, but maybe worth a try.

Good luck :)

---

### Post by mcduck on 2015-10-13
HAve you somehow disabled the overlay scrollbars? When you hover the mouse cursor near the scrollbar area you should see a larger scrollbar handle (with up & down buttons) appear next to it. The tiny scollbar visible in your video is just a visual indicator, not the bit you are expected to use to scroll with.

Try running this in a terminal:
```
gsettings reset com.canonical.desktop.interface scrollbar-mode
```

If that doesn't do it, make sure the [overlay-scrollbar]("apt:overlay-scrollbar") package is installed, and try specifically setting the scrollbar mode:
```
gsettings set com.canonical.desktop.interface scrollbar-mode overlay-auto
```
(or to force normal scrollbars instead:)
```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

---

### Post by Swagman on 2015-10-13
Thanks for the replies guys.

overlay-scrollbar is installed but nothing would make it work as it should included the first suggestion of editing the scrollbar width.

> gsettings set com.canonical.desktop.interface scrollbar-mode normal

Has done the trick and I'm happy with it, so that's a win !

Cheers

---

