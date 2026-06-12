---
title: "Beryl on feisty"
date: 2007-04-18
forum: Desktop Effects &amp; Customization
---

### Post by Fireblend on 2007-04-18
Damn, I knew this would happen. I just upgraded to Feisty, installed beryl with sudo apt-get install beryl and I don't get window borders. Everything works fine tho. It's only the emerald theme or whatever it's called. Help please >_< 
Edit: Also, forgot to mention that even tho I try running beryl and beryl manager, the beryl icon won't appear in the notifications area.

---

### Post by Fireblend on 2007-04-18
Alright I solved it. For those that might have the same problem, try running "emerald --replace &"

---

### Post by mikibg on 2007-04-19
do not work that ... only if I do this
Beryl Manager >Select Window Decorator>GTK Window Decorator 
if I do this I get window borders but if I try with emerald I lose borders???
install GL desktop for settings

---

### Post by jacksenechal on 2007-04-28
The window decorations broke for me too when I upgraded from Breezy to Feisty. It doesn't matter if I use compiz or beryl, or if I choose the GTK Window Decorator from within the beryl manager, or if I run "emerald --replace &". None of it works. 

I've also uninstalled and reinstalled all the beryl and emerald related things, as well as the nvidia-glx drivers, to no avail.

Anyone have suggestions? I'm lost without my pretty windows... :cry:

---

### Post by subslug on 2007-04-28
See if [ [COLOR="Sienna"]this trick[/COLOR] ](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631) helps. You'll need to restart X before it'll take but it fixed my issue when nothing else would.

---

### Post by jacksenechal on 2007-04-29
> **subslug said:**
> See if [ [COLOR="Sienna"]this trick[/COLOR] ](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631) helps. You'll need to restart X before it'll take but it fixed my issue when nothing else would.

Thanks, that did it! Specifically, I just needed to add this line to my xorg.conf, for my nvidia card:
 
  Option "AddARGBGLXVisuals" "True"

I'm also pleased to note that the slow scrolling issues I'd been experiencing with Firefox when using Beryl under Breezy are fixed. Now there is truly no barrier to using Beryl full-time. Very happy.

---

