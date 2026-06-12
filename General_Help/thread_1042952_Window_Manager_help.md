---
title: "Window Manager help"
date: 2009-01-18
forum: General Help
---

### Post by SirSigma on 2009-01-18
A few days ago I was trying to add a wallpaper changer to my Sessions Preferences, and I accidentally changed the command for my Window Manager. I looked things up and thought everything was back to normal, but I think something is wrong; my desktop effects are always disabled on start-up. This is a really annoying problem for me. Does anybody know the absolute correct Window Manager command for Sessions? I ask because I looked around and can't seem to find anybody with this specific problem.

---

### Post by alan34 on 2009-01-18
I take it you are using Compiz. The command is

compiz --replace

and for Emerald the window decorator it is

emerald --replace

Try them in a terminal first to test.

---

### Post by SirSigma on 2009-01-18
Thanks for the help. I tried the commands on Terminal.

However, I'm using Metacity. Is the command just metacity --replace then?

EDIT: I changed the command to metacity --replace and it still defaults to no desktop effects after a restart. I've come to the conclusion that metacity alone does not include desktop effects. Can anybody tell me a command that gets both metacity and my desktop effects back?

---

### Post by SirSigma on 2009-01-18
It's been over an hour and I'm still searching online and making guesses on what the command should be. Does anybody know?

Oh, and I found out I am indeed using Compiz for desktop effects.

---

### Post by mssever on 2009-01-18
> **SirSigma said:**
> However, I'm using Metacity. Is the command just metacity --replace then?
Metacity has no desktop effects. Compiz is what provides them. I don't know how to make your change persistent, but if you run fusion-icon, it might be able to set it for you.

---

### Post by SirSigma on 2009-01-18
> **mssever said:**
> Metacity has no desktop effects. Compiz is what provides them. I don't know how to make your change persistent, but if you run fusion-icon, it might be able to set it for you.

WOW!

Your instructions didn't completely help me, but they got me on the right track. Now I've got my desktop effects back! Thanks!

---

