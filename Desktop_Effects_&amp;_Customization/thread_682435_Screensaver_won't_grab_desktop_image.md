---
title: "Screensaver won't grab desktop image"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by noremac on 2008-01-30
I searched around for this problem and saw some other people ran into this problem, but it seemed they are all from years ago, and some were never solved.

As my screensaver, I would like to display my desktop in some fashion. Either the AntSpotlight or Flipscreen. First in gnome-screensaver when I tried, it wouldn't work(it would just display two random images). And it seems I can't find the option or an advance tab to tell it to grab the desktop image rather than these two random images (I have dual screen setup). 
So I installed XScreensaver and use it to get an advance tab and selected the Grab Desktop Image box. But to my dismay, it still would not work. I either get an Ant just turning around back and forth on a black screen, or I get an empty white boarder that starts doing flips. No desktop image in either. The preview will show the XFlame but nothing in the actual screensaver. 

Any thoughts? Thanks in advance.
-Cameron

---

### Post by noremac on 2008-02-04
Anyone, Anybody?

---

### Post by papabean on 2008-05-25
I know this is a few months old, but I find myself in the same predicament.  I'd like some of the screensavers (Flipscreen3d, for example) to grab a snapshot of my desktop rather than wherever it's getting it's current image.

SOLVED:  Install *xscreensaver.* ```
sudo apt-get install xscreensaver
``` Then launch *xscreensaver-demo* whichever way you'd like.  Don't start the daemon if asked.  Click the *Advanced* tab at the top.  From there, you can choose *Grab Desktop Images*.

I unchecked the option to use the wallpapers in /usr/share/wallpapers.  Mind you, I'm using KDE, but this set the option in Kscreensaver so now Flipscreen3d flips my desktop around, GLeidescope reflects my desktop in crazy patterns and XAnalogTV makes me want to smack the side of my monitor.  :)

---

