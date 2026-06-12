---
title: "changed grid settings in compizconfig, system toolbar no longer functioning properly"
date: 2014-07-30
forum: Desktop Environments
---

### Post by madisunnyd on 2014-07-30
So basically what I'm trying to accomplish is turning off the mouse gestures that resize windows i.e. when you drag a window to the left side of the screen it will fill up half the screen, drag it up it will go fullscreen etc. And enable some keyboard shortcuts that do the same thing. I was messing about under Window Management because I wasn't really sure what all of the options did. Couldn't tell you everything I enabled/disabled.

I'm pretty sure I put everything back to default except in Grid, where I disabled all of the options under the Corners / Edges tab so that the mouse gestures are disabled and the keyboard shortcuts are set up under Bindings. This achieved what I wanted, but now the system toolbar isn't functioning properly. Instead of showing the close/maximize/minimize buttons, menu bar tabs, or title of the active window, it's just blank. So when windows are maximized, those functions can't be accessed and the window can't be moved unless I use keyboard shortcuts to resize the window. But it isn't consistent. It's like a 50/50 chance every time I open a window whether or not it's going to work. I can't find any rhyme or reason behind when it will or won't work. 

I haven't done anything besides change the settings in CompizConfig. Is it possible I could reset it to default settings and that would fix the problem. And if so, how would I do that?

[B]EDIT

[/B]
Nevermind. I was able to figure out how to reset compiz using this command: 
[COLOR=#555555][FONT=consolas]dconf reset -f /org/compiz/[/FONT][/COLOR]

---

### Post by deadflowr on 2014-07-30
> [COLOR=#000000] Is it possible I could reset it to default settings and that would fix the problem. And if so, how would I do that?[/COLOR]

Generally you would go to the ccsm side panel > preferences > reset to defaults.
after the reset, which should cause a screen debacle for a minute(don't worry it should reset itself) you might need to check on the unity plugin to make sure it is enabled.
Also check the other plugins as well, but the unity one is the one I have found to not get enabled after a reset.

---

