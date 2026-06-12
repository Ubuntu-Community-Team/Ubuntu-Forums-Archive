---
title: "How do I replicate this desktop?"
date: 2010-02-09
forum: Desktop Environments
---

### Post by Garnett on 2010-02-09
[[IMG]http://i164.photobucket.com/albums/u32/garnettf/pti-seb-screesnhot-fluxbox-fc9-2-1.jpg[/IMG]]("http://i164.photobucket.com/albums/u32/garnettf/pti-seb-screesnhot-fluxbox-fc9-2.jpg")

I love:
[LIST]
[*]The frameless terminal window (but how do you close/minimise it?)
[*]The translucent windows
[*]The awesome icons on the dock
[/LIST]

Any ideas on these?

---

### Post by mcduck on 2010-02-09
Frameless windows can be created with most window managers. Compiz allows you to do that (just exclude anything you want without borders in Window Decoration-plugin's settings), as do Fluxbox, Openbox and almost all the others. You'd usually close (and move, resize etc.) them by a keyboard shortcut, or from any panel you might be using.

Transparent windows require you to run some compositing manager. Compiz is the most common one, but if you want to use some other window manager you'd suuaally go with xcompmgr. Which by the way also works without graphical acceleration, so it's usbale on older computers as well. As long as you are ready to take the performanc hit from cmpositing with your CPU. In that screenshot the compositing must be done with xcompmgr since the window maanger clearly is Fluxbox.

The dock icons lok like they are from the Buuf icon theme. At least the style is very similar. Bit of a Linux classic.. ;)

---

### Post by Garnett on 2010-02-09
Wow! Awesome.Thanks.

So Fluxbox and Openbox are Windows managers like Compiz? And xcompmgr is another one. Blimey.

---

### Post by mcduck on 2010-02-09
Fluxbox and Openbox are window managers. Of course there are many others as well.

Compiz is a window manager that includes a compositing manager. (plus a framework for plugins, which allows it to do all kinds of fancy effects and animations)

..and xcompmgr is just a compositing manager, so you can use with any window manager you want to.

---

### Post by oshunluvr on 2010-02-10
Looks somewhat like E17 - Enlightenment to me...

---

### Post by falconindy on 2010-02-10
> **oshunluvr said:**
> Looks somewhat like E17 - Enlightenment to me...
You can plainly see 'Fluxbox' on the menu in the screenshot. Openbox, fluxbox, blackbox (and a few minor others) are all fairly similar.

---

### Post by 3Miro on 2010-02-10
It might be easier to just use Gnome + Compiz + Awn manager in Ubuntu. Since Gnome + Compiz is set up by default and Awn is installed directly from the repos. Then you need to play with compiz config setting manager (install it from Synaptic) and the Gnome panels (maybe gconf-editor as well). You will not get 100% the same desktop, but it will be close and probably easier (also probably slower all three components are known to eat resources).

---

