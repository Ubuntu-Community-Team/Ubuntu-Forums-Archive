---
title: "Making A Videogame Emulator Supersystem"
date: 2005-10-31
forum: Desktop Environments
---

### Post by jlacroix on 2005-10-31
Hello everyone, I was hoping to get some help with this little "project" of mine.

What I want to do is create a system for emulators and games (namely, for now, NES, ZSNES, and GBA, but I may want to add more later) and hook it up to a TV. I want to get it running on my main computer first, and then move the configurations over to a dedicated box.

I want a frontend for each emulator for Ubuntu. ZSnes already has a good GUI, but the NES and GBA emulators do not, I have to do those with the command line. I got clever and put the emulators commands in the mimetypes for those roms, but still can't get Visualboyadvance to work.

My quest for the "perfect frontend" took me to several frontends, like Gnomeboyadvance, that won't run or install because they end up depending on older versions of dependencies which is just plain annoying.

I've also been looking at Mythgame, which won't even install from Synaptic due to dependency problems, but evenso, Mythtv seems to be a right of passage to install, an intermediate user like me can't make heads or tales of setting it up, which is inexcusable for them to make it so darn hard. Mythtv-Mythgame is probably what I want, though.

Anyway, my main purpose of doing this is to get all my games in once place. Hooking up my NES and constantly blowing into it to play it is just plain annoying, and in order to play all my GBA games on my TV I would have to buy a $75 part and risk damaging my GBA when I open it up, not my idea of fun. It would be nice to "consolidate" all these games into one box, hence this project.

So basically I want an NES frontend, and a GBA frontend, and hopefully a cool frontend for Zsnes also, but I would prefer one frontend for all, and while not required, selecting a game from the list with my controller would be nice too, so when I hook it up to my TV I won't have to have a keyboard attached.

Anyway let me know, hopefully I can get this going...

---

### Post by jlacroix on 2005-10-31
I don't mean to be a pest but does anyone have any ideas? At the very least how to set up NES or GBA frontends?

---

### Post by daveg on 2005-12-14
Yeah, I've used mythtv/mythgame in the past. It does make a pretty sweet video game emulator system. I used KnoppMyth not ubuntu on it though as it had all that stuff setup and ready to go (never did get my dvb card working on it, but that's another story :confused: )

---

### Post by mcduck on 2005-12-15
have you seen AdvanceCD? It's a live-cd with MAME- and MESS-emulators and a nice frontend. You could check that out for nice tips.

[http://advancemame.sourceforge.net/cd-readme.html]("http://advancemame.sourceforge.net/cd-readme.html")

---

### Post by bradroger on 2005-12-15
I had a very similar line of thought.  I wanted to get something so I could play any game for any system....using a controller sitting on the couch.  I tried myth-game also but my troubles made me give up the whole idea altogether.  I wonder how hard it would be to code a simple controller-driven gui that ties together all the command line emulators.  I don't know much about programming but it seems like a simple enough project for someone who knows what they're doing.

---

### Post by ikki_72 on 2006-01-04
yup, great idea, but is there anyone currently working on it?

---

### Post by gitfiddler on 2006-01-04
Mcduck, thanks for the tip about AdvanceCD, it looks like fun!

---

### Post by Zwack on 2006-01-04
So, if I get this right, what we have is a bunch of people with an idea that they like which they think should be easy to code, and they want someone to write it?

I'm not criticising the questioners or the wish.

I think the answer seems to be that this doesn't exist yet.

So, given that it doesn't exist, what can be done to make it happen?

Does anyone who wants this have programming experience?  Is anyone willing to learn?  There are News groups devoted to programming, and languages that make programming interfaces easier...  I'm guessing but a Python front end with a uniform interface shouldn't be too hard.

You need to refine your ideas first, plan as much as you can and then see if you can get some input from people and maybe even help.  If you're willing to do most of the work then you can probably get a lot of good advice once you've started.

I think you would want a simple front end that lists all available emulators so that you can choose one, and then gives you the available games for that emulator.  Then you select that and it starts the emulator automatically giving it the right parameters.  You probably also need a preferences or set up screen that lets you add parameters to both individual games and emulator command lines.

You may want either instead or as well a screen that lists all available games and lets you choose one.

So, work out what you would like to see, and then decide if you want to try and write it.  If not, you'll need to look for someone to do it for you or something that is easily modifiable that already does it.

I hope that this helps,

Z.

---

### Post by sethmahoney on 2006-01-04
Making a frontend shouldn't be too hard with Glade and Python.  My only concern would be trying to operate it with a gamepad, but that might be easy, too.  Especially using the gamepad as the sole interface, setting it up as a single frontend to multiple command-line programs would probably be easiest, as you could have that frontend start when Ubuntu starts.

Anyhow, yeah, decide on the emulators you want to use, gather documentation for each, and make a nice GUI mockup.  After that, getting it going with Python should be pretty easy.  I'd be interested in setting up a similar system, so post your progress in this thread!  I'd also be willing to do some scripting/GUI stuff if necessary, although I'm probably not the most reliable person in the world...

---

