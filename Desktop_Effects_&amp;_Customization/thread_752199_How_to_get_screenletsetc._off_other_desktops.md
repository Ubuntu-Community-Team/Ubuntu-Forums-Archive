---
title: "How to get screenlets/etc. off other desktops?"
date: 2008-04-11
forum: Desktop Effects &amp; Customization
---

### Post by SaddaGocaraRupa on 2008-04-11
Hello there, dear Ubuntu fiends,

I finally got back on ubuntu after a year or so without it and just upgraded to GG. All went well and compiz fusion is much much better than beryl ever was, BUT:

I forgot how to keep stuff on one desktop. I'm on a transparent cube and all screenlets and windows I have open on desktop1 show up on all other desktops. I only want one, though. I used to have this configured in Beryl, but can't remember how I did it. Also, I used to have raised windows. There is an option like that in the Adv. Desktop Eff. Settings ('Raise windows'?) but it doesn't give that nice 3D thickness to screenlets and windows once you zoom out. If anyone remembers those settings, I'd be mighty grateful.

Cheers,

-sadda

---

### Post by aashay on 2008-04-11
I think you mean Autoraise windows in ccsm, which is entirely different. The 3d windows feature while rotating the cube hasn't been implemented in compiz yet. Make sure your screenlets aren't "sticky" and they will show up on only one workspace

---

### Post by SaddaGocaraRupa on 2008-04-11
Thanks, aashay. I got the screenlets off the other screens. Now it's just the main menu bar that bothers me. Is it possible to un-sticky that? It shows up on all other desktops. 

Bummer about 3d windows. oh well, i'll just have to wait then. What is auto-raise, then?

Cheers,

-sadda

---

### Post by aashay on 2008-04-12
I have no idea what autoraise does. I think its supposed to autofocus windows when you hover upon them for some time; but it never happens in my case. The main menu bar(panel?) cannot be un-stickied. You can try hiding it completely if you want. But that will keep it on all workspaces, just hidden till you hover over it.  Another idea would be to use Awn or some other dock. I usually alt-tab or expose my way through windows, so had no use for the panel. Got rid of it and installed awn to save some real estate on my laptop screen.

---

### Post by SaddaGocaraRupa on 2008-04-12
bummer. i could do it (unsticky the menu bar) on feisty/beryl. awn is great. i used to run it and only just got it to work again on my machine after a few mishaps. 

now i have only one problem:

screenlets doesn't want to remember my previous configuration. whenever i boot up, i have to start up all the screenlets i want manually. i went to 'sessions' -> 'save current session' but it didn't help. any other tips?

thanks again, aashay!

-sadda

---

### Post by tommyhakinen on 2008-04-12
> **SaddaGocaraRupa said:**
> 
screenlets doesn't want to remember my previous configuration. whenever i boot up, i have to start up all the screenlets i want manuallya



For screenlets to start on startup, open screenlets manager. Look for the options, then select "Running Screenlets". You will see those screenlets that are currently running on the right. select one of them and check both "Start/Stop" and "Auto Start on Login". Then do the same for the rest of the screenlets.

That should do it.

---

### Post by SaddaGocaraRupa on 2008-05-22
> **tommyhakinen said:**
> For screenlets to start on startup, open screenlets manager. Look for the options, then select "Running Screenlets". You will see those screenlets that are currently running on the right. select one of them and check both "Start/Stop" and "Auto Start on Login". Then do the same for the rest of the screenlets.

That should do it.

Unfortunately it doesn't! When I do click on them once I open Screenlets manager (which autostarts and is in the Gnome panel, but doesn't open the actual screenlets), "Start/Stop" and "Austostart on Login" are ticked, but the won't actually open on login. I have to manually go to "Autostart Screenlets" and hit "Start/Stop", at which point they all pop up. :confused:

---

