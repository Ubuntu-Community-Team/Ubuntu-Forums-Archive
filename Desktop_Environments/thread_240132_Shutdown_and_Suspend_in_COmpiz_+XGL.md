---
title: "Shutdown and Suspend in COmpiz +XGL"
date: 2006-08-20
forum: Desktop Environments
---

### Post by PRGUY85 on 2006-08-20
Hey:

I installed Compiz and XGL using the Automatix Bleeder package.  It works flawlessly after switching to 24bit color. Yet, the suspend feature is not working properly.  In order for it to work, I had to add a kill compiz function whenever I suspend the machine, yet this doesn't work all the time.  Sometimes it doesn't suspend at all, just lock the screen.  Other times it never comes back from Suspend.  And the times it works, I have to reactivate compiz by toggle-compiz-nvidia.

Also, I read having a separate XGL session affects the Quit menu.  Well, my Quit menu doesn't display the Shutdown and restart icons anymore.  

Anyone know  away around all this?

---

### Post by MikeMLP on 2006-08-20
I'm not sure if there *is* a way around this.  I have similar problems on an ati radeon mobility 9600 with suspend, although it tends to work more often than not.  The menu indeed does not contain a shutdown or restart.  Usually what I do is I switch to metacity, log out, and then choose shut down.  Sometimes this just freezes to a black screen.

The reason why the shutdown and restart icons are missing has something to do with the fact that XGL / compiz runs its own window manager on top of GDM.  Just keep in mind that it is alpha software, and this is being done so that the developers of XGL / compiz don't have to wory about writing their own window manager program and can concentrate on creating nice plugins and effects.  At least, that is what I have read.  If someone else knows of some fixes for these "problems," I'm listening :).

---

### Post by siman on 2006-08-20
I always have this problem with my Nvidia card, and searching through the forums I came to the same conclusion as MikeMLP.

Creating a shortcut to halt / reboot on your desktop is a good workaround, or pressing CTRL+ALT+BACKSPACE to logout without fiddeling with the mouse.

---

### Post by PRGUY85 on 2006-08-20
So anyone know whats the best workaround for suspend?  I could just switch to regular Gnome and then Suspend, yet that would be kind of a pain...  Anyone know how to reactivate Compiz automatically after coming back from suspend.

---

### Post by MikeMLP on 2006-08-20
I'm sure its the kind of thing one could create a script for, but I wouldn't have the first idea of where to start.  You might want to post this question here: [http://www.compiz.net/index.html]("http://www.compiz.net/index.html")

Hope everything works out for you, and if you find a good workaround, please let us know in this thread, I'd love something that could take care of this automatically.

---

