---
title: "Compiz Fusion leave window outlines"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by themusicwave on 2007-10-31
I have been having a strange problem with Compiz fusion since the Gutsy update.

Sometimes when a window closes, Compiz still leaves the windows border.  it appears as an outline grayish square with no fill. It will not go away until I either turn off compiz fusion or restart gnome.


I have an Nvidia card with Nvidia drivers.  I also have avant, it all worked great until about a week ago.

Could this be due  settings???

---

### Post by Zorael on 2007-10-31
That sounds like something to do with your video card settings.

Could you post your xorg.conf file, perhaps? And the command with which you launch Compiz?

---

### Post by themusicwave on 2007-11-01
I think I fixed it but only time will tell.

I went under animations and chaned the window close event from Razr to vacuum.

The strange thing is when I close a window it still does the same action it used to, but doesn't seem to leave the outlines.

It's like compiz kind of ignores the settings I give it and does whatever it feels like.

---

