---
title: "Got rid of Unity Overlay Scrollbars and solved issue with Thunderbird too"
date: 2013-04-09
forum: Desktop Environments
---

### Post by L a r r y on 2013-04-09
I share with you a fix to a longstanding issue I have had with the Unity Desktop in Ubuntu Linux 12.04

I got fed-up with the Unity Desktop's "overlay" scrollbars, and found a way to globally disable them.  These are the ones that hang outside the window space and only appear with a mouse-approach.

I am back to the standard scrollbars that one sees in Gnome 2 Desktops in my earlier experiences with Linux.

**Thunderbird users** will also find the insane color scheme of its standard scrollbars is cleared up as well, if my experience is not unique!  While Thunderbird mail client did not use the overlays, the color scheme of the standard scrollbars was such that the active components could not be discerned from the gutter background.  Disabling the overlays brought back a sane color scheme to these scrollbars!

These overlays are for the birds, for they exist outside the window they are associated with, and often disappear leaving me clicking on a window behind the one I want to scroll.   That brings the unwanted window forward and buries what I am working with to the bottom of the stack if I have more than one open.

The solution is published here, and quoted below: [http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html](http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html)



In a Terminal, enter:

```
sudo su
echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars
```

---

