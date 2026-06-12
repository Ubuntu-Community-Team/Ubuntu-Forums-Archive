---
title: "Something wrong with Gnome?"
date: 2015-01-07
forum: Desktop Environments
---

### Post by salmichaels on 2015-01-07
For some reason I've been unable to access preferences or make any adjustemtns to the task bars in gnoma flashback. I'm not sure what happened. I attached a screen shot of what happens when I click on them: [ATTACH=CONFIG]259084[/ATTACH]

You see it just has that selection and "always on top" is the only thing I can choose, and that doesn't even do anything.

---

### Post by deadflowr on 2015-01-07
What keybindings did you try.
I thought you needed to do alt+rightclick, or super+rightclick, or ctrl+rightclick to access the panel controls...

---

### Post by salmichaels on 2015-01-07
Right, that's what I've always done, and the only thing that comes up now is that's in that screen shot. It's bazzah...

---

### Post by deadflowr on 2015-01-07
It's also not super+alt+rightclick?

---

### Post by salmichaels on 2015-01-07
I'm doing the same thing I've always done, and *all* it does is what I show you in the screen shot. Everything else is dandy, but I can't adjust any of these bars.

---

### Post by CantankRus on 2015-01-08
The key is super+alt+rightclick.
Are you in the compiz or metacity fallback session?
```
echo $DESKTOP_SESSION 
```

---

### Post by salmichaels on 2015-01-09
Wait a second, you're right. The key *is* super+alt+rightclick. 

But why???????????? Last week it was just alt right click. 

This is so, so, so annoying. 

I can also say that the alt + tab setting I had to toggle through windows? gone. 

I haven't changed anything. I might have authorized an update (they come in every other day) and that did it, but again, WHY?????

---

### Post by deadflowr on 2015-01-09
alt+rightclick = metacity's way
alt+super+rightclick = compiz's way.

---

### Post by kansasnoob on 2015-01-10
> **deadflowr said:**
> alt+rightclick = metacity's way
alt+super+rightclick = compiz's way.

+1! There are two flashback sessions available, Flashback with the Metacity window manager and Flashback with the Compiz window manager:

[http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682)

They perform in quite different manners.

---

