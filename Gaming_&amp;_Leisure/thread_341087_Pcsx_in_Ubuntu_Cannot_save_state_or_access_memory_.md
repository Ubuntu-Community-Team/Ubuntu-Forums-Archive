---
title: "Pcsx in Ubuntu: Cannot save state or access memory card!"
date: 2007-01-18
forum: Gaming &amp; Leisure
---

### Post by darkmaster on 2007-01-18
Hi everyone! I really can't get rid of a problem I've got using Pcsx emulator.
First of all, I've got an Nvidia geforce go 7600 and everything's working fine, running aiglx + beryl at the moment. 

My issue is: I downloaded Pcsx using the repos, on Ubuntu edgy eft, and everything was Ok. When I run the emulator, after configuring it fine, it works great but... when I run an iso image, the little main window closes, another window opens asking me the filename to load and when I choose the file, this new window remains opened and another one, with the screen size I choose in pete's 3D plugin, opens, with the game in it. So basically, first thing I noticed: the main window of the emulator closes immediatly, when I run a game. So, if this window is closed and only the one with the game's opened, How can I save a state?

I have to access the menu to save a state. It is done by File --> states --> save or load state. So, how can I save a state? It says that with Maiusc + 1 (Shift + 1 ???) the state should be saved in slot 1 (Of what?) but even with this command during the game, nothing happens and nothing is saved. My feeling is that the main Pcsx windows should not close after I ask it to run an iso... is it correct? If yes, why does it happen????

And another weird thing. if, in a game, I access the memory card and choose to save, it starts checking and remains like this forever. The check goes on in loop but the game is not crashed or something... simply, the game continues checking forever! Why is this? memory cards are setted up as I can see... 2 memcards in my home folder....

Can anyone help me with this problems preventing me from playing this wnderfull psx emulator? And don't tell me to use epsxe... I tryed it but after some seconds the game freezes and then return normal and this process goes on for the entire game... so it is basically unplayable. And there's no sound to since it tryes to use the OSS plugin! It doesn't work for me, I'd need alsa. 

The post is about a problem with Pcsx, so, please, can anyone hel me?

---

### Post by cborga1985 on 2007-01-18
epsxe has always worked great for me. try installing epsxe from [asher256's repo]("http://asher256-repository.tuxfamily.org/index.php?page=home&lang=en"). oss should not cause it to crash. another thing is that alsa has oss emulation so that shouldn't be a problem.

---

### Post by pathdoc on 2007-01-20
Hi,

I've got the exact same problem.  Installed pcsx from repos and I cannot save to the memory cards.  The system does not hang, but nothing i do lets the games be saved.

I tried installing epsxe from asher's repos and I'm having the same problem.
any ideas?

---

### Post by tenshi-no-shi on 2007-03-17
I am having the same problem. I can't even do save states, what is going on?

---

### Post by kopilo on 2007-03-18
have you check the director that pcsx tries to save to is either owned by your user login and that it is not write protected?

Also if you haven´t already, try ´formatting´ the card before saving to it.

Configuration -> Memory Cards --> Format

---

### Post by Duncan_Idaho on 2007-03-23
I have that problems too, the main window close when running a game, when want to save the game enters an eternal loop searching for a card
I tried formatting them, but that didn't work :(
also, saving/loading states with keyboard doesn't work at all

---

### Post by siman on 2007-03-24
i'd like to point you to [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/) (as disturbedite did for me)

i too had problems with pcsx and epsxe... psX just worked

> **disturbedite said:**
> this is just a heads up, but if you're interested in ps1 emulation, there is good news!  [pSX]("http://psxemulator.gazaxian.com/") is a new(er) emulator for the ps with great compatibility and something unique among ps emulators:  its designed to be plugin free!  i was surprised and glad that ps emulation had picked back up for linux.  i'd encourage you to check it out if you're interested in ps emulation.

---

### Post by Duncan_Idaho on 2007-03-24
well, it's worth trying so thanks for the link :)

---

### Post by Arlanthir on 2007-03-31
Well, here's one more with the same problem.. I just want tony hawk's 2 to work without hanging on the auto 'checking memory card' =/ It works fine with epsxe, but pcsx is better for everything else xD

---

### Post by leomelo on 2007-05-05
> **cborga1985 said:**
> epsxe has always worked great for me. try installing epsxe from [asher256's repo]("http://asher256-repository.tuxfamily.org/index.php?page=home&lang=en"). oss should not cause it to crash. another thing is that alsa has oss emulation so that shouldn't be a problem.
epsxe is not open source.

---

### Post by jerome1232 on 2008-04-21
Through trial and error i figured out that in pcsx, F1 saves state, F2 switches the save slot, F3 loads state, F4 gives a thumbnail view of the save slot currently active :) cheers (pSX may "just work" but the plugins produce better looking graphics)

---

### Post by drunkmatador on 2008-05-06
Thanks! I was trying to figure out the same thing.. can't get back to the main menu once a game is loaded. But all I really needed were the keyboard shortcuts, I suppose.

Now I just need to figure out how to load different video and audio drivers and I'll be set.

---

### Post by acoustibop on 2008-05-07
PSEmulator plugins may produce more impressive graphics, jerome1232, but I'll go with pSX' more accurate graphics any day.

The thing that really surprised me when pSX first came out (for Windows) a bit over a couple of years ago was the difference in graphics: I hadn't realised just how much enhancement distorts the game.  Many of my games were NTSC ones that I couldn't play on my PAL Playstation; I really thought that that's how some of them must look until pSX disabused me of this misconception.

For me, "better looking" is how the game really looks, not an aggregation of atifacts and distorted images.

I'd also warn against depending on save states: over time, a game in progress tends to accumulate errors that accumulate to the point where they cause glitches in the game and finally make it unplayable.  Saving to a memory card effectively strips out these errors, so when you reload from the memory card, you have a clean game again.  Save states, however, are a 'snapshot' of the game at that point and include any errors that have occured up to that point.  So, in reloading the save state, you reload the errors.

This apparently will happen even with a Playstation: usually, because there's no equivalent to save states, you always save to memory cards and this corrects the problem.  But apparently, people who have played games on a Playstation without saving and reloading for very long periods (we're talking tens of hours) have observed the same problem.

---

### Post by jerome1232 on 2008-05-07
Yeah I think i actually have to agree with you on that about the graphics, I just like how it can smooth out the sprites mostly,(FF9 looks much better sprite wise) That's interesting about the save states vs memcards, so using save states, then once you get to save location, save, load then save a state over you're old state, wouldn't this fix that issue?

---

### Post by acoustibop on 2008-05-08
Yes, that should be fine if you're saving your save state from a clean game, jerome1232.  What I usually do is use save states as much as I like during a playing session, but always end with a memory card save and always start the next session by loading from that save.  That should be more than enough to keep the game clean, unless you're doing monster playing sessions! ;)

---

### Post by nocturn@shadowground.com on 2008-05-25
hey,


i'm new to the pcsx but i think its the only one that i can use as i'm a mac OS X user. just having a few problems and wondering if there was any way round them or if anyone could shed some light on the situation.

i don't really understand the memory card or the freexe states. mainly cause i have been playing a game but it won't save to the memory card. it just says it can't find it but leaves no option for me to direct it two them. and the freeze states literally freeze the controls when defrosted. i'm not having a lot of luck with the preferences cause they are kind of limited. therefore there's only so much i can change and i'm not seeing any positive effects. can someone help me out. if theres a better emu out there or specific things i should be looking to change??


help would be greatly appreciated, cheers
p.

---

### Post by Drokles on 2009-05-27
I don't quite understand why this helps, but it does.

Try downloading a sony bios (without being illegal about it, because I think most online communities aren't supposed to encourage that.) This works if the your problem is corrupted save files after you've tried saving.

Something you also may want to do is put your memory card in a directory that has a shorter name. I've heard that is a solution to some OS.

Best of luck in any case!
~ Drokles

P.S. I'd like to point everyone reading this to the pcsx-r emulator:
[http://www.codeplex.com/pcsxr](http://www.codeplex.com/pcsxr)

It works brilliantly!
I must admit that I've only tested it with FF9 so far, but the only flaw until now has been the framerate dropping slightly for a second at a time when loading the menu or entering combat.

---

