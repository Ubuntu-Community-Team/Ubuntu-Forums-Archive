---
title: "Problems with World of Warcraft"
date: 2007-01-24
forum: Gaming &amp; Leisure
---

### Post by Mileeta on 2007-01-24
I installed WoW, following the wiki that was posted in another thread.  Everything installed ok, and the game patched up to current without a problem.  Now there are no graphics at all, nor is there any sound.  There are text blocks, I can read anything on the screen, I can select a server, but there are no pictures to speak of.  Also, as far as sound goes, it worked once, when I installed the original game, but once I installed the expansion, the sound went out the window as well.  I think if I knew where WoW was installed I could fix the sound issue, but I was hoping someone could help with the video.

Guess that's what I get for thinking my ATI Radeon 9800 XT was a good card.

-M

Oh, I'm using wine 0.9.29 and Ubuntu 6.06 Dapper.

---

### Post by inCursorated on 2007-01-25
i'm having WoW ATI woes as well... /sigh
just out of curiousity what driver are you using?

btw, it should be installed in /home/[username]/.wine/drive_c/Program Files/World of Warcraft

---

### Post by willskills on 2007-01-25
Poor ATI customers.... people seem to really struggle getting WoW to run acceptably with an ATI card, if at all.

If you can afford it, trade your ATI in or buy an Nvidia card........ over the weekend, I managed to get a few friends interested in Ubuntu.

I was playing WoW when they arrived, and was swtiching workspaces to xmms (with various visual plugins running), browser and google earth..... while I was flying on my gryphon.

After logging out I turned on Beryl and just let them drool. Needless to say, they all begged for a LiveCD and a list of handy links for when they invariably get stuck.

Luckily we have all been friends for a while, and all actually use Nvidia. They all managed to install Ubuntu, get it running with drivers & sound, and wine & wow without a problem.

Hooray for more converts \o/

---

### Post by jaytek13 on 2007-01-25
Yeah, I have to say (although this probably isn't very helpful, it is probably the best recommendation) that since ATI has always been lax in their Linux support, and Nvidia has always been quite exceptional with their Linux support, if you are a gamer and want to start using Linux/Ubuntu a Nvidia card is absolutely a must have.

And you don't necessarily need top of the line. I have a 6600 which can probably be scored from an online site for maybe $50. With that I am running WoW pretty much flawlessly.

Buying a new card may not be what you want to hear, but really it's the best thing you can do for yourself.

---

### Post by inCursorated on 2007-01-25
i'm using a vaio laptop so i don't have the option of adding an nvidia card... it's a nice laptop aside from the ati hardware... i'll find a way to getting working... started a [thread]("http://ubuntuforums.org/showthread.php?t=344214") for my issue (that currently has some unanswered questions) if anyone is interested in trying to help...

---

### Post by Mileeta on 2007-01-25
Well, I managed to get the video problems sorted out (using icky proprietary drivers from ATI, but it works now).  I still have no sound, however.

I had sound once.  When the game first installed, I could hear the song play.  On my second startup, however, the sound didn't work and hasn't worked since.  I had the same problem with Diablo II, which also is unresolved.  Any ideas?

-M

---

### Post by Sammi on 2007-01-26
It's most likely caused by the fact that you've configured Wine to use OSS(which you should). The problem can be fixed by launching WoW with the aoss command in front. See here for instructions: [https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49](https://help.ubuntu.com/community/WorldofWarcraft#head-9f4c9e2df7bf2ce0429e495e9e6e55f58eac4e49)

Post back with more details if this doesn't work.

---

