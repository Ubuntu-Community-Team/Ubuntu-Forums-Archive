---
title: "sdlmame stopped working"
date: 2011-04-19
forum: Gaming &amp; Leisure
---

### Post by Russell_S on 2011-04-19
Hi, for the past couple of days I have had qmc2 and sdlmame working quite happily. However, last night after a normal Ubuntu software update sdlmame appears to have stopped working. When I run qmc2 it just sits there "waiting for data" and I think it is because it cannot find sdlmame. It is setup to look for sdlmame in "/usr/games/sdlmame" but if I look in that folder sdlmame is not present whereas it definately was there before.

If I open a terminal window and type "sdlmame" it reports that it is currently not installed. However, if I run the command "sudo apt-get install sdlmame" it reports that sdlmame is already the newest version.

So on one hand it is saying that sdlmame is up to date and on the other hand it is saying it is not installed. This has me totally confused and wonder if someone could explain this to me and more importantly how to overcome it please.


Many thanks

Russell

---

### Post by Russell_S on 2011-04-19
On further investigation it appears from the package manager that the sdlmame that is now installed is a "dummy package" whatever that is.

What is this dummy package for and how do I go back to the "real" one I had before.

I've tried removing sdlmame and then installing it again but I just get the same results.

---

### Post by mips on 2011-04-19
> **Russell_S said:**
> It is setup to look for sdlmame in "/usr/games/sdlmame" but if I look in that folder sdlmame is not present whereas it definately was there before.


Mine points to /usr/games/mame

---

### Post by DoktorSeven on 2011-04-19
Yes, SDLMame is now obsolete since they brought in the stuff for Linux into the MAME mainline.  You need to install the "mame" package (**sudo apt-get install mame**) if it's not already installed, and the binary is I believe /usr/games/mame (I compile my own MAME, keeping current with every MAME release myself).

---

### Post by Russell_S on 2011-04-20
Hi again,

Thanks for that, it is now all working again but with mame now instead of sdlmame.


Thanks again

---

