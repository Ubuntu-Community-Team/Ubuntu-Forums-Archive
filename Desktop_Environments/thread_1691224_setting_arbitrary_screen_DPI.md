---
title: "setting arbitrary screen DPI"
date: 2011-02-19
forum: Desktop Environments
---

### Post by lvm on 2011-02-19
kubuntu 10.10, monitor is a TV. When screen DPI (system settings-application appearance-fonts-force fonts DPI) is set to 96 or 120 fonts at default sizes are too small - remember, it is a TV viewed from a distance. Setting font sizes to about 15-17 helps, unfortunately not all programs - e.g. system settings themselves, honour these settings. And when I set fonts DPI to disabled, at default sizes fonts become way too big, to make fonts look normal I have to set font sizes to about 5-6, unfortunately some programs e.g. seamonkey use screen DPI to set sizes of all controls - icons, tabs etc, and they become enormous. No other values except 96, 120 and disabled are available.

My question is: how can I set screen DPI to something bigger than 120 but less than the value it gets set when it is set to disabled?

---

### Post by wildweathel on 2011-06-07
Bump and threadjack since this seems to be the most recent "Why does KDE make DPI hard?" thread.

Rant:

I think the most common understanding of DPI/resolution/font-size/etc is summed up by the phrase "screen real-estate:"

- I buy an expensive screen with a high resolution so
- I can sit close to it
- and fit lots of tiny text on it.

Most screens have a physical DPI around 100 or so, the OS (originally Windows) can safely assume a fixed DPI, and most people sit close to a monitor.  Higher resolution = bigger screen = bigger field-of view.

Monitor makers like it because it gives them something to charge for.

Print artists want the ability to make the image-on-screen match the physical size of the image-in-print.  Thus, monitors have the ability to tell the OS what they're physical size is and everything works for the graphic designer.  I understand this is OS X's behavior.

Finally, there's the approach inherited from film projection / TV / home cinema: the larger the screen, the further back and larger the sweet spot becomes.  The higher the resolution, the finer and sharper--not smaller--the image.  Since the viewer sits back, a 24" screen doesn't cover any less or more viewing area than a 36" screen.  Physical size doesn't matter.  But, an image on a 1200-line screen should be twice as many pixels high as on a 600-line screen.  

For this user, 1 point is not 1/72 of an inch.  It's some fraction of the screen height.  Exactly which fraction should be adjustable and determines how big or small *everything* is: text, applications, icons.

If an OS can satisfy this last user, it can satisfy the first.  He can just crank the scale down so everything's as small and blurry as he can stand.  Or, if your big TV/monitor is halfway across the room, crank things up and enjoy big, crisp, easy to read text.

There's a magic point here screen size matches print size and the OS should make it button-push easy to set things up that way if the user wants.  Everyone would be happy and peace would reign.

But, KDE doesn't make things easy; you either get (bad) OS X aping or a more authentic Windows aping with forced DPI.  

---

Technical:

So, how do you set DPI in KDE?  Well, if you want either 96 DPI or 120 DPI, you're in luck. System Settings -> Application Appearance -> Fonts -> Force Fonts DPI

But, I want my screen to hold as much text as an 8-inch tall piece of paper: vertical resolution, 1200 dots / 8 inches = 150 DPI.  No luck there. 

I've tried setting ScreenSize to 200mm in xorg.conf.  xdpyinfo still gives the physical screen size.  Setting that with xrandr --fbmm at least changes what xdpyinfo returns, but KDE ignores that.  

still looking...

--- 

In /etc/kde4/kdm/kdmrc
ServerArgsLocal line
add -dpi XX to the end.  

Changes text size and xdpyinfo, but doesn't rescale icons nor do all applications obey.  In particular, Google Chrome is hard-coded to 96 DPI.

---

