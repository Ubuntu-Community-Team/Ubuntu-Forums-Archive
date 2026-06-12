---
title: "Terminal Size"
date: 2009-05-27
forum: Desktop Environments
---

### Post by CarlosinFL on 2009-05-27
When I open Gnome Terminal application to function in bash shell, my terminal always opens in a specific size and in the top left corner of my screen. Is it possible when I open 'Terminal' to have it open in full screen.

---

### Post by kerry_s on 2009-05-27
> **Carlwill said:**
> When I open Gnome Terminal application to function in bash shell, my terminal always opens in a specific size and in the top left corner of my screen. Is it possible when I open 'Terminal' to have it open in full screen.

lol, to hard to click the button or press f11? ;)

---

### Post by CarlosinFL on 2009-05-27
Not hard, just annoying...

Why not make it the default and save yourself a button click...

---

### Post by boof1988 on 2009-05-27
> **Carlwill said:**
> When I open Gnome Terminal application to function in bash shell, my terminal always opens in a specific size and in the top left corner of my screen. Is it possible when I open 'Terminal' to have it open in full screen.

Here are two links that may have some useful information for this.

[http://ubuntuforums.org/showthread.php?t=188948](http://ubuntuforums.org/showthread.php?t=188948) and [http://ubuntuforums.org/showthread.php?t=465670](http://ubuntuforums.org/showthread.php?t=465670)

I used the second one (IIRC) to learn how to use the "--geometry" option to make a launcher to open a terminal with specific position and dimensions.

I would imagine (hope) that the "--geometry" option could be added to menu launchers as well??

HTH

---

### Post by drs305 on 2009-05-27
My shortcut uses this. You can play with the settings:
```

gnome-terminal --geometry=140x50+50+50

```
The 140 is width, the first 50 is number of lines, and the last two are x and y offsets from the borders.

---

### Post by boof1988 on 2009-05-27
> **drs305 said:**
> The 140 is width, the first 50 is number of lines, and the last two are x and y offsets from the borders.

Just wanted to clarify further (I hope this is correct)...

140 -> ~number of *characters* wide
50  -> number of *character* lines
x   -> number of *pixels* offset from left edge of screen
y   -> number of *pixels* offset from top edge of screen

Someone please correct me if this is wrong.

---

### Post by CarlosinFL on 2009-05-27
Awesome guys!

---

### Post by Nythain on 2009-05-27
you coudl install terminator and harness teh power of its awesome config file ( wich gnome-terminal probably has one of buried somewhere deep in the bowels of your home folder anyways) or switch to a better terminal emulator and use the .Xdefaults :P

---

