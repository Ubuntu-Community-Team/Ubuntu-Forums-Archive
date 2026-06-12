---
title: "ssh-add / gnome-ssh-askpass starts behind desktop background"
date: 2007-07-17
forum: Desktop Environments
---

### Post by gangolli on 2007-07-17
I'm trying to get ssh-add / gnome-ssh-askpass to run when my gnome session starts.

I added ssh-add to my session programs using **System | Preferences | Sessions**.  

This works but the window comes up behind the desktop background.  I can see it in the workspace switcher and manipulate it to the front by moving it to a different workspace.

I've also tried starting it with 

[FONT="Courier New"]env GNOME_SSH_ASKPASS_GRAB_SERVER=1 GNOME_SSH_ASKPASS_GRAB_POINTER=1 ssh-add[/FONT]

which does indeed grab the X server and pointer, but the window is still not visible.

Maybe I'm going about this the wrong way.  Any suggestions/clues?  For further context, this is happening under xserver-xgl, and it may be specific to that.  My gnome session starts with metacity as window manager and I generally switch to beryl manually.

---

