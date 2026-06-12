---
title: "Compiz Question: Trying to make &quot;Aero Snap&quot; work in Gnome"
date: 2011-04-12
forum: Desktop Environments
---

### Post by Adrastus on 2011-04-12
[SIZE=3][FONT=Arial]Hi all,

I hope this is the right forum for this, but it looked better than general help so here goes.

I'm trying to get the Aero Snap feature from Win7 to work in Ubuntu using Compiz.  I followed the instructions from [OMGUbuntu]("http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/")[/FONT][/SIZE] [SIZE=3][FONT=Arial]to use the wmctrl package for Compiz and entered the following as commands 0, 1, and 2, respectively:

[/FONT][/SIZE]```
WIDTH=800 && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

WIDTH=800 && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
```[SIZE=3][FONT=Arial]

(I wrote in my width because it didn't seem to work with the code from the blog even though it looked like an elegant solution)

This works ok, but there are some problems: If i use the edge bindings suggested it wreaks havoc with my windows, opening any program (I didn't test this exhaustively but I think it's safe to generalize) automatically maximizes it regardless of it's previous settings, and this makes my tilda session go crazy on start up (the transparent terminal stuck to the desktop); to avoid the first problem I set the commands to key bindings--Win+Shift+arrow keys-- and this is great cause I rarely use the gestures in Windows anyways, the problem is that the commands don't work on maximized windows.  If I have a non-maximized window I can use the key commands to pin it to the left or the right or maximize but once it's maximized I can't do anything else.

A possible workaround to this could be to create another command to restore a window from maximized and use that first but this adds an extra step to something that is supposed to be a time saver.  So, while a workaround would be doable, it is not preferred.  The desired solution is to find a way of setting the commands, or some other compiz feature, that will let me use my key commands to make a maximized window pin to half the screen.

I don't really understand the command syntaz for the compiz commands and I'm relatively new to Linux but I'm learning fast and I can copy-paste with the best of 'em.

--Adrastus

[/FONT][/SIZE]

---

### Post by ankspo71 on 2011-04-12
Hi,
Try this more recent link:
[http://www.webupd8.org/2011/01/set-up-hot-corners-for-compiz-grid.html](http://www.webupd8.org/2011/01/set-up-hot-corners-for-compiz-grid.html)

You'll be happy to know that this type of functionality is included by  default in Ubuntu 11.04 (coming soon, April 28th) :D

Hope this helps.

---

### Post by Adrastus on 2011-04-12
[FONT=Arial][SIZE=3]Beautiful!!

Thank you so much!
[/SIZE][/FONT]

---

### Post by Copper Bezel on 2011-04-12
I find a simpler solution more useful - the one I use only requires one edge and one command. I have the button binding for the top screenedge set to this: ```
wmctrl -r :ACTIVE: -b remove,maximized_horz; sleep 0.1; wmctrl -r :ACTIVE: -b toggle,maximized_vert
```
You'll need the package wmctrl, and you can remove the "sleep 0.1;", which is a workaround, if you're not using emerald. It just maximizes the window vertically when you click the top edge of the screen (or unmazimizes maximized windows; double-click, then, to change from maximize to maximized vertically.) No random silly stuff going on when you move the mouse around, and edge flipping still works on the other three sides. = )

Edit: Never mind, simultaneous post. = )

---

