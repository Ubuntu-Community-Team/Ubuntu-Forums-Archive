---
title: "Azulejo - Easier window tilling for gnome and other non tilling DEs"
date: 2011-03-29
forum: Desktop Environments
---

### Post by picox on 2011-03-29
Hey all,
hope I'm posting this in the right place...

After trying many tilling window managers, I came to the conclusion that they are not really what I was looking for. I needed something less intrusive that would provide the same kind of power but would not break my current workflows.

So, I decided to roll out my own window tilling/resizing solution.

I called it *Azulejo* and it's highly inspired by [winsplit revolution]("http://www.winsplit-revolution.com/"), which I use when on Windows.

If you're wondering what this does, maybe the current keymap may help:

```
Super+2		Place two windows side by side
Super+3		Place a window on the left half of the screen and two on the right half
Super+4		Arrange four windows two by two
Super+R		Rotate windows' positions i.e. cycle windows
Super+H		Resize and move current window to the left
Super+K		Resize and move current window to the right
Super+Y		Resize and move current window to left upper corner
Super+U		Resize and move current window to right upper corner
Super+B		Resize and move current window to left lower corner
Super+N		Resize and move current window to right lower corner
```

**Grab the source with mercurial:**
```
hg clone https://bitbucket.org/plainas/azulejo
```

**deb package, info & updates:**
[http://lamehacks.net/blog/tag/azulejo/](http://lamehacks.net/blog/tag/azulejo/)

This is still very experimental and minimal, but I believe it can already be very useful. 


**Technical stuff for toolkit geeks:**
This is an extremely minimalist application that uses python bindings to wnck for all its window manipulation needs.
This works fine with some glitches here and there. If you have good knowledge of xlib, wnck, or other such things, you're encouraged to throw some suggestions/criticism.

---

### Post by K.Mandla on 2011-03-31
Moved to Desktop Environments.

---

### Post by Gourgi on 2011-04-06
looks good in the specs although i didn't tried it yet. does it play nice with compiz ?

---

### Post by picox on 2011-04-09
> looks good in the specs although i didn't tried it yet. does it play nice with compiz ?

I don't know. One of the reasons why I wrote this is because a couple of alternatives out there depend on compiz

Maybe you could try it out and give some feedback.

As a side note, I am starting to notice that those who find this useful tend to use simpler DEs such as openbox or xfce.

---

