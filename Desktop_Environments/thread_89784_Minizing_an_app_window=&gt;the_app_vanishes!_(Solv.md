---
title: "Minizing an app window=&gt;the app vanishes! (Solved)"
date: 2005-11-13
forum: Desktop Environments
---

### Post by eeried on 2005-11-13
(So sorry -- I meant "minimizing")
I've had that problem with Hoary and this wasn't solved by Breezy since  /home  is on its own partition.

When I minimize the window of an open application, it simply vanishes into thin air, together with the app itself.

So I ought to reconfigure something but I don't what in Gnome. I browsed through the hidden gnome dirs but didn't find anything obvious to edit.
I don't mind losing my present settings if I can recover the minimize function -- at the moment I need to have apps open across the 4 workspaces, which isn't totally unconvenient but...;) 

Your help would be much appreciated!
Cheers,

---

### Post by jasay on 2005-11-13
If you can still alt-tab to the program then right click on your panel > add to panel > window list.

---

### Post by kelsey23 on 2005-11-13
First, press CTRL+ALT+F3. Now it should say "Ubuntu 5.10 "Breezy Badger"  (computer name) tty3". There also should be a log-in prompt. log-in with your username and password. Once you have logged in, type:

ps - | less

scroll up and down in that. and see if the application name is anywhere in that list. If it is, than the application is *still* running. If it isn't then the application isn't :-)

**Note: to get back to GUI mode, press CTRL+ALT+F7**

---

### Post by aysiu on 2005-11-13
I'm with jasay on this one. You're probably just missing "window list" from the panel.

---

### Post by eeried on 2005-11-14
aysiu and jasay, you were right -- I did what jasay said (!) and all's well -- the window's list's back!  and I can minimize away!
What a comfort!
Many thanks for your help!
:)

---

