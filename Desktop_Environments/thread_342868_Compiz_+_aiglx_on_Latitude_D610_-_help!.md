---
title: "Compiz + aiglx on Latitude D610 - help!"
date: 2007-01-20
forum: Desktop Environments
---

### Post by Kensey on 2007-01-20
OK, I think I give up.  I just upgraded my laptop to Edgy in an effort to try this nifty compiz thing I keep hearing about.  After a night and a morning of reading various FAQs, HOWTOs, forum threads, and blog posts, it seems I know less than when I started.

First, the feasibility question: is it even *possible* to make the stock Edgy compiz run on Edgy with an Intel GMA915 video chipset?  If it's not, we can all go home and I'll just deal with it.  I don't really want to add third-party repositories to my apt sources.list, especially since that seems to have been a major source of issues for the Dapper -> Edgy upgrade.

Second, assuming it is feasible, how do I do it?  I tried just running compiz under the standard X server settings after tweaking xorg.conf.  That didn't work; when I ran compiz --replace all my titlebars would disappear and compiz would complain about GLX_EXT_texture_from_pixmap not being supported.  Then I tried changing the X server in gdm.conf to Xgl, which started up, and when I ran compiz with the indirect-rendering command-line at the end of the man-page, it actually sort of half-worked -- I got no titlebars still, but inactive windows became half-transparent.  In an effort to fix the titlebar issue, I ran gnome-window-decorator and the whole X session promptly crashed and restarted.

That's where I am right now -- currently I'm still in the Xgl server, but on the next gdm restart it'll be the standard again.  glxgears reports a framerate of ~90fps, but the animation is very slow and choppy (I noticed slowness starting firefox too -- the zoom-rectangle animation is also slow and choppy).

Is there any way out of this maze?  Should I just dump compiz and call it a day?

---

### Post by Kensey on 2007-01-21
Hm.  Well, I got it working (turns out the Standard server was the one I wanted anyway), but now I want to turn off some of the admittedly nifty effects to speed things up.  Which effects burn up the most CPU?

I'm thinking of turning wobbly-windows and the rotating-cube effect off, and leaving the window and menubar translucency on.  Wobbly-windows in particular seems to interfere with menus, tooltips and the volume OSD -- whenever a menu pops down I have to wait for it to stop wobbling before I can actually use it, for example.  I guess it's time to start digging around in gconf.

---

