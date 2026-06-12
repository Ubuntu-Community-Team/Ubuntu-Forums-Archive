---
title: "Force Quit Force Quit"
date: 2005-07-26
forum: Desktop Environments
---

### Post by Irony on 2005-07-26
I used the force quit button today and then couldn't get rid of the little force quit window in the centre of the screen.

The window says 'click on window to force quit or ESC to cancel'.

How do I get rid of the thing, it just sits in the middle obscuring the middle of any other window.

---

### Post by Xian on 2005-07-26
There could be some tiered boxes that need to be closed in sequence. Short of this you could try removing them with the gnome-system-monitor, the killall command in a terminal session, or just by logout/login.

---

### Post by varunus on 2005-07-26
Another nice little trick:  open a terminal and type ```
xkill
``` into it.

You cursor will change to a little crosshair.  Click on any window, and the process that created it will be forced to quit.

---

### Post by Irony on 2005-07-27
Thanks for the replies.

I discovered the system monitor, didn't see the killall command at the time but I will give it a go next time.

The xkill in terminal I will also have to try.

---

### Post by konflikt on 2006-08-14
Thats right.  xkill in a terminal window does the job nice.  Blender locked up on me right now, while I was trying to render a scene from Elephant's Dream(actually, I had no idea it would take so long to render, and the window would not respond to clicking on the "X" button in the top right).  This one kicks a**.  Thanks for the tip buddy.

---

