---
title: "Possible to close all files in bottom panel at once?"
date: 2010-08-19
forum: Desktop Environments
---

### Post by Wtwine on 2010-08-19
Hi

I sometime have multiple files open for printing.  Is their an easy way to close all the files in the bottom Gnome panel in one go when finished, rather than right clicking each one and selecting "close"?

Cheers

---

### Post by quixote on 2010-08-21
If there is, I haven't heard about in my five years or so of using ubuntu.  It's a good idea.  Put it in Brainstorm!  Be nice to see it implemented.

---

### Post by Gaygerbil on 2010-08-21
I think what would be even better than that is if they created commands for closing, maximizing, minimizing, and resizing windows through the terminal. That way we could create all these scripts and shortcuts with those commands. :]

Right now it seems like those actions are done through a script that invokes metacity.

As for your question it's pretty simple if you know the likely apps to be open at the bottom panel. *I'm not exactly sure what you're talking about*

But if you are talking about closing things like Chrome/Firefox and a music player and VLC/Totem and typical things like that. You can write a command to do 

pkill chrome && pkill vlc && pkill skype && pkill blah blah.

And assign that to a shortcut. Even if the app isn't open it won't do anything trying to kill something that isn't running so it's all good.

---

