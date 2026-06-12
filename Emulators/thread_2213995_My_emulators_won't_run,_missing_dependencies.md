---
title: "My emulators won't run, missing dependencies"
date: 2014-03-29
forum: Emulators
---

### Post by MattKimura on 2014-03-29
I had to restart my computer and re-install all my emulators. But now when I load a game, they seem to have a problem. For ex, SNES games run slow, and PS1 games take long before they start up. They worked flawless before on my previous install of Ubuntu.
I'm looking for whatever dependencies I might be missing. I have no idea what these emulators need in order to work. I installed a bunch of things before, but now I can't remember what they were. Something about libgtk. According to research, it isn't included in Ubuntu 13.10 Saucy. PPA's won't install it either, they're outdated.
I'm using a new Chromebook, with a new 3.0 USB flash drive. The games loaded perfectly fine with this same setup.

---

### Post by deadflowr on 2014-04-01
Can you tell us which snes and ps1 emulators you have?

There are several for each, and some come ready to use in Ubuntu.
(Like pcsx-r, and zsnes)

Others, though, may not be as well put together for Ubuntu's more recent releases.

---

### Post by MattKimura on 2014-04-03
> **deadflowr said:**
> Can you tell us which snes and ps1 emulators you have?

There are several for each, and some come ready to use in Ubuntu.
(Like pcsx-r, and zsnes)

Others, though, may not be as well put together for Ubuntu's more recent releases.

Thanks for the reply, but I've solved my problem.

It was a fresh Ubuntu install, so I had to run :sudo apt-get update && sudo apt-get upgrade

Then I had to install Ubuntu-restricted-extras
Then I installed Java (That doesn't effect emulators)

So then I ran Snes9x, and it worked flawless like it did back then. PCSXR works flawless as well, happy to see my emulators working properly now.

On a side note, Im using a chromebook, and Im using what's called "Crouton". It's what's running Ubuntu on my Chromebook. I updated Crouton, so that may have also fixed my problem with the emulators. Whenever a ChromeOS update is released, it messes up Crouton.

---

### Post by Harry_Davis on 2014-04-23
I had similar problem. Thanks, [[COLOR="#000000"]it[/COLOR]]("http://xbx360.com/version-2-4.html") worked for me too.

---

