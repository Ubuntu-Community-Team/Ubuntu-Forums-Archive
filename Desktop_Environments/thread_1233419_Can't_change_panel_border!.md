---
title: "Can't change panel border!"
date: 2009-08-06
forum: Desktop Environments
---

### Post by quadratini on 2009-08-06
Hi, I'm going nuts trying to figure this out and I know it's something simple. I'm trying to remove the tan panel border that divides it and the screen or at the very least change it's color/transparency so that it blends in with the background. Here's my gtkrc code and have a look at my screen shot - that tan line divides the panel and the desktop and looks like crap. Should be simple right? Help!
 
#############################################################################
# Prelighted Widget Style
#############################################################################
style "prelights" {
bg[PRELIGHT] = "#627EBD"
fg[PRELIGHT] = "#FFFFFF"
}
widget_class "*MenuItem*" style "prelights"
widget_class "*Toolbar*" style "prelights"
widget_class "*Scrollbar*" style "prelights"
widget_class "*Scale*" style "prelights"
widget_class "*Button*" style "prelights"
widget_class "*Progress*" style "prelights"
style "panel"
{
bg_pixmap[NORMAL] = "Veron08.png"
fg[NORMAL] = "white"
xthickness = 4
ythickness = 3 
}
widget_class "*Panel*" style "panel"
widget "*Panel*" style "panel"
class "*Panel*" style "panel"

---

### Post by quixote on 2009-08-07
That's a gorgeous toolbar!  I'm jealous.  The ochre line looks to me like a leftover from the ubuntu default desktop.  ??  Is that a possibility?  I wonder if it would be possible to kludge something by telling the default desktop you want a 100% transparent panel, and then going ahead with your customization?  Just a wild and crazy guess.

---

### Post by quadratini on 2009-08-10
Thanks, I figured it out. The solution was:
 
bg[NORMAL] = "black"
 
Matches my black background...

---

### Post by quixote on 2009-08-10
I thought it was probably going to be something showing through from the default desktop.  By the way, where did you enter that line?  I.e. which file and where is it?  That looks like a news-I-could-use method :D.

(Later update: Oh, wait, in the gtkrc file, of course.  D'oh!)

---

### Post by quadratini on 2009-08-10
In the panel section. Check out [http://orford.org/gtk/](http://orford.org/gtk/)
 
It has some excellent samples and explanations on customizing gtkrc (including where to put that line)

---

### Post by quixote on 2009-08-10
Great link.  Thanks!

---

### Post by quadratini on 2009-08-11
No problem!

---

