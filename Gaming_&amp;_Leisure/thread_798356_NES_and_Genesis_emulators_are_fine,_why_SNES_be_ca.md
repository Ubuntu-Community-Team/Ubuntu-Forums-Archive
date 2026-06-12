---
title: "NES and Genesis emulators are fine, why SNES be causing trouble?"
date: 2008-05-18
forum: Gaming &amp; Leisure
---

### Post by SZF2001 on 2008-05-18
Maybe it's because I'm not playing with power, but the thing is I can manage to run Genesis games nearly perfectly (thanks [Gens](http://ubuntuforums.org/showthread.php?t=290008&highlight=gens)!) and NES games of course very easily (with that GFCE Ultra NES Emulator). Here's the thing; SNES games run with trouble. Allow me to explain:

You see, I can't manage to get sound going. Yes, I did do a search through the forums because there are plenty of other "ZSNES is being crackly" threads. I used [this thread](http://ubuntuforums.org/showthread.php?t=733387&highlight=zsnes) to fix the major crackling, but it still seems that games WILL crackle no matter what I do with the settings in the Sounds options. And some frame issues but those aren't a huge deal.

I used Envy to install propriety nVidia drivers. My card is an old crap 64MB one but it would handle SNES games just fine on Windows...

Also using Xubuntu so there shouldn't be memory hogs around.

I've tried Snes9express and gsnes9x, which are basically the same, but neither can pick up my MS Sidewinder OLD SCHOOL dpad controller (but everything else can, seeing how I've added the modules for it to the modprobe file at bootup). They also don't have permission to do jack crap with any settings I make. Even under su (I know that's a bad idea, but I had to try)...

Any ideas?

---

### Post by BigSilly on 2008-05-18
I run ZSNES with the command -

```
zsnes -ad sdl
```

I created a launcher on my panel, and have that as the command to launch it (right click, Properties/Command on the panel launcher). Also, I set the sampling rate to 48000hz in Config/Sound in ZSNES. I have libsdl1.2debian-all installed, but I'm not sure if this makes a difference. Still, mine works without crackles now so I happy.

EDIT: Sorry, should have read your link. You've obviously tried this and still have issues.

---

### Post by acoustibop on 2008-05-18
You've pointed us to the thread you consulted, SZF2001, but you haven't said what you actually tried.

As I advised there, install libsdl1.2debian-all.  Don't worry if this removes any other SDL drivers; support for them will be reinstated in the libsdl1.2debian-all package.  This is a useful step for fixing sound problems in a number of applications, including games.

Then do 'znses --help' in a terminal; this will give you, amongst other information, a list of the optional sound drivers.  Go through this list, starting zsnes with 'zsnes -ad <sound driver>' where <sound driver> is the particular one you want to try, until you find the one that works best for you.  Then do 'zsnes -ad <sound driver>' again with the driver that works best, this will set it in configuration, so ZSNES will use it from then on.

---

### Post by SZF2001 on 2008-05-18
Here's an idea;

In Gens nothing worked right until I made it switch to OpenGl. Now it works like a charm. Is there some way to force zsnes to use OpenGl, or does it already, or what? I used the --help command but I don't see anything relative to that...

---

### Post by acoustibop on 2008-05-18
Look on the video configuration tab.  Display modes with an 'O' use OpenGL.

So, again, what have you actually tried?

---

### Post by frenchn00b on 2008-05-18
> **SZF2001 said:**
> Maybe it's because I'm not playing with power, but the thing is I can manage to run Genesis games nearly perfectly (thanks [Gens](http://ubuntuforums.org/showthread.php?t=290008&highlight=gens)!) and NES games of course very easily (with that GFCE Ultra NES Emulator). Here's the thing; SNES games run with trouble. Allow me to explain:

You see, I can't manage to get sound going. Yes, I did do a search through the forums because there are plenty of other "ZSNES is being crackly" threads. I used [this thread](http://ubuntuforums.org/showthread.php?t=733387&highlight=zsnes) to fix the major crackling, but it still seems that games WILL crackle no matter what I do with the settings in the Sounds options. And some frame issues but those aren't a huge deal.

I used Envy to install propriety nVidia drivers. My card is an old crap 64MB one but it would handle SNES games just fine on Windows...

Also using Xubuntu so there shouldn't be memory hogs around.

I've tried Snes9express and gsnes9x, which are basically the same, but neither can pick up my MS Sidewinder OLD SCHOOL dpad controller (but everything else can, seeing how I've added the modules for it to the modprobe file at bootup). They also don't have permission to do jack crap with any settings I make. Even under su (I know that's a bad idea, but I had to try)...

Any ideas?

in any cases, as alternatives : 
xe [http://xe-emulator.com/index.php?m=shots&lm=about&ls=](http://xe-emulator.com/index.php?m=shots&lm=about&ls=)
sdlmess  => [http://www.mess.org/](http://www.mess.org/)

---

### Post by disturbedite on 2008-05-18
i've stated in several of those "ZSNES crackly sound" threads that there is a known issue of zsnes having crackly sound on computers with onboard (built-in) sound chips.  do you happen to have one of those?
i have one, but fortunately, i never encountered the problem using the packages from the repo.  (although i did get the problem when compiling zsnes from svn).

---

### Post by SZF2001 on 2008-05-18
> **disturbedite said:**
> i've stated in several of those "ZSNES crackly sound" threads that there is a known issue of zsnes having crackly sound on computers with onboard (built-in) sound chips.  do you happen to have one of those?
i have one, but fortunately, i never encountered the problem using the packages from the repo.  (although i did get the problem when compiling zsnes from svn).

I have me a sound card on the PCI board, or whatever it's called. I can take it out. So that's probably enough description to tell you that it's not an onboard one... I remember getdeb had a good zsnes package, one that was better than the one in the repo. But that was forever ago. :(

> **frenchn00b said:**
> in any cases, as alternatives : 
xe [http://xe-emulator.com/index.php?m=shots&lm=about&ls=](http://xe-emulator.com/index.php?m=shots&lm=about&ls=)
sdlmess  => [http://www.mess.org/](http://www.mess.org/)

Thanks, I'll be sure to try them out!

> **acoustibop said:**
> Look on the video configuration tab.  Display modes with an 'O' use OpenGL.

So, again, what have you actually tried?

I'll look for those.

What I have done is mess around with the video settings, usually 800x600 fullscreen does a pretty good job but otherwise I've turned off all fancy filtering and basically anything having to do with Super Eagle. I've also used the terminal to find the right sound output, like the thread says to do.

I've also tried going into the sound options and turning everything off (like the 8-point something)... I'm not sure what else to try besides the other suggestions which I'll get back on.

---

### Post by mister_k81 on 2008-05-19
Did you give this version of SNES9X a try? : 

[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)

It works well for me under Hardy, with controller support and OpenGL.

---

### Post by disturbedite on 2008-05-21
just thought i'd add that zsnes is a more accurate emulator though.

---

