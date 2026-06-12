---
title: "Different Background Images on each workspace (Beryl)"
date: 2006-12-06
forum: Desktop Environments
---

### Post by kelbizzle on 2006-12-06
I know everyone over at bery-project.org say this isn't beryl's task...It should be. At least I think so. So I was curious to know if anyone has been able to do it at all?

---

### Post by yatt on 2006-12-06
> **kelbizzle said:**
> I know everyone over at bery-project.org say this isn't beryl's task...It should be. At least I think so. So I was curious to know if anyone has been able to do it at all?
I know one person who did, but he lost all his desktop icons becasue all beryl can due is cover the desktop with a picture.

---

### Post by kelbizzle on 2006-12-06
thats not cool. I wish something comes from left field soon.

---

### Post by jstroot on 2006-12-13
I just posted to another thread, but this one is better.

CALLING ALL CARS!!

I want to do this so bad I can TASTE it!!!!1

If ANYONE has ANY ideas on how to accomplish this, please, let us know.

Thanks ,

Jstroot

EDIT: There is a program called [Wallpapoz]("http://wallpapoz.akbarhome.com/index.html"), that supposedly works in gnome to change desktop backgrounds automatically. Author of site claims that the next release will have support for compiz/beryl. I am Jack's anticipation!!!!!

---

### Post by mcduck on 2006-12-13
if you are running beryl there's app called xwinwrap that allows you to run screensavers and movies on the desktop.

You can use that with the GLSlideshow screensaver to get a  nice desktop slowly fading from one wallpaper to another :D

```
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glslideshow -window-id WID -duration 30 -pan 15 -fade 10 -clip -delay 50000
```

---

### Post by jstroot on 2006-12-13
"if you are running beryl there's app called xwinwrap that allows you to run screensavers and movies on the desktop."

That is fantastic, if that is the effect you're going for.

Now I hope I don't start some weird trend by giving my idea up, but telling you might help give a better idea of what I'm trying to accomplish.

I want my desktop cube to look like the hellraiser puzzle box. So, when I start manually rotating the cube with the mouse, it will zoom out, and voila!! A bitchin hellraiser puzzle box!! With the new cube transparency plugin, I am sure it will look great (with good looking scans of the puzzle box, of course.)

So, if you see anyone a few months down the road with a hellraiser cube in ubuntu, you heard it here first!!!! (Or maybe not.)

---

### Post by mcduck on 2006-12-13
That's very cool idea. Somebody here had a Borg cube (from Star Trek) with a nice space pic as skydome image and that was nice too..

Anyway, getting different wallpapers for different desktops is a bit tricky thing.. In gnome Nautilus is the app responsible of drawing the wallpaper and desktop icons, but even if it would get support for having different wallpapers on virtual desktops that probably wouldn't work with Beryl as Beryl doesn't have virtual desktops like normal gnome has but instead one desktop with multiple virtual viewports (there's a difference..).

Then again, if Beryl would do the wallpapers it'd have to draw them on top of the Nautilus desktop, and that would mean loosing all icons on your desktop..

---

### Post by Vord on 2007-02-01
I know this is an old thread, but I could definitely live with having beryl draw desktops over nautilis, since I don't have any desktop icons, could somebody explain how I'd do this?

---

### Post by kelbizzle on 2007-02-12
Yea I havn't tried any of the xwinwrap tricks. Although I seen a video where someone had the matrix screensaver on they're desktop. I do admit it looked pretty sweet. I did see that the beryl team is working on [BDE heres the post about it.]("http://dev.beryl-project.org/~racarr/uncategorized/15/beryl-desktop-manager-2/")

---

