---
title: "Enemy Territory Problems"
date: 2006-07-18
forum: Gaming &amp; Leisure
---

### Post by _simon_ on 2006-07-18
I am experiencing random "freezing" in that the game will suddenly "freeze" on the screen and the only way to get out is press the reset button.

I thought it might be heat related as it's very hot at the moment but I can play UT2004 without an issue and that's cauing my CPU to run hotter than ET does.

I'm running version 2.60.

Athlon 3200+, 2.6.15-26-k7 Kernel
1Gb PC3200
128Mb Geforce 6800, 1.0-8762 Drivers 

Any ideas?

---

### Post by _simon_ on 2006-07-19
I guess it's just me? :-k

---

### Post by crane on 2006-07-19
I would suggest checking system logs to see if you can see the problem.
Was the game running and then caused problems or never run at all?

---

### Post by maxx_730 on 2006-07-19
I have the same problem, my TC:E just started freezing when i click during the start movie. I tried loads of things already like reinstalling drivers, reinstalling TC:E etc etc, nothing works.

---

### Post by twa1296 on 2006-07-19
> **maxx_730 said:**
> I have the same problem, my TC:E just started freezing when i click during the start movie. I tried loads of things already like reinstalling drivers, reinstalling TC:E etc etc, nothing works.

exactly the same problem here. i've gotten it to work once after a reinstall. but after a reboot the same freeze occurred again. have tried reinstalling since, without success.

it all seems very strange since i've been using et and tc:e on this setup for months now and there haven't been any updates recently.

has anyone with this problem been able to get some terminal output? or does anyone know how to log the terminal output (fullscreen freeze hides terminal)?

---

### Post by maxx_730 on 2006-07-19
It is working again here! This whole thing still seems  strange though. Anyone had a chance to check this on another distro? Cause if it didn't work on other distro's too ive got some et phone home conspiracy theories coming up.

---

### Post by twa1296 on 2006-07-19
> **maxx_730 said:**
> It is working again here! This whole thing still seems  strange though. Anyone had a chance to check this on another distro? Cause if it didn't work on other distro's too ive got some et phone home conspiracy theories coming up.

same same. very odd. servers were down last night apparently.

---

### Post by _simon_ on 2006-07-19
> **crane said:**
> I would suggest checking system logs to see if you can see the problem.
Was the game running and then caused problems or never run at all?

The game runs fine, I can be at any point **playing** when it just freezes. Haven't looked at logs yet... which should I be looking at?

If a server fell over whilst in play would that cause it do you think? - maybe I have been unlucky.

---

### Post by Rashid584 on 2006-07-19
I got the other problem described, where it freezes if you click during the intro video. I made my own thread about it but I guess this one is getting more responses :p

I'm gonna try playing it now, see if it magicly resolves itself. Doubt it will :(

Very very strange...doesn't seem to be giving me any problems now, although they may start again now that I;ve said that :p

-Rashid

---

### Post by crane on 2006-07-20
OK, I played this game the other night with no problems.
I will try to recreate this problem tomorrow night if I can. You guys are saying the freezing happens when you click the mouse during the start up movie?

---

### Post by B0rsuk on 2006-07-20
_simon_ : I don't know about any existing logs, but you can make it running et this way:

```
et 2>filename
```

where *filename* is, for example, messages.log .
As you can notice if you run et from console, it your console is filled with messages once you quit. So it's just a matter of redirecting messages from stderr (2) to filename. I suppose you can do it with any q3 engine game, and others.
Single '>' means log file is overwritten each time you run it this way. If you want it to append, use '>>' instead.
This way, you can also save your logs and later analyze them to make your own stats, for example with grep or awk.

**A possible reason for your crashes**
I heard there are problems with some gfx card drivers (windows) when playing ET. Freezes happen when punkbuster checks your machine's RAM for cheats.
Try playing on servers with disabled Punkbuster to see if it still freezes. If it doesn't, it's probably caused by punkbuster and you should try using different drivers.

No, server going down shouldn't cause you any problems. It would just look like you pulled the plug out of your ethernet card, 'connection interrupted' and so on.

---

### Post by _simon_ on 2006-07-20
I'll try what you have suggested, thank you. :)

---

### Post by _simon_ on 2006-07-22
ok it froze again on a server with punkbuster disabled.

Where can I find the log file I created? I did a search but it found nothing.

---

### Post by _simon_ on 2006-07-26
Just came accross the log - totally forgot about this!

The only thing it says is:

```

non-network local connections being added to access control list

```

I'm not even sure what that means.. whether it's normal or if that's the reason for the sudden freeze.

---

### Post by qrm on 2006-08-04
if the game freezes during the opening movie you should check if .cfg files like etconfig.cfg in etmain and /etpro/profiles/profilename/ dont exeed the 14 kb limit

---

### Post by missingxtension on 2006-08-08
im thinking that youre using an ati card is that correct?
i had the same problem but mi drivers disapeared and no matter how much i reconfiged my x.conf i was not able to get fglrx drivers to load
did you try checking your fglrxinfo ?

---

### Post by the_fury on 2008-10-26
I actually have a similar problem, I can play the game fine but in the middle of it (randomly, mind you) it will freeze and display a screen of what looks like a long chain of machine-gun bullets. idk if this some kind of virus or not, but nothing works, not even alt+backspace. I have to force shut down the cpu and restart.

---

### Post by reldo07 on 2009-08-23
ya i have been playing wolfenstein for about 4 years now, never had the problem until now that i start up et and i click through the video and it freezes then after about 20 secs it will go to the main menu then i click play online and it freezes again then about 20 secs later it will go to where the servers are but i cant see any servers come up. any help?

---

