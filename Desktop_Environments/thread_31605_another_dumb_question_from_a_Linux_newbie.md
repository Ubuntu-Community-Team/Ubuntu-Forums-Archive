---
title: "another dumb question from a Linux newbie"
date: 2005-05-03
forum: Desktop Environments
---

### Post by fractalvibes on 2005-05-03
Ok,
Dumb question 356,789.  Using Ubuntu 5.04 and Icewm.  When I open up a terminal window and run something, how do I cut and paste from that window into a text editor?  I get no scroll bars on the terminal window either, so I cannot see what output has already passed....

thanks,

fv

---

### Post by XDevHald on 2005-05-03
[QUOTE=fractalvibes]Ok,
Dumb question 356,789.  Using Ubuntu 5.04 and Icewm.  When I open up a terminal window and run something, how do I cut and paste from that window into a text editor?  I get no scroll bars on the terminal window either, so I cannot see what output has already passed....

thanks,

fv[/QUOTE]
 if you have a scroll button on your mouse your can do that as well to scroll up, if not then right click on the Icewm to see if it has options for this to.

Now with the copy/paste, simply highlight the text, then right click and it'll show Copy, then goto the next terminal and right click again and select Paste :)

The other guys might have an easier way of explaining this, and possibly helping you out with the terminal scroll issue.

---

### Post by mlmurray on 2005-05-03
[QUOTE=fractalvibes]Ok,
Dumb question 356,789.  Using Ubuntu 5.04 and Icewm.  When I open up a terminal window and run something, how do I cut and paste from that window into a text editor?  I get no scroll bars on the terminal window either, so I cannot see what output has already passed....

thanks,

fv[/QUOTE]
 For scrolling in most terminal windows and any virtual terminals, SHIFT+PG UP, should do the trick.

Copying and pasting in X is really slick, especially if you have a middle mouse button.  As soon as you highlight text, X put's it in it's "cut buffer", to paste that text, just position you cursor where you want it, then press the middle mouse button.  Viola!, copy and paste.

Also, the cut buffer is separate from gnome (or kde's) clipboard.  If you're using the gnome-terminal or konsole(in kde) and you see a menu up top (or when you right click, as suggested by BB) you can copy and paste in the traditional (windows style) way.

---

### Post by fractalvibes on 2005-05-03
If it was that simple I would not have asked...using Icewm.   Two mouse buttons.
I can highlight the text ok, but ctrl + c is not copying to clipboard that is accessable from the desktop.  Right click produces nothing.

command > somefilename.txt may be the only way.....

fv

---

### Post by mlmurray on 2005-05-04
> If it was that simple I would not have asked...using Icewm. Two mouse buttons.

First suggestion:  Get a three button mouse - you'd probably appreaciate a scroll wheel as well.  They are cheap.  This will solve your problem.

Second suggestion:  Try clicking both left and right mouse buttons simultaneously.  I think Ubuntu sets this up by default.  If not look in you xorg.conf file for a setting in the "input Device" section that looks like:  ```
Option          "Emulate3Buttons"       "true"
```  If this is set to false, set it to true and restart your Xserver (easiest way is just CTRL+ALT+BACKSPACE).  If that doesn't work go and buy a three button mouse.  It makes working in X so much easier.

As I said, X's "cut-buffer" is different from KDE or Gnomes "clipboard".  The "clipboard" which you rightly knew you can utilize with the traditional menu cut,copy,paste commands or the keyboard shortcuts, only works with KDE, Gnome apps or apps that are specifically aware of this clipboard.  X's "cut-buffer" on the other hand works in all X apps.

---

### Post by fractalvibes on 2005-05-04
Thanks!  Selecting the text and clicking both mouse buttons seems to work ok - just have to repeat for each screen's worth.

thanks,

fv

---

