---
title: "tiling wm"
date: 2009-08-20
forum: Desktop Environments
---

### Post by blur xc on 2009-08-20
I've been noticing the tiling window managers more and more- and is there a compiz plugin or effect that can do that in gnome?

I'm happy w/ gnome, and I like my compiz settings, and wouldn't trade them for a tiling wm straight across, but it'd be nice to have it in addition to the rest of my compizeffects.


I use SolidWorks and it has a settiing for tiling all open docs, which is very useful.  Should  be a standard issue item for any wm, imo.  Sadly, I spend a pretty decent amount of time in front of my windows pc aligning my open windows to be "just right", since it doesn't even have any snap to edges options.

BM

---

### Post by coldReactive on 2009-08-21
> **blur xc said:**
> I use SolidWorks and it has a settiing for tiling all open docs, which is very useful.  Should  be a standard issue item for any wm, imo.  Sadly, I spend a pretty decent amount of time in front of my windows pc aligning my open windows to be "just right", since it doesn't even have any snap to edges options.

While tiling is good for some, it's not good for everyone. It can be put into WMs, but I don't think it should be on by default.

That said, GNOME is not a Window Manager, it's a desktop environment. COMPIZ on the other hand ***_IS a window manager_***. Installing another window manager and running it will cause compiz to quit.

IT IS NOT possible to have compiz integrate with other WMs at this time.

You should also give your suggestion to the compiz fusion forums: [http://www.compiz-fusion.org](http://www.compiz-fusion.org)

---

### Post by zhocchao on 2009-08-21
there is a tiling plugin for compiz. it's in the compiz-fusion-plugins-unsupported package i think.

---

### Post by blur xc on 2009-08-21
I've noticed there are a few compiz plugnins missing from my compiz list of plugins.. (?)  Anyway, I was also looking for this one- [http://www.youtube.com/watch?v=dJbgjBX8DaI&feature=related](http://www.youtube.com/watch?v=dJbgjBX8DaI&feature=related) and couldn't find it.

How do you add the unsupported package?  I searched in add-remove and didn't find anything.  I saw a website somwhere (but lost the link) that showed something about adding a compiz repos....

thanks,
BM

---

### Post by ceti331 on 2009-08-21
_Windows_
Have you seen "WinSplit Revolution" for the PC?
by default it uses the numeric keypad as hotkeys to place windows in screen halves or quaters.
windows 7 uses WIN+Left/Right to place in the left / right half.

I too am utterly amazed that there isn't wasn't a straightforward TILE HORIZ/VERT hotkey. You can do it by multiple select (ctrl-click) then hitting RMB for a menu which shows the tile options, but it's so awkward for such a common function!

_Linux - Fluxbox. nearly_
Under Fluxbox you can setup hotkeys to place/resize windows so you could easily do something like the vista/winsplit method. you can also put 'maximize vertically' on a hotkey which is nice.



_ linux, other window managers.._
[1] [http://ostatic.com/wmtile](http://ostatic.com/wmtile)
 - so you could associate that with a hotkey.
BUT its always screwed up the panels whenever i've used it

[2] _wmctrl_-command line tool for throwing windows around, which could presumably be run from a hotkey, so could setup something like windows 7
you might be able to make some script to sort it's window list & place everything on the current desktop in certain locations ? 


I'd quite like something which simply shifts the Current and Previous windows so that they're side by side (resizing if there's not enough space) .. (i suspect Enlightenment 'unclutter' might do that)

---

### Post by zhocchao on 2009-08-21
in terminal type:

sudo apt-get install compiz-fusion-plugins-unsupported

---

### Post by blur xc on 2009-08-24
> **zhocchao said:**
> in terminal type:

sudo apt-get install compiz-fusion-plugins-unsupported

Well, I found out why unsupported extras are unsupported!

I tried the tiling plugin, and it's cool and it worked fine, until I logged out and tried to log back in!...  

My whole desktop fell apart!  Ripping, tearing, you name it!  I disabled the tiling plugin, rebooted, and all returned to normal...   

Maybe I'll try it again when the next release of compiz comes out...

BM

---

