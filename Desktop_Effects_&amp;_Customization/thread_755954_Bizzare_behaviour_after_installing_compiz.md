---
title: "Bizzare behaviour after installing compiz"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by paulig2001 on 2008-04-15
Hi,

I recently installed the various packages required to enable compiz on kubuntu. I tried to get it going but it gave me an error to do with xgl and wouldn't work.

I gave up and left it, but the next time I turned on my computer, for some reason, my default font had changed, everything was really slow to render and also for some reason when i clicked the log out button I could no longer shut down or restart, just log out.

Any idea what on earth could possibly be going on here?

-Paul.

---

### Post by Zorael on 2008-04-15
Curious.

As for slow-to-render, perhaps your video driver got changed somewhere along the road? What videocard are you using? And which packages did you install to get compiz running? You should only need compiz-core and compiz-kde along with its dependencies to get it running, some more if you want plugins, which you likely do. You shouldn't install xserver-xgl if you have an Nvidia card. And I seem to vaguely remember that you shouldn't if you have an ATI card either (instead going with fglrx), but don't quote me on that.

The can-only-logout thing can be easily fixed; somewhere in the administrative settings there's an option to allow for more shutdown options. I can't look into it right now, since I'm on a l0sedows box. As for why it changed, I've no idea.

---

### Post by paulig2001 on 2008-04-24
Got rid of xserver-xgl. Did the job. Bizarre stuff altogether. Fixed the logout thing and everything.

So the moral of the story is obviously don't install xserver-xgl unless you actually know what its for...

---

