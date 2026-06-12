---
title: "Gnome Panel not controlled by Compiz?"
date: 2008-12-13
forum: General Help
---

### Post by bishounen on 2008-12-13
Am I missing something here?  Despite all my experimentation with Compiz Fusion in Ubuntu 8.10, I cannot get it to control the gnome panel, and thus make all my window elements theme together smoothly.

Additionally, the "minimize" effect absolutely REFUSES to work, unless I use the "minimize effect" choice in CCSM, which them eliminates all the other effects for the windows!  GRRR!

I MUST be doing something wrong, because I simply cannot get Compiz Fusion to function as I have seen it used in so many YouTube videos and online demos.

HELP!

---

### Post by gettinoriginal on 2008-12-13
No, compiz does not control anything about your panel.  And getting compiz to do the things that you see on youtube takes alot of tinkering, but can be achieved.  You may want to install emerald, it allows for more contiguous settings.

Your best bet is when you want to make a certain thing happen is the following:

In google search: compiz settings
In google search: ubuntu forums compiz (selected action)

---

### Post by bishounen on 2008-12-14
Well, I already have Emerald installed, and am using the Compiz Fusion Icon in my tray so I can control everything.  It just seems that there is alot of overlap in what some choices in there do, and some conflicts among items.  I guess it's still a work in progress.  I just wish it was easier to change EVERYTHING with a single click.  I hate having to manually reconfigure all the different elements in 15 different places.

And, IMHO, Compiz SHOULD take over the panel.  The Panel is part of the desktop look.  Indeed, Panel is the first thing (or things, if you keep the top and bottom ones in Gnome)  that you see on the desktop besides the background.  If it doesn't match the window decorations, it looks unprofessional.

Maybe I should drop a suggestion to the Compiz people.  Although I find it hard to believe that they haven't had that suggestion already.

On my second question, any way to get the advanced effects to actually DO SOMETHING when you minimize a window?  All I get now is the window blinks away.  Basically as if Compiz wasn't even running and I was having Metacity do the minimization.  Any clue how to fix this?

---

### Post by gettinoriginal on 2008-12-14
Use animations to configure minimize window, it can flame, fold, airplane, or many other configs.  As far as the panel, that is gnome,  if you want compiz to control your apps and configs, you might consider awn or cairo-dock.  :p

---

### Post by bishounen on 2008-12-14
> Use animations to configure minimize window

Perhaps I wasn't clear.  I AM using "Animations" to configure the "minimize" effect.  The problem is it ISN'T WORKING.  I configure animations to minimize with "Burn" for example (and I've tried pretty much ALL the effects, with the same results.) and after closing out of "Animations"  I open a bunch of different windows, and one by one, minimize them all as a test.

The effect (regardless of the effect I choose) does NOT work.  The window simply disappears, as though Metacity was still controlling the minmising.

What could be causing this?

---

### Post by Wartender on 2008-12-14
when that happens i just reset the animation fields (the little brush icon), and i configure them again. that worked for me the last time this happened.

---

### Post by bishounen on 2008-12-14
> when that happens i just reset the animation fields (the little brush icon), and i configure them again. that worked for me the last time this happened.

That did it!  Thanks!

Now I'll just have to decide if I want to try Cairo dock.  I hated AWN.

Thanks guys!

---

### Post by Wartender on 2008-12-14
you're welcome :), glad i could help.

---

### Post by dryfly on 2008-12-14
jumping in on this thread...I have been toying with compiz...I believe I have it installed...but I do not see an icon to tweak adjustments??? any thoughts? Thanks...

---

### Post by ellalan on 2008-12-14
Install fusion-icon in synaptics.

---

### Post by gettinoriginal on 2008-12-14
You will also need CCSM and Simple CCSM from synaptics :p

---

### Post by gettinoriginal on 2008-12-14
Also just found gnome-color-chooser in synaptic, enables you to better configure your gtk things (ie panel, icons, desktop).  :popcorn:

---

### Post by dryfly on 2008-12-14
I got all the bells and whistles now...seems to be stressing my video card though...fun to play with,,,but not sure I will keep the hollywood version...thanks to all! CHeers!

---

