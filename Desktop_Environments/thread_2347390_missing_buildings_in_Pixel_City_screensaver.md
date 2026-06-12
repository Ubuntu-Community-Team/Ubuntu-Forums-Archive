---
title: "missing buildings in Pixel City screensaver"
date: 2016-12-24
forum: Desktop Environments
---

### Post by jamesjones01 on 2016-12-24
I'm using Ubuntu 16.10, running Cinnamon, and I have an nVidia 960 graphics card running the 367.57 driver. This morning I decided to set it to run the GL screensaver "Pixel City", which generates a random nighttime cityscape and flies through it. I went into preferences and selected it under "Screensaver", and sure enough, it started up... but the buildings were missing. Here's an example of the sort of thing one should see from Pixel City (with the company name signage turned off, apparently):

[IMG]http://lh5.ggpht.com/_S0f-AWxKVdM/SgMG0Zw4wII/AAAAAAAAINE/ATbbqW-WJdE/pixel-city%5B4%5D.jpg?imgmax=800[/IMG]

Unfortunately, Google Photos's public access shortened URLs don't explicitly mention a file, and hence doesn't show a file extension--so the forum won't show an image inline via such a link. This will get you to a screenshot of how it looks on my system: [https://plus.google.com/photos/photo/109435516894972872684/6367659386716563810?icm=false&authkey=CMO9l9CXv_uzmwE](https://plus.google.com/photos/photo/109435516894972872684/6367659386716563810?icm=false&authkey=CMO9l9CXv_uzmwE)

As you can see at the link, there are very few buildings, and some signage lettering cropped and hovering in the middle of the air.

Is this a known issue? Any suggestions on how I can get the screensaver to display properly? I suspect that other OpenGL users such as games will trip over whatever is causing this.

---

### Post by mc4man on 2016-12-26
Try setting Effects to either "Effect None" or "Effect Color Cycle"

---

### Post by jamesjones01 on 2016-12-28
Where do I do that? The cinnamon screensaver settings let one choose a screensaver, but doesn't appear to give one access to individual screensaver settings, which effects presumably is.

(Actually, [https://github.com/linuxmint/cinnamon-screensaver/issues/105](https://github.com/linuxmint/cinnamon-screensaver/issues/105) may be relevant here; it's titled [FONT=arial]"[COLOR=#333333]Configuration options or saner defaults for xscreensaver screensavers?" Perhaps the thing to do is to switch to xscreensaver--the blurb for cinnamon-screensaver one sees when looking at it in synaptic shows text very reminiscent of the infamous original gnome-screensaver about "the ability to lock down configuration settings"; has history in the form of [https://bugzilla.gnome.org/show_bug.cgi?id=316654](https://bugzilla.gnome.org/show_bug.cgi?id=316654) repeated itself?[/COLOR][/FONT]

---

### Post by jamesjones01 on 2016-12-28
Solved, for my purposes, by disabling cinnamon-screensaver, which doesn't give you any control over individual screensaver settings (yes, Mr. Santayana, you were right), and using xscreensaver instead. Pixel City looks just fine now.

---

### Post by maxreason2 on 2017-03-29
Good to know jamesjones01.  I had the same problem.  I killed the cinnamon-screensaver process, then installed xscreensaver.  But when I run xscreensaver it does not list pixelcity (which I did install and would run before with cinnamon-screensaver), but had the same defects as you mentioned.  Sooo... how do I get xscreensaver to include the pixelcity screensaver so I can select it as the xscreensaver screensaver?

---

### Post by Dennis N on 2017-03-29
> **maxreason2 said:**
> Good to know jamesjones01.  I had the same problem.  I killed the cinnamon-screensaver process, then installed xscreensaver.  But when I run xscreensaver it does not list pixelcity (which I did install and would run before with cinnamon-screensaver), but had the same defects as you mentioned.  Sooo... how do I get xscreensaver to include the pixelcity screensaver so I can select it as the xscreensaver screensaver?

In Ubuntu, just xscreensaver is not enough. You need these packages:
xscreensaver
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra
rss-glx

Pixel City is in rss-glx. Follow the directions in /usr/share/doc/rss-glx/README to get the rss-glx screensavers to show up in xscreensaver's list.

If it does not run smoothly, change Settings to: Effect None

---

### Post by maxreason2 on 2017-03-30
Thanks!  Runs great... especially nice with colors.  Wish it included music like in the youtube "making of pixel city" video... but I guess that's not the idea of screensavers!  But could be an option... maybe.

All those files were installed, but I did have to add pixelcity and skyrocket to the .xscreensaver file.  That was the trick.  Thanks!

---

