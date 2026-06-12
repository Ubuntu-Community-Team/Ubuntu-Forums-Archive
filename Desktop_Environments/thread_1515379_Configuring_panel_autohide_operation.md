---
title: "Configuring panel autohide operation"
date: 2010-06-22
forum: Desktop Environments
---

### Post by buchs on 2010-06-22
I am using 9.10 Ubuntu with the Compiz window manager.  I am interested in changing the behavior of the panel (top and bottom) autohide operation.  I have been in the CompizConfig Settings Manager / General Options and changed the Edge Trigger delay but that does not seem to impact how fast the panels unhide when I am at the edges.  I would like to delay the response time before unhide occurs.  Also, I would like to narrow the trigger region so that I have to be closer to the edge to trigger it.  Does anyone know how to control these things?  Can you direct me to any documentation?  I am comfortable working underground (command line, editing, programming) but I often find myself stepping into an ocean when I try to solve simple problems, so I would like to build on others experiences.  Thanks.

---

### Post by Breambutt on 2010-06-22
Alt+F2 > gconf-editor > /apps/panel/toplevels/top_panel_screen0

I'm actually on Lucid but you can at least use the search in gconf-editor if the location on your machine differs from this proposition.

---

### Post by buchs on 2010-06-22
Excellent!  Thanks very much!  You've opened a new door on customization in Ubuntu for me.  The location was the same in 9.10.

---

