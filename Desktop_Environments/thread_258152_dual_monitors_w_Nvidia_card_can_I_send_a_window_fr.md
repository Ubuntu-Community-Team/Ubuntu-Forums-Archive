---
title: "dual monitors w/ Nvidia card: can I send a window from screen0 to screen1?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by vaskeli on 2006-09-15
I have a dual screen system (a monitor(screen0) and a TV(screen1)), working through an Nvidia card. I set it up according to [these instructions]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-p.html"). I'm not using TwinView.

My two desktops work independently. They have different resolutions, taskbars, etc. Programs open in the screen that they're launched from.

I am looking for a way to move an *open* window or application from screen0 to screen1 and vice versa. I don't necessarily need to be able to drag it across (TwinView will do this, but it has other drawbacks which I'd like to avoid it). Ideally, I'd like a contextual menu command (similar to the command "Move to Another Workspace...") to perform the operation, but a functional bash script will do.

I should mention that I'm very new to Ubuntu and scripting, so I'll probably only understand the most basic instructions. I'll really appreciate any help that's offered.

---

### Post by giants_fan on 2006-09-15
There is package called 'teleport' that should do what you want.  

See:  [http://packages.ubuntu.com/dapper/x11/teleport](http://packages.ubuntu.com/dapper/x11/teleport)

I tried it a while back, but unfortunately, didn't get it to work.  I didn't try very hard, though...

---

