---
title: "Lower games performances in Natty 11.04"
date: 2011-05-10
forum: Gaming &amp; Leisure
---

### Post by elect on 2011-05-10
Hello,

I am not sure if this is the right place...

However I am experiencing some very lower performance playing ut2004.. (i750, 5850 and 4gb)


I thought it could have been the upgrade, so I installed 11.04 by zero, nothing changed...

Last AMD drivers

ati-driver-installer-11-4-x86.x86_64


I wonder why it's like this... should I install some old kernel?

Now I'm using 


Linux elect-desktop 2.6.38-9-generic #43-Ubuntu SMP Thu Apr 28 15:23:06 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Jagoly on 2011-05-10
for me the reverse was true (the switch to xubuntu might have had something to do with it)

what sort of reduction are we talking about? 3fps or 30fps?

---

### Post by elect on 2011-05-10
> **Jagoly said:**
> for me the reverse was true (the switch to xubuntu might have had something to do with it)

what sort of reduction are we talking about? 3fps or 30fps?

I dont know exactly, but originally it was completely fluid at high details and now not even a low..

Also the loading map times, before it was used to take about 10s, not almost 30s...

---

### Post by Jagoly on 2011-05-10
Well, then that would definitely be a case of something not working properly. Is the slow down pretty much for anything highly graphical? A lot of people (including me) are having problems with these drivers on 11.04. Are you using unity or gnome 2?

---

### Post by keltic dave on 2011-05-10
it could be the ati drivers

In my experience nvidia > ati  things just work generally better on nvidia hardware on linux than ati.

---

### Post by Jagoly on 2011-05-10
> **keltic dave said:**
> it could be the ati drivers

In my experience nvidia > ati  things just work generally better on nvidia hardware on linux than ati.

That's true, but some people still have machines with ati cards, Eg, got laptop as a gift from parents. We can't all afford to go out and by a new machine. Perfonce wise the ati cards are fine. The problem is getting certain things to work at all.

---

### Post by elect on 2011-05-11
> **Jagoly said:**
> Well, then that would definitely be a case of something not working properly. Is the slow down pretty much for anything highly graphical? A lot of people (including me) are having problems with these drivers on 11.04. Are you using unity or gnome 2?

Unity

So you think I should try the previous ones...?

---

### Post by oldrocker99 on 2011-05-11
I dual boot with Windoze 7 (just for games), and I had a weird smearing across my Dell ST2010 monitor in Windows AND Ubuntu with the latest ATI drivers. Then, yesterday, the smearing disappeared in both systems. Go figure...

---

### Post by elect on 2011-05-11
> **oldrocker99 said:**
> I dual boot with Windoze 7 (just for games), and I had a weird smearing across my Dell ST2010 monitor in Windows AND Ubuntu with the latest ATI drivers. Then, yesterday, the smearing disappeared in both systems. Go figure...

What u mean exactly with "smearing"?

---

### Post by mastablasta on 2011-05-12
> **elect said:**
> Unity
 
So you think I should try the previous ones...?
 
 
try switching to classic Gnome. Linux has a stupid habbit of prioritizing desktop (and desktop effects) instead of programmes. so for example eventhough you run a game full screen all your desktop shortcuts might be active.
 
same thing here... and this goes especially for Unity which is running some sort of desktop effects. disabling these effects (if still possible in Gnome classic) can give quite a performance boost. 
 
If oyu ask em wheneevr user is running some porgramme like game full screen desktop effects should automaticly be turned off.

---

### Post by oldrocker99 on 2011-05-12
> **elect said:**
> What u mean exactly with "smearing"?

I mean that there were multiple "shadows" to the right of any high-contrast thing on the screen (like the cursor or a mouse pointer), which made the display distressingly unwatchable. Then, it went away, and the display on both systems is as sharp as a tack.

Again, go figure.

---

### Post by sparkler on 2011-05-12
ive been having problems with 11.04 and ati as well its really laggy even moving windows around is laggy i wish i stuck with nvidia

---

### Post by elect on 2011-05-14
> **mastablasta said:**
> try switching to classic Gnome. Linux has a stupid habbit of prioritizing desktop (and desktop effects) instead of programmes. so for example eventhough you run a game full screen all your desktop shortcuts might be active.
 
same thing here... and this goes especially for Unity which is running some sort of desktop effects. disabling these effects (if still possible in Gnome classic) can give quite a performance boost. 
 
If oyu ask em wheneevr user is running some porgramme like game full screen desktop effects should automaticly be turned off.

I will, but first I wanna try the last drivers

11.5	released on 5/9/2011 ^^

---

### Post by elect on 2011-05-14
> **elect said:**
> I will, but first I wanna try the last drivers

11.5	released on 5/9/2011 ^^



No improvements :(

---

### Post by elect on 2011-05-15
Found this

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/763005)


no success for me

---

### Post by Dlambert on 2011-05-17
Ubuntu natty uses unity. (RESOURCE HOG) try unity 2d maybe? Just a suggestion.

---

### Post by oldrocker99 on 2011-05-17
For best game performance, you should install xubuntu or lubuntu and log in to that. Works for me. Then you can go back to Unity, or you may like the speed (or dislike the things that you take for granted in GNOME and which are a lot more hidden in the lighter-weight desktops. One of the many, many great things about GNU/Linux is the choice of GUIs available, from extremely featured, to stripped down and bare, from utility to speed. But I digress:oops:)

To make it easy, search Lubuntu in the Software Center. You might like it.

---

### Post by Dlambert on 2011-05-18
Lubuntu's great (for 32 bit) use xubuntu if you want 64 bit

---

### Post by elect on 2011-05-24
You didnt get the problem, cmon, with the previous ubuntu and older drivers everything was fine..

Its not a problem related to my computer's performances..

---

### Post by thepiratefish on 2011-05-25
wait some of you guys use lubuntu to game on instead of ubuntu?

---

### Post by elect on 2011-05-25
I tried the new 2.6.39

ut2004 crashes :(

---

### Post by elect on 2011-05-25
2.6.35-22  has no network connectivity


dhclient doesnt work, dunno why :/

---

### Post by elect on 2011-05-28
up

---

### Post by bud986 on 2011-05-28
Unity is performance killer nr1 Heroes of newerth is now unplayable for me :P

---

### Post by elect on 2011-05-28
Unity is disabled

---

### Post by Omegus on 2011-05-28
I myself have 10.10 with ati card and a amd processor  and I have never had any sort of graphics related preformance .plus I have unity active.

---

### Post by elect on 2011-05-28
> **Omegus said:**
> I myself have 10.10 with ati card and a amd processor  and I have never had any sort of graphics related preformance .plus I have unity active.

gpu?

---

### Post by Omegus on 2011-05-29
Radeon HD5850 1GB

---

### Post by elect on 2011-05-30
> **Omegus said:**
> Radeon HD5850 1GB

and do you have the last amd driver? 11.5?

Kernel?

---

### Post by alexou2648 on 2011-05-30
Guys, i really have a strange issue since i updated from 10.04 to 11.04 (by updating before to 10.10). When i move my mouse in the bot-right corner of the screen, it freezes the screen for some seconds. I first thought it was a bug inside Heroes of Newerth, since i had lags and freezes when i moved the mouse on the map (which is on the bot-right corner for me)...but it's on the desktop too...
So, where should i put this strange issue? I guess it's Xorg related. I'm using the last kernel on natty, on x86_64 with the 11.5 ati driver.

---

### Post by elect on 2011-06-03
up

---

### Post by elect on 2011-06-14
up

---

### Post by jborgmann on 2011-07-01
Everything seems to work fine for me...until I get into a game.  Intro animations are fine, menus are fine, settings, etc all work fine.  Even the weapons viewer works fine.

However, when I try to enter a game, the game loading screen is all black with white text (it's been a few years but I remember there being an image on the loading screen) and then once I get dumped into the game I have no mouse, no meshes (like I can't see my player/weapon).  The environment is fine, sound is fine, but that is it.

At that point my only option is to break out to a virtual terminal and kill the process.  The GUI is completely locked up at that point.

Going to give Gnome Classic a shot but I may have to resort to using Crossover or Cedega.  :(

---

