---
title: "Compiz not starting up at login after upgrade to Jaunty"
date: 2009-04-27
forum: Desktop Environments
---

### Post by my window broke on 2009-04-27
So I upgraded to Jaunty yesterday and now whenever I start up my computer I have to reload my compiz settings everytime. Kinda annoying since I have a widget layer with screenlets that isn't loading properly until I reload compiz, making my computer login a big mess. None of the compiz settings work (checked widget layer turn off with f9, rotate cube, etc...) but once I reload it everything is fine. Any tips?

---

### Post by dccrens on 2009-05-04
Same here. Still looking for an answer...

---

### Post by IllegalCharacter on 2009-05-09
I haven't found the root cause of this, but a workaround is like so:

Go to System->Preferences->Startup Applications.

Click Add. Set the name to "Compiz" and the command to "compiz --replace". Click Add. Log out and log in again. Seems to work fine for me.

---

