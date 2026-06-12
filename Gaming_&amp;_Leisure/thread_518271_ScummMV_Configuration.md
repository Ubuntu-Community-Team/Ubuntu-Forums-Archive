---
title: "ScummMV Configuration"
date: 2007-08-05
forum: Gaming &amp; Leisure
---

### Post by tgbrowning on 2007-08-05
I'm having a difficult time with running ScummMV and Flight-of-the-Amazon.  Specifically, I'm deaf and have to use subtitles. Then there's the fact that I have vision problems.  Hence, I need the subtitles and I need enought time to read the darn things. Unfortunuately, the max length for the time (255) is to short for me to to read the subtitles on the first go.  

I need to slow down my machine (I'm running this under Feisty Fawn, on a HP Pavilion dv2000), AMD Turion64 dual core and Nvidia video drivers.  

Is there a simple way to slow down the application? I'm not sure what power options might do under Ubuntu or even if that might be an avenue to pursue. 

Thanks in advance.

Browning>>>

---

### Post by hikaricore on 2007-08-05
You should be able to slow it down with [powernowd]("http://packages.ubuntu.com/feisty/admin/powernowd") assuming it supports your cpu.

I can't remember if it's installed by defualt in Feisty or not, but it can be installed with:

```
sudo aptitude install powernowd
```

Then remember to read the man pages to find out how to use it.  ^_^

```
man powernowd
```

---

### Post by rrinker on 2007-08-05
Hmm, I'll have to check that one out. I don't use the subtitles because I have to, I use them because I prefer to not turn the speakers on unless I'm playing music or watching a movie. I read fast, but the slowest speed is just a bit too fast for the longer dialogs.

---

### Post by tgbrowning on 2007-08-05
Thanks -- I'll give that a whirl. I expect that will be the case in a lot of the older apps I was thinking of revisiting.  Much obliged.

Browning>>>

---

### Post by BoyOfDestiny on 2007-08-06
> **tgbrowning said:**
> I'm having a difficult time with running ScummMV and Flight-of-the-Amazon.  Specifically, I'm deaf and have to use subtitles. Then there's the fact that I have vision problems.  Hence, I need the subtitles and I need enought time to read the darn things. Unfortunuately, the max length for the time (255) is to short for me to to read the subtitles on the first go.  

I need to slow down my machine (I'm running this under Feisty Fawn, on a HP Pavilion dv2000), AMD Turion64 dual core and Nvidia video drivers.  

Is there a simple way to slow down the application? I'm not sure what power options might do under Ubuntu or even if that might be an avenue to pursue. 

Thanks in advance.

Browning>>>

Hi, press space to pause/unpause the game.
Hopefully that will do the trick :)

EDIT: Doh, I just realized that doesn't apply to all of the scummvm supported games...

EDIT2: Ok I think I found a solution.
If you run scummvm from a terminal
ctrl + z will pause
type fg to resume

try this out from a terminal

scummvm --talkspeed=255 -n -g hq3x --aspect-ratio queen

Note: replace hq3x with 3x if you just want it scaled (no smoothing)

The only downside is the terminal has to have focus.
If someone knows of a hotkey, please share it.

The alternative if the powernowd suggested thing doesn't work, is to use dosbox, and try the DOS version of flight of the amazon queen (it's freeware now too after all). 

It is very easy to slow down the game (ctrl+F11) or pause on the fly (alt+pause) under Dosbox (GPL and in the repos.)

Here is a screencap of scummvm showing the hq3x rendering, and ctrl+z to pause it

---

