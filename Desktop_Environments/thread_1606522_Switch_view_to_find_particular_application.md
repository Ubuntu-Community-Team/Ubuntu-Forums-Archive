---
title: "Switch view to find particular application"
date: 2010-10-26
forum: Desktop Environments
---

### Post by cpbl on 2010-10-26
Hello. I would like to set up a hot key to switch the focus to a particular existing application. E.g. I often have an open terminal named "alpine". I would like to be able to press a key and have my view switch to the top-listed window with the name "alpine".

I am using compiz or etc, whatever is the default in Gnome/Ubuntu.

Thanks!

---

### Post by cpbl on 2011-02-06
Here are some things I will happily PAY YOU to implement or tell me how to set up.  Propose a price if you know how to solve one or more:


My window manager (compiz,…) does a very clever job of dealing with “full-screen” mode when I have an extended desktop, e.g. I can drag a window from a display with one size to a display with a different size, and it will spring back to full-screen in the new display. Pretty cool. But:

[LIST]
[*]I want a key binding to make the window full-screens (rather than full-screen), ie to span the space across the extended desktop, rather than just the portion covered by one display device.
[*]I want a key binding to make a window full-screen in the OTHER device of an extended desktop, ie to switch screens
[/LIST]
Also,

[LIST]
[*]I would like to set up a hot key to switch the focus to a particular existing application. E.g. I often have an open terminal named “alpine”. I would like to be able to press a key and have my view switch to the top-listed window with the name “alpine”.
Of course, I’d also like to see a better-working bounty system for Ubuntu or GNU/Linux development. I’ve ideas for that…
[/LIST]


(This is actually also a post at [http://cpbl.wordpress.com/2011/02/06/bounties-for-gnome-compiz-window-behaviour-improvements/](http://cpbl.wordpress.com/2011/02/06/bounties-for-gnome-compiz-window-behaviour-improvements/))

---

### Post by Krytarik on 2011-02-06
I don't know a solution for the fullscreen span thing, but for the second mentioned one (which is also mentioned in your initial post).

To switch to given window and give it the focus, you could simply use "wmctrl":
```
sudo apt-get install wmctrl
```Given the name of your window is "alpine", this is the command you would have to use:
```
wmctrl -a alpine
```To set it up for a keyboard shortcut (assuming you are running Compiz):
- go to "System -> Preferences -> CompizConfig Settings Manager -> Commands"
- add the command in the first tab, "Commands"
- assign a key combination in the "Key Bindings" tab

---

### Post by cpbl on 2011-09-29
> wmctrl -a alpine

Wow!! Thank you, Krytarik!!! 
I've set up a bunch of shortcuts. That works beautifully.

---

