---
title: "QXF - wrong player profile"
date: 2009-04-23
forum: Gaming &amp; Leisure
---

### Post by CapeCodKiter on 2009-04-23
I'm having a problem with XQF and the player profile that is being used in Wolfenstein: ET. 

XQF is using an old profile that I deleted. So when I start W:ET using the game icon, I have one profile. But when I start the game using XQF, I have a different profile. 

The problem now is that the profile that XQF uses has a good amount of xp that I dont want to lose. Any idea where XQF is getting its settings from and how I can "recover" that player profile? Everything works fine if I start the game with XQF.

Thanks!

---

### Post by rizzeh on 2009-04-23
Could it be that you are connecting to a modded server (etpro,etpub,noquarter) via XQF? 
Starting the game using game icon will launch plain/vanilla etmain.

---

### Post by CapeCodKiter on 2009-04-23
I am connecting to a server that has jaymod ([http://www.deathrowinmates.net/](http://www.deathrowinmates.net/)) but wouldn't it use the only profile that my install of W:ET has? Or does XQF create its own profiles? Why wouldn't both programs use the same profile since they both use the same executables?

---

### Post by rizzeh on 2009-04-23
XQF, as far as i know, doesnt create new profiles, but jaymod has its own folder with config files. It's location would probably be somewhere ~/.etwolf/jaymod
Unless you've installed it manually

---

### Post by CapeCodKiter on 2009-04-23
> **rizzeh said:**
> XQF, as far as i know, doesnt create new profiles, but jaymod has its own folder with config files. It's location would probably be somewhere ~/.etwolf/jaymod
Unless you've installed it manually

Thanks! I found the jaymod folder. It does have 2 profiles in there. My old, original one and my newer one. Interesting... I deleted the older profile a while ago. But I deleted it from the main W:ET appliation (not using QXF to start the game)

How do I find the GUID for each profile?

---

### Post by rizzeh on 2009-04-24
you could try connecting to server with profile in question and punkbuster mentions your GUID in terminal:
 et +connect your.server.ip

this is what i got:

PunkBuster Client: PB Server assigned guid = 02fc576e****************

---

