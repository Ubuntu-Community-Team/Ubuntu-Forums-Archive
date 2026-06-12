---
title: "Something like the Beryl put plugin without Beryl?"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by Soybean on 2007-06-11
I've been using Beryl on my desktop at work for a while now, but my system isn't really *quite* good enough for it, and I finally got tired of the reduced performance and occasional freezes. It's not really worth it when you have to turn off most of the animations, anyway. ;) So I switched back to metacity, and everything is working better, but now I'm experiencing withdrawal symptoms. I miss the cube, I miss the scale plugin... but most of all, I miss the "Put" plugin. I had no idea how dependent I had become on the ability to fire windows to the corners or the center of the screen with a press of a button. 

For anyone who's not familiar, with this plugin enabled, Super+<any number key> will move the current window to a position on the screen that corresponds to the number's position on the number pad. Super+7 moves it to the top-left, Super+5 moves it to the center, etc.

So my question is, is there a way to get similar functionality without a 3d window manager? Scale and cube use some fancy graphics tricks, of course, so I know I'll have to get by without them. But Put seems like it ought to be pretty straightforward. Does one of the popular window managers have a similar feature, or is there a way to add this functionality in metacity? I suppose I could get the metacity source code and try adding it myself, but I figured it might be better to ask here for an easier solution first. :D I tried searching, but the words "like," "put," and "plugin" are pretty common, and on these boards, "beryl" doesn't narrow things down much either.

---

### Post by Soybean on 2007-06-13
So I have continued trying to find a solution on my own, and I figured I'd post an update on the off chance that anyone else was interested.

The first thing I found was some of those "hidden" metacity configuration options in gconf-editor. There are keybindings available for moving windows to any of the 4 corners or 4 screen edges.
Problems:
1) there was no "move to center"
2) the move was always relative to the current window position -- fine for the corners, but it wasn't what I was looking for for the edges
3) poor support for multiple monitors (I'm using TwinView)

Next, since I was otherwise happy with Metacity, I looked into the possiblity of adding the functionality myself. Metacity is open source, and I'm a programmer, so it seemed reasonable enough. I quickly decided that custom-patching the Metacity source directly wasn't the way to go -- mainly because it would be a big hassle any time they released an update. Next I considered making a "plugin" kind of like Devil's Pie that would do what I wanted, and spent a few hours working on that, but in the end I decided it was too big of a project for me. I don't generally do GUI programming (sometimes I'll throw a web frontend on something as an afterthought, but it's rare), so learning all about glib, gdk, gtk, xlib, libwnck, etc, etc for a simple feature seemed like too much. The moving aspect would likely have been easy enough, because I could probably have just pillaged the window-moving code straight from Devil's Pie, but learning enough to catch the keypresses in an appropriate way would've been a lot of work.

So, I said, "forget Metacity, there are lots of window managers out there!" Here are a few that I tried:

**Kwin** - couldn't find anything close, but I'm not really familiar with the KDE way of thinking. I wouldn't be surprised if the feature was there, just in some place that I didn't think to look.

**Ion** (and other tiling window managers) - I'm not sure I would be happy with how sterile these all look, but they do have the general feature of being able to put a window where you want it on the screen quickly using the keyboard. There's a bit of a learning curve, too, but it doesn't look insurmountable. I may actually come back to one of these later, since I think it might make me "feel" more productive in the long run.

**OpenBox** - what I'm using now. By setting up appropriate keybindings in rc.xml, with "MoveToEastEdge" actions and the like, I was able to get the effect I wanted... on a single monitor. OpenBox supports multiple monitors in general, but these move actions are a bit flaky. "MoveToCenter" always goes to the first screen, and if you move to the edge between two screens and then hit the button a few more times, your window will hop across the boundary in a few steps and end up on the other monitor. I'll probably either file a bug report on this one, or try to patch it myself.

Todo: Check FVWM. I just started looking at this one before I went to bed last night. It looks like it would take a few days' work to get it set up just right, but it's so configurable that I'm thinking it *must* be able to do what I want somehow! ;)

Anyway. I'll probably update this post one more time in a few days, with my final decision (likely either tweaked FVWM or patched OpenBox). I realize that there's not much interest in the subject  -- stopping using Beryl is atypical enough, and I wouldn't be surprised if I were the only such person to miss the Put plugin more than everything else. But I figure it's good to post my findings anyway, just in case. Some day, someone may have the same question I did, and if that theoretical future person finds this thread, he or she will be sure to appreciate my follow-ups. :D

---

### Post by ThomasAdam on 2007-06-13
> **Soybean said:**
> Todo: Check FVWM. I just started looking at this one before I went to bed last night. It looks like it would take a few days' work to get it set up just right, but it's so configurable that I'm thinking it *must* be able to do what I want somehow! ;)

It will - see [http://fvwm.lair.be](http://fvwm.lair.be)

-- Thomas Adam

---

### Post by airtonix on 2007-06-22
try using : 
 brightside - screen corner actions for mouse
 devilspie - control windows

---

