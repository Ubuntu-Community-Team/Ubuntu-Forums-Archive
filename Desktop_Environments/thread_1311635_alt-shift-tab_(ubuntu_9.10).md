---
title: "alt-shift-tab (ubuntu 9.10)"
date: 2009-11-02
forum: Desktop Environments
---

### Post by SomeIdiot on 2009-11-02
I just tried raising the visual effects level from none to normal and while it looks nice, there seems to be a bug with the alt-tab menu, in that you can't use alt-shift-tab to move backwards in the menu.

Is there any way to make this work? It's a bit of a game breaker for me unfortunately.

---

### Post by blur xc on 2009-11-02
> **SomeIdiot said:**
> I just tried raising the visual effects level from none to normal and while it looks nice, there seems to be a bug with the alt-tab menu, in that you can't use alt-shift-tab to move backwards in the menu.

Is there any way to make this work? It's a bit of a game breaker for me unfortunately.


Works fine for me, but I use super-tab and conversely shift-super-tab.  Install compiz config settings manager (search synaptic or apt-cache search) and you can define all your key-bindings for the different affects.  I personally use the shift switcher and the scale plugin to switch between open windows.

BM

---

### Post by jeromatron on 2009-11-03
It's not working for me either.

I'm updated on 32-bit karmic with normal effects enabled.  I have the nvidia graphics driver as well.

alt-tab works fine, but alt-shift-tab doesn't go backwards through that same list.

---

### Post by blur xc on 2009-11-03
Did either of you verify the key bindings in compiz config settings manager?


BM

---

### Post by tuwe on 2009-11-03
Hi,

to enable Alt+Shift+Tab, do the following:

* install compizconfig-settings-manager
* start it through System->Preferences->CompizConfig Settings Manager (or type `ccsm` in a terminal, do not confuse it with Simple CompizConfig Settings Manager)
* navigate to Application Switcher in the Window Management section
* enable your favourite key binding for Prev Window.

OR

* start gconf-editor
* navigate to apps->compiz->plugins->switcher->allscreens->options and set the value for prev_key to <Shift><Alt>Tab

You could probably even issue a gconf-tool command, but i don't know the exact syntax.

---

### Post by mozillalives on 2009-11-04
sweet - the compiz instructions helped me. Thanks.

and whoa - it might take me a little while to get used to the compiz version of alt+tab. But at least alt+shift+tab is back. :)

---

### Post by mcduck on 2009-11-04
> **mozillalives said:**
> sweet - the compiz instructions helped me. Thanks.

and whoa - it might take me a little while to get used to the compiz version of alt+tab. But at least alt+shift+tab is back. :)

There are at least three different Compiz plugins for this purpose, so if it's acting differently from what you are used to you are probably just using a different plugin than before.. :)

---

### Post by robinparriath on 2009-11-10
Here is a [solution in another thread]("http://ubuntuforums.org/showthread.php?t=1311047") that doesn't require additional install

Worked for me...

---

### Post by divyabdasar on 2010-06-07
I was working on compiz settings. after disabling the compiz settings ALT+TAB wasn't working on ma machine. 

After reading forums discussions then got the solution for it.

under 
System->Preferences->Keyboard shortcuts

under
windows managment->move between windows,using pop-up window---- set the shortcut key as alt+tab.

Then it worked :):):):)
Thank you opensource. thank you guys for sharing your knowledge..:):):):)

---

### Post by salterlee on 2011-05-18
Or I went into Compiz Config Settings  (System > Preferences), then "Window Management", then checked  "Application Switcher" and it started working again. Hope you've got it  sorted, but for anyone else who gets the problem, it's a good one to  try.

---

### Post by amireldor on 2011-07-17
i have a similar issue on 10.10. though i have the <alt><shift>tab setting on compiz, it won't work, and i guess it's because i have another language layout installed and the alt+shift switches between the two layouts.

still searching for solutions, will update if i find something interesting.

oh and if you know something about this i'd love to hear it :)

---

