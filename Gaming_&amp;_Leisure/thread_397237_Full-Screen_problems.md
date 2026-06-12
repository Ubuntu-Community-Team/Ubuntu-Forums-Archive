---
title: "Full-Screen problems"
date: 2007-03-30
forum: Gaming &amp; Leisure
---

### Post by tm0054 on 2007-03-30
I asked this question a while back but didn't get any difinitive answers... To start I am running Ubuntu 6.10 (Edgy).

I enjoy the games available for Ubuntu, but on my 1200x800 laptop there isn't a single game that will go into full-screen mode. Whether I select full-screen or windowed mode all games I've tried show up in a small window. I've tried setting my screen to 1024x768 (thinking it might be having difficulty with a widescreen resolution), but no luck-  the same issue exists.

ZSnes, KQ, and a handful of other games all refuse to switch into full screen mode. (ZSnes under Vista works in full screen mode no prob)

I have a desktop machine w/Ubuntu set to 1280x1024 and full screen works like a dream on that machine so I know it's related to my laptop somehow. I want my laptop to work as it is my main computer.

Info about my laptop:

It has a generic Intel Video card, and I am running 915Resolution to get it to work in 1200x800 mode.

Are there any tricks/programs I can install to allow games to switch into full screen?

---

### Post by califman831 on 2007-04-26
I would also like to run games in full screen, like warzone2100, just gives me a small window and I can't figure out how to enlarge it.

---

### Post by cogadh on 2007-04-26
Most games only support a limited number of resolutions and those resolutions are standard sizes that a normal CRTor LCD can run (640X480, 800X600, 1024X768, 1280X1024). I've only seen a few games that have an "enable widescreen" option and those are usually newer retail games. Unfortunately, you can't make a game that was designed around a standard resolution scale up to a non-standard resolution. This is espescially true of older games like Warzone  2100. That one is actually designed around a 640X480 default resolution and it can scale up to 800X600, but no higher than that.

---

### Post by Inigo Montoya on 2007-04-27
my guess is that its x-server related (at least for some games...). could you post your _/etc/X11/xorg.conf_ file.
[INDENT]<if you don't know what the x-server is>
the x-server (on ubuntu Xorg) is the software all the graphic applications run on. it provides the very basic things for the graphical user interface, games and other applications.
</if you don't know what the x-server is>[/INDENT]
why could it be x-server related?
there is a section in your xorg.conf which describes which resolutions could be used. as far as i remember this was set to 1280X800 on my laptop when i installed 7.04. this might be the case for you too.

---

### Post by antiemptyv on 2007-07-20
> **califman831 said:**
> I would also like to run games in full screen, like warzone2100, just gives me a small window and I can't figure out how to enlarge it.

this was posted a while ago, buuuttt try ALT+Enter.

---

### Post by dimeotane on 2007-09-20
here's the solution for warzone 2100 when you get a large black border around a small 800x600 section of the game.  Make a launcher to lunch the game with the resolution of your monitor... in the case of my little notebook LCD display, I use the command: 

warzone2100 --resolution 1280x800

thats TWO hyphens in a row - and -

---

