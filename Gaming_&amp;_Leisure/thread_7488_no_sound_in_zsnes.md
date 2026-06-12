---
title: "no sound in zsnes"
date: 2004-12-07
forum: Gaming &amp; Leisure
---

### Post by vontez on 2004-12-07
I'm trying to be nostalgic with zsnes, but the sound isn't working.  There aren't too many sound options within zsnes itself for me to play with.  Has anyone ran into this problem before?  I'm using an hp pavilion zt3000 laptop with ubuntu warty (obviously).

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=vontez]I'm trying to be nostalgic with zsnes, but the sound isn't working.  There aren't too many sound options within zsnes itself for me to play with.  Has anyone ran into this problem before?  I'm using an hp pavilion zt3000 laptop with ubuntu warty (obviously).[/QUOTE]

try running it as a super user. put

sudo zsnes

in console

---

### Post by vontez on 2004-12-08
Great, running zsnes as root fixed my sound problem.

I added a zsnes menu icon to my Gnome applications menu.  Is there a way I can get the program to launch with regular user privileges?  Or can I edit my zsnes.desktop file to launch the program as root?

Thanks for the help so far!

---

### Post by DoubleDangerClub on 2004-12-09
For some reason, even running zsnes as sudo doesn't get my sound working, any ideas?  All my other sound works systemwide though.  I have an Allegro card.

---

### Post by saBrEwolf on 2004-12-13
Have you guys considered using Snes9x? Its works like a dream on my system and has sound. (The only thing it doesn't do unless root is fullscreen, which is a pain). There's a graphical tool also, GSnes9x, its gtk1, but it makes life easier.

---

### Post by jpvcx on 2004-12-13
Hello,

You need to install libsdl1.2debian-esd (or alsa if you don't use esd) from universe. Libsdl1.2debian-oss conflicts with Libsdl1.2debian-esd, so apt/synaptic will remove it. Sound should work with zsnes after that. (It should also work in other sdl applications.)

---

### Post by ncohen on 2004-12-16
I've recently tried to install snes9x.  Using synaptic I can find these two entries

gsnes9x
snes9xexpress

But seem to depend on a package not in any of my repositories?  I'm new to ubuntu, can anyone explain what's going on and/or how to fix it?

snes9express:
 Depends: snes9x-x but it is not installable

Thanks

---

### Post by dfreer on 2007-05-15
check out my AMD64 repository in my sig.
even though it is an AMD64 repository I have 32-bit zsnes 1.51 and pSX in there, simply apt-get install zsnes. it is compiled with libao support so that sound doesn't sound scratchy, and it may fix your no sound issues. good luck!

---

### Post by dresnu on 2007-05-22
try what's suggested on the second post in this thread: [http://ubuntuforums.org/showthread.php?t=442192&highlight=zsnes+sound](http://ubuntuforums.org/showthread.php?t=442192&highlight=zsnes+sound).

It worked for me by just leaving esd though. This fixed also sound to other games.

---

### Post by bigdee973 on 2008-08-20
u dont need to mess with no configurations or nothing simply open up terminal..copy and paste this...

zsnes -ad sdl

sound should work perfect... dont type in sudo...that will only allow sound for root... by typing it just that way i gave it to u, all u'll have to do is click the link that was already made and it will work with sound... works perfect

---

### Post by varonbondumb on 2008-08-25
> **bigdee973 said:**
> u dont need to mess with no configurations or nothing simply open up terminal..copy and paste this...

zsnes -ad sdl

sound should work perfect... dont type in sudo...that will only allow sound for root... by typing it just that way i gave it to u, all u'll have to do is click the link that was already made and it will work with sound... works perfect

this worked great, thanks :guitar:

---

### Post by kessaris on 2008-09-14
Thank you that works well!

Just to clarify, we only need to run the code once and the zsnes will continue to operate in the same fashion when clicking its link from the games menu!

---

### Post by entic on 2008-09-28
Using zsnes -ad sdl did, indeed, activate my sound, but it's very scratchy... any ideas?

---

### Post by bigdee973 on 2008-09-30
> **entic said:**
> Using zsnes -ad sdl did, indeed, activate my sound, but it's very scratchy... any ideas?

not too sure but try opening ZSNES..CLICK CONFIG>SOUND and make sure that you have your sound sampling rate @ 48000HZ just click the sample rate box (the box with the green numbers right under sample rate) usually its 38000hz or so just click that area once at a time til its at 48000hz tell me if that works.. do that and then close zsnes or even reboot the computer and see if it works let me know

---

### Post by jsenlai on 2009-01-04
> **bigdee973 said:**
> u dont need to mess with no configurations or nothing simply open up terminal..copy and paste this...

zsnes -ad sdl

sound should work perfect... dont type in sudo...that will only allow sound for root... by typing it just that way i gave it to u, all u'll have to do is click the link that was already made and it will work with sound... works perfect

finally!! after those advice of installing this and that and didn't do any good! Thanks Alot!!

---

### Post by aryangor on 2009-12-20
> **bigdee973 said:**
> u dont need to mess with no configurations or nothing simply open up terminal..copy and paste this...

zsnes -ad sdl

sound should work perfect... dont type in sudo...that will only allow sound for root... by typing it just that way i gave it to u, all u'll have to do is click the link that was already made and it will work with sound... works perfect

worked for me 100% !!! thanQ :KS

---

### Post by bigdee973 on 2011-10-17
thanks i didnt discover this.  i got it from another thread i seen and decided to share.  sometimes u should look at manual pages for any program...almost every program installed in linux have man pages that will give you a list options/switches (e.g. zsnes -ad) and what the switches do...sometimes u can get a positive result if u open up a program with a set a switches (e.g. zsnes -dd -ad  etc)... to view man pages just open up Terminal and type man plus the program name (e.g. man zsnes , man pidgin, man whateverprogram)

---

