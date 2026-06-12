---
title: "The Mana World"
date: 2005-09-07
forum: Gaming &amp; Leisure
---

### Post by jdodson on 2005-09-07
[SIZE=4][COLOR=Red]**The Mana World**[/COLOR]
[/SIZE]
Clipped from site([http://www.themanaworld.org](http://www.themanaworld.org))

The Mana World (TMW) is a serious effort to create an innovative free and open source MMORPG. TMW uses 2D graphics and aims to create a large and diverse interactive world. It is licensed under the GPL, making sure this game can't ever run away from you.

The project includes the development of both a client and a server, as well as the development of an online world. At the moment we're making alpha releases of the client, while our server is in early development. The eAthena free software Ragnarok Online server is used until our own server has matured enough to replace it. Once ready, we'll be making releases of our server too so anybody will be free to set up their own server and start building their own online world.

Clipped from jdodson's mind:

The Mana World is sweet freedom MMORPG and it is only a Alpha game!  The latest patch 0.0.16 added a new INN/Casino and a new skills tree.  I really recommend you check this game out.  They have big plans to make the game more than just a level grind(is currently).  You consistently have 8-12 people online([http://animesites.de/~tmw-server/online.txt](http://animesites.de/~tmw-server/online.txt)) at any given time and they are made 50/50 between new people and high level characters.

If you loved the SNES Mana game, check this out!  They push out a patch every month, so the new stuff keeps flowing.  Are you an art person?  Are you a music person?  Then contribute.  Are you a MMORPG player?  Then play.  Check it, I love this game.

My ingame player name is Nebuiz, I generally play on my lunch breaks at work and in the evenings at times.  You can check to see who is online this way: [http://animesites.de/~tmw-server/online.txt](http://animesites.de/~tmw-server/online.txt)

There might be some other dependicies, dpkg will let you know what they are and they are available in universe.  Get the files quick, no telling how long I will be able to host them.

Happy Gaming!

---

### Post by KingBahamut on 2005-09-07
The Secret of Mana and TSoM2 will always hold a special place in my heart, thus the reason that I love this game.

---

### Post by jdodson on 2005-09-07
[QUOTE=KingBahamut]The Secret of Mana and TSoM2 will always hold a special place in my heart, thus the reason that I love this game.[/QUOTE]

true dat.  i loved mana.  soooo good.  games today cant really compare in the same way really.  nowdays games just throw lighting effects and 3D, like somehow that would make an interesting story.  the story of mana alone was sweet, the game play was incredible too for its time.

---

### Post by madjo on 2005-09-07
hmm the first link you gave doesn't work (it adds a ) to the end of the link):
this does work:
[http://www.themanaworld.org/](http://www.themanaworld.org/)

btw, is it me, or does the logo look a lot like Ubuntu's? :)

---

### Post by Weav on 2005-09-07
hhhmmm I would like to try this game but for some reason it doesn't work.

I run tmw from the console the windo opens up but it just stays black nothing loads within the window. It prints this out on the console:

```

steve@ubuntu:~/Downloads$ tmw
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```
Any ideas? thanks

---

### Post by jdodson on 2005-09-07
[QUOTE=Weav]hhhmmm I would like to try this game but for some reason it doesn't work.

I run tmw from the console the windo opens up but it just stays black nothing loads within the window. It prints this out on the console:

```

steve@ubuntu:~/Downloads$ tmw
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```
Any ideas? thanks[/QUOTE]

nope.  

compile it from source, then you will have to fill in the dependencies.

---

### Post by madjo on 2005-09-10
I noticed on the downloads page of The Mana World, that they include a Debian Repository. Is it safe to grab it from there (even though it is a few versions behind), or should we really use the source and build it from there?

---

### Post by Nightblade on 2005-09-11
[QUOTE=madjo]I noticed on the downloads page of The Mana World, that they include a Debian Repository. Is it safe to grab it from there (even though it is a few versions behind), or should we really use the source and build it from there?[/QUOTE]
 I tried the debian repos but it failed due to deps.

---

### Post by seiflotfy on 2005-09-12
isnt this the secret of mana!!! 
if it is lets hope square delivers us a final fantasy
and capcom a breath of fire

---

### Post by pizzach on 2005-09-12
Who ho ho ho ho.  I've been working on my rpg programming skills.  I started gba development and have don't some work on a FF3 redo in java.  But this might be my first time trying to do some actual open source project contributions.  Thanks for the link jdodson!  This is a sweet find indeed. (^_^)V

---

### Post by Nightblade on 2005-09-12
[QUOTE=pizzach]Who ho ho ho ho.  I've been working on my rpg programming skills.  I started gba development and have don't some work on a FF3 redo in java.  But this might be my first time trying to do some actual open source project contributions.  Thanks for the link jdodson!  This is a sweet find indeed. (^_^)V[/QUOTE]
 Im doin my best to be able to help there too lol ;)

---

### Post by fartbarker on 2005-09-14
[QUOTE=Nightblade]Im doin my best to be able to help there too lol ;)[/QUOTE]
 anyone still playing this? 
Looks pretty cool but not sure how I go about installing. I tried dl from those links but got error message.

---

### Post by Nightblade on 2005-09-15
[QUOTE=fartbarker]anyone still playing this? 
Looks pretty cool but not sure how I go about installing. I tried dl from those links but got error message.[/QUOTE]
 Sure ppl play, but it's mostly under development. Try getting it from CVS and compiling it, you need a lot of extra deps though.

---

### Post by lrmall01 on 2005-09-17
Looks like the files above are no longer hosted - I get broken links.

If you add TMWs repositories and try to install you get this on Hoary:
[I]tmw:
  Depends: libcurl3 (>=7.14.0-2) but 7.12.3-2ubuntu3 is to be installed
 Depends: tmw-data but it is not going to be installed[/I]

I had this working fine on a Debian unstable setup, but I recently wiped it out to install Ubuntu.  

Any suggestions on how to get around this dependency?  Build from source I guess.

Thanks.

---

### Post by teevee on 2005-09-17
Great game.

To install it, I just added the repository to the sources list, then instead of doing "apt-get install tmw" I did "apt-get install tmw tmw-data libguichan" and it stopped complaining. ;-) Oh and don't forget tmw-music for sounds and background music.

Edit: Oh, I'm running Breezy, don't know if this makes a difference.

---

### Post by Egree on 2005-09-18
[QUOTE=teevee]Great game.

To install it, I just added the repository to the sources list, then instead of doing "apt-get install tmw" I did "apt-get install tmw tmw-data libguichan" and it stopped complaining. ;-) Oh and don't forget tmw-music for sounds and background music.

Edit: Oh, I'm running Breezy, don't know if this makes a difference.[/QUOTE]
 It works for me too (running breezy). ^_^

---

### Post by lrmall01 on 2005-09-18
I wonder if Breezy uses a different version of libcurl - regardless of how I apt-get it still has the dependency issue with libcurl

---

### Post by jdodson on 2005-09-19
[QUOTE=Egree]It works for me too (running breezy). ^_^[/QUOTE]

Yeah I think it does.  Hoary is out of sync with Debians glibc, Breezy, I believe is more uptodate.

---

### Post by fserve on 2005-09-20
[QUOTE=jdodson]Yeah I think it does.  Hoary is out of sync with Debians glibc, Breezy, I believe is more uptodate.[/QUOTE]
 then hoary isn't able to run the game?

---

### Post by plumcreek on 2005-09-30
Doesn't look like it.

---

### Post by Quirky on 2005-10-01
You can run it in Hoary. You need to compile from sources though.

Install:
build-essentials
sdl-net dev
curl dev
physfs dev
guichan (compiled from source from sourceforge)

then get the source for tmw from sourceforge. 
./configure && make
sudo make install

If you are missing a library, configure will let you know. It isn't worth the effort at the moment IMO, too beta with nothing much to do.

---

### Post by zAo on 2005-10-04
I installed by APT, on Breezy (current). Now I get:
```
$ tmw
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by tmw)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan_sdl.so.0)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan.so.0)

```

The libstdc++6 is installed.
Any ideas? Thanks.

---

### Post by madjo on 2005-10-04
I'm on hoary, and I built it from source, just fine (no error msgs or anything), but when I try to start the game I get this message:

tmw: error while loading shared libraries: libguichan_sdl.so.0: cannot open shared object file: No such file or directory


The libguichan_sdl.so.0 is in /usr/local/lib, I checked that... but why can't the game find it, when trying to start it, while it could find it, when I ran 'configure'?

---

### Post by madjo on 2005-10-05
[QUOTE=zAo]I installed by APT, on Breezy (current). Now I get:
```
$ tmw
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by tmw)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan_sdl.so.0)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan.so.0)

```

The libstdc++6 is installed.
Any ideas? Thanks.[/QUOTE]
do you have glibc installed, and if yes, is it of the correct version?

---

### Post by Quirky on 2005-10-06
[QUOTE=madjo]The libguichan_sdl.so.0 is in /usr/local/lib, I checked that... but why can't the game find it, when trying to start it, while it could find it, when I ran 'configure'?[/QUOTE]


Try running `sudo ldconfig' then try again. It could be that the lib isn't in ld's list of dynamic libraries. Happens occasionally when you install new libs.

---

### Post by madjo on 2005-10-06
[QUOTE=Quirky]Try running `sudo ldconfig' then try again. It could be that the lib isn't in ld's list of dynamic libraries. Happens occasionally when you install new libs.[/QUOTE]
thanks, that solved it :)

---

### Post by DariusTriplet on 2005-10-10
I'm having the same problem as zAo, and have no idea how to solve it.  I checked APT for "glibc", and couldn't find anything relevant to the issue.

I'm running Breezy, if that helps at all.

---

### Post by DJ_Max on 2005-10-10
[QUOTE=DariusTriplet]I'm having the same problem as zAo, and have no idea how to solve it.  I checked APT for "glibc", and couldn't find anything relevant to the issue.

I'm running Breezy, if that helps at all.[/QUOTE]
Make sure you have the dev files.

---

### Post by DariusTriplet on 2005-10-10
libc6-dev?  I already have it.

---

### Post by DJ_Max on 2005-10-10
[QUOTE=DariusTriplet]libc6-dev?  I already have it.[/QUOTE]
I meant the other libraries, (libstdc, glib, etc...)

---

