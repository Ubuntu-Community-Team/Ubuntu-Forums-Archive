---
title: "packaging nexiuz?"
date: 2005-06-14
forum: Gaming &amp; Leisure
---

### Post by forcotton on 2005-06-14
take a look at this [http://www.nexuiz.com/](http://www.nexuiz.com/)
This is a totally GPL game, including the maps, sounds, etc. It would be a good add on to the ubuntu game tome.  ;-)

---

### Post by sethmahoney on 2005-06-14
It looks pretty nice.  Has anyone gotten it working on Ubuntu yet?

---

### Post by gil-galad on 2005-06-14
I think I heard it is going to be in breezy.   For now you can get an excellent loki installer **[here](http://www.liflg.org/?catid=6&gameid=64)**

---

### Post by afonic on 2005-06-14
[QUOTE=forcotton]take a look at this [http://www.nexuiz.com/](http://www.nexuiz.com/)
This is a totally GPL game, including the maps, sounds, etc. It would be a good add on to the ubuntu game tome.  ;-)[/QUOTE]
 Hi,

if 3D Accelarion (OpenGL) works on your PC it's unzip and run.

Nice gfx, but the game is not that good itself. For GLP it's awesome though, and its probably the best freeware game as well.

---

### Post by Burgundavia on 2005-06-14
It will be in Breezy if someone packages it. Either us or Debian.

Corey

---

### Post by baRRacuda on 2005-06-15
yes, and it's great! :) the loki installer works fine.

---

### Post by ubuntu_demon on 2005-06-15
it will be in breezy because someone is working on packaging it see :

[https://wiki.ubuntu.com//UniverseCandidates](https://wiki.ubuntu.com//UniverseCandidates)

I have requested a backport already see :

[http://www.ubuntuforums.org/showthread.php?t=40619](http://www.ubuntuforums.org/showthread.php?t=40619)

---

### Post by sethmahoney on 2005-06-15
Anyone else have problems with the sound being super choppy?

---

### Post by afonic on 2005-06-15
[QUOTE=sethmahoney]Anyone else have problems with the sound being super choppy?[/QUOTE]
 Use the _sdl file and not the _glx one.

And if any of you is wait for an ubuntu package to try it out, don't. As I said before it's unzip and run. No compiling and stuff.

---

### Post by slux on 2005-06-15
[QUOTE=afonic]
Nice gfx, but the game is not that good itself. For GLP it's awesome though, and its probably the best freeware game as well.[/QUOTE]

Why do you think so? In my opinion it's an awesome good old hardcore deathmatch game, with some interesting twists. The competition it has are the likes of Q3, UT and UT200x. Of course if you don't like the whole game genre, then it's natural you don't like it but I'd like to hear your gripes if it's not that.

Personally I'm eagerly waiting for CTF maps and other new gametypes (and even started playing around with QuakeC to see if I could come up with some) but the basic DM is pretty cool. :)

The new patch due in a few weeks is going to address the bugs left, add some maps and bots.

sethmahoney: If you mean that the sounds always pause after a small period of playback right from the start, you're probably having sound card driver issues. I think Nexuiz uses 48kHz by default and many drivers seem to have some problems with that (mine included). Switching to alsa/oss, using the alsa OSS wrapper might help. See the Nexuiz forums for a thread on the topic with additional solutions.

---

### Post by afonic on 2005-06-15
I love deathmatch games, and yes it's good but it's also normal that it can't stand in competition with commercial ones. I have fun playing it, but if you compare it to Q3 and UT it needs a lot of work.

And I don't talk about gfx and stuff but the general "feeling". I don't like the guns and stuff for example, they should have made some better guns. And the way they shoot is too fake. I agree something like that can be fixed in the future, that's why I am patient waiting for the next update!

---

### Post by slux on 2005-06-15
[QUOTE=afonic]
And I don't talk about gfx and stuff but the general "feeling". I don't like the guns and stuff for example, they should have made some better guns. And the way they shoot is too fake. I agree something like that can be fixed in the future, that's why I am patient waiting for the next update![/QUOTE]

Could you be a bit more specific on what you find wrong with them? What do you mean by fake: gameplay or sounds or..? I don't see such a big problem or difference to the proprietary counterparts even though you might say that some of the guns have issues. Things can be fixed but the team needs feedback on perceived problems or they don't know what to fix. :)

---

### Post by afonic on 2005-06-15
[QUOTE=slux]Could you be a bit more specific on what you find wrong with them? What do you mean by fake: gameplay or sounds or..? I don't see such a big problem or difference to the proprietary counterparts even though you might say that some of the guns have issues. Things can be fixed but the team needs feedback on perceived problems or they don't know what to fix. :)[/QUOTE]
 Well, because we are getting off-topic here and because I generally like the game I want to say I don't dislike the game. Actually I play it quite a lot.

I didn't say the game is crap or that it has problems. What I am saying is that if this game is to get as good as commercial ones they have to improve some things, like the ways the guns shoot (and the effect of the shooting) as well as the guns themselves (for example the starting gun is almost useless). Also it needs some better maps, but I hope the community will make those.

---

### Post by skoal on 2005-06-15
Yippy Ki Yo...

1. download .zip
2. copy to /usr/local/games
3. unzip
4. chmod u+x nexuiz-linux-x86*
5. ./nexuiz-linux-x86-glx

and off we go! weeeee...

It's pretty well polished but with my Ti-4600 spitting polygons out faster than you can shake a stick at, it's still quite choppy at 1024 w/default settings.  Time for a quick glance at the READMEs.  Some dude kept owning me with a rail gun but the servers seem pretty active, so I'll have time to exact some revenge once I get better FPS.

Thx for the link to this game...

\\//_

---

### Post by jaakan on 2006-02-25
I wonder if anyone is making a Dev-package too.
-it would just be the souce code, which comes with the game, and would install anything else you would need to compile it.

Just an idea...

[QUOTE=ubuntu_demon]it will be in breezy because someone is working on packaging it see :

[https://wiki.ubuntu.com//UniverseCandidates](https://wiki.ubuntu.com//UniverseCandidates)

I have requested a backport already see :

[http://www.ubuntuforums.org/showthread.php?t=40619](http://www.ubuntuforums.org/showthread.php?t=40619)[/QUOTE]

---

