---
title: "pop ups are driving me mad"
date: 2009-11-01
forum: Desktop Environments
---

### Post by phekdra on 2009-11-01
Hello all,

I've just upgraded to 9.10 and every time I move the mouse over an item in the gnome panel I get an annoying pop-up message telling me what I already know, and I don't know how to turn them off! :evil: It's particularly bad in Firefox, but that may be a different issue...

By far the worst, however, is the workplace switcher, which leaves a yellow-backed permanent message saying 'click to start dragging xxxx' on my desktop after I've moved the mouse away, requiring me to move the mouse back over it to get it to go away. It's driving me bananas! I'm sure it wasn't this bad in Jaunty. Please help...

Andrew

---

### Post by stinkeye on 2009-11-01
> **phekdra said:**
> Hello all,

I've just upgraded to 9.10 and every time I move the mouse over an item in the gnome panel I get an annoying pop-up message telling me what I already know, and I don't know how to turn them off! :evil: It's particularly bad in Firefox, but that may be a different issue...

By far the worst, however, is the workplace switcher, which leaves a yellow-backed permanent message saying 'click to start dragging xxxx' on my desktop after I've moved the mouse away, requiring me to move the mouse back over it to get it to go away. It's driving me bananas! I'm sure it wasn't this bad in Jaunty. Please help...

Andrew
You can turn some of them off in gconf-editor
/apps/panel/global/tooltips_enabled
and this thread shows how to use compiz and opacity settings to hide them
[_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=672864[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=672864")
_[COLOR="DarkRed"]Edit:[/COLOR]_
Just tried the compiz solution and this works.
Just need to add [COLOR="RoyalBlue"]Tooltip 0[/COLOR]

---

### Post by phekdra on 2009-11-01
> **stinkeye said:**
> You can turn some of them off in gconf-editor

Aha - thanks very much!

I seem to remember a long time ago Gnome 1.x used to come with a control panel that allowed me to change things like that without resorting to gconf-editor.

No I haven't gotten over it yet... :p

Andrew

---

