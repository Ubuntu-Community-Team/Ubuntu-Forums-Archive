---
title: "Fluxbox and wmdrawer - mutiple dockapps starting"
date: 2006-05-29
forum: Desktop Environments
---

### Post by Resurrection on 2006-05-29
I know this is technically in the Gnome section, but I didn't know where else to put this topic.  I am using Ubuntu Breezy but I am trying out Fluxbox along with Rox-filer.  Everything works great with the exception of the fluxbox "slit"

I am trying to use wmdrawer but everytime Fluxbox starts up, it creates two instances of wmdrawer, one before fluxbox starts fully, and one after.  So I get two dockapps side by side that do the same exact thing.  If I remove the one line from my fluxbox startup file that tells it to start wmdrawer, then it doesn't start at all.  With "wmdrawer &" added in to the startup file, I get two instances.  With no dockapps running and if I start wmdrawer from the command line, I get only one instance.

Any ideas?

Edit:  It happens with any dockable application I try, wmclock, wmfire, etc.  So obviously my fluxbox startup file starts the app, then something in another file starts the app again.

---

