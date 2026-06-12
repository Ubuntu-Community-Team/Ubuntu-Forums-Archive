---
title: "Doom"
date: 2009-07-09
forum: Gaming &amp; Leisure
---

### Post by zoomy942 on 2009-07-09
So, i was diggin through some old software and found doom 1 and 2.  i googled around on how to use it with ubuntu, but everything was outdated information ad included 16 million command line switches.

Is there nothing i can install and just copy the WAD files over and just play in a window in ubuntu?

---

### Post by LinuxFox on 2009-07-09
You could try DOS Box, which plays DOS games under Linux.  Though I don't remember how to mount disks/CDs on it.  Or try a source port like [PrBoom]("http://prboom.sourceforge.net/").  You could get it via Add/Remove, or compile it.  Though if you compile it, you'll need to put the WAD file in the "/share/games/doom" directory before playing.  

Though I don't know if the WAD is on the CD or inside the installer, I don't own it.  I know this because I tried this with Freedoom, but I have a feeling it works the same way for the original games.

I hope this helps.

---

### Post by BoyOfDestiny on 2009-07-09
You don't have to worry about mounting under Linux with dosbox (well unless you need to mount a CD anyway.) If you've got your folder, i.e. DOOM, go in, right click on the exe, choose open with dosbox. 

Install dosbox via Add/Remove, Synaptic, or
```
sudo apt-get install dosbox
```

for prdoom synaptic or ```
sudo apt-get install prdoom
```

The benefit there is you can get the game to render in opengl. prboom is an interpreter, so imagine using the original game data with a custom engine.

DOSBox plays the original game exe and game data as if you were running it on a 386 or better ;) There is more overhead as dosbox is emulating a full old school x86 computer with soundcard/vidcard/ etc...

---

### Post by disturbedite on 2009-07-09
i highly recommend skulltag. it has tons of features.

[http://skulltag.com/wiki/Automatic_Installation_on_Ubuntu_and_Variants](http://skulltag.com/wiki/Automatic_Installation_on_Ubuntu_and_Variants)

---

### Post by zoomy942 on 2009-07-09
what is skulltag?

and i tried dosbox and got this

---

### Post by LinuxGamer on 2009-07-09
> **zoomy942 said:**
> what is skulltag?
[This]("http://skulltag.com/download/") is skulltag. Also use the link he gave as they have a nice auto loading script.
It is one of the better working Doom 1 and 2 Engines for Linux.

---

### Post by Grishka on 2009-07-09
> **zoomy942 said:**
> what is skulltag?

and i tried dosbox and got this

you have a Windows version of Doom, it seems. dosbox won't run Windows games. but you just need DOOM.WAD to play Doom with one it's [many source ports](http://doom.wikia.com/wiki/Source_port). I've been using [the Doomsday Engine](http://sourceforge.net/projects/deng/files/) for years, myself. both on Linux and Windows. you can get it from [it's developer's PPA](https://launchpad.net/~yagisan/+archive/ppa). the current version is a bit unstable, so you might want an older one, 1.8.6 is stable, if I'm not mistaken. and Skulltag is a Doom source port centered on a multiplayer network play.

---

### Post by ShadowTek on 2009-07-09
You could try Doom on a console emulator. There was a Doom for SNES *and* N64, and the N64 one was pretty good.

---

### Post by CharmyBee on 2009-07-10
Chocolate Doom for faithfulness, Dosbox + Doom 1.9 for even more faithfulness, and prboom for everything else. Fine here. Skulltag for multiplayer, but that's closed source and thus I can not compile it.

---

### Post by disturbedite on 2009-07-10
1. skulltag is awesome for single player too.

2. compiling skulltag isn't necessary because binaries are always released.

---

### Post by LinuxFox on 2009-07-10
> **CharmyBee said:**
> Chocolate Doom for faithfulness, Dosbox + Doom 1.9 for even more faithfulness, and prboom for everything else. Fine here. Skulltag for multiplayer, but that's closed source and thus I can not compile it.I agree, I tried Chocolate Doom to play the shareware episode once.  I plays as if you were playing it on DOS.  Even the setup windows are like DOS screens.

---

### Post by donkyhotay on 2009-07-10
> **disturbedite said:**
> compiling skulltag isn't necessary because binaries are always released.

Assuming you trust the people doing the writing/compiling. Binaries work but since you don't have access to the source code it's impossible for either you or someone you trust to verify there isn't something malicious in the code. I use linux binaries but I'll admit I feel a lot less comfortable using something without source code then something with. Given a choice between different options I always go with the open source choice. Personally I just use prboom for my doom fixes.

---

### Post by Sand &amp; Mercury on 2009-07-11
There are heaps of Linux ports around. If you want the authentic, old-school Doom experience, try Chocolate Doom: [http://www.chocolate-doom.org/wiki/index.php/Chocolate_Doom](http://www.chocolate-doom.org/wiki/index.php/Chocolate_Doom)

PrBoom is good too. My favourite though by far is GZDoom, though they only have Windows binaries (that work fine through wine). GZDoom is incredibly fast, stable, well optimized, provides a fertile ground for modders and adds OpenGL acceleration, and free up/down looking.

---

### Post by disturbedite on 2009-07-11
> **donkyhotay said:**
> Assuming you trust the people doing the writing/compiling. Binaries work but since you don't have access to the source code it's impossible for either you or someone you trust to verify there isn't something malicious in the code. I use linux binaries but I'll admit I feel a lot less comfortable using something without source code then something with. Given a choice between different options I always go with the open source choice. Personally I just use prboom for my doom fixes.

thats the silliest thing i've heard in a while. i understand the "comfort" in compiling something one's self but the forum is open for development & bug reporting where the devs frequent. i communicate with the linux dev and i'm not a member of the development team. prolly thousands if not hundreds of thousands of people use skulltag.

---

### Post by Grishka on 2009-07-11
> **disturbedite said:**
> thats the silliest thing i've heard in a while. i understand the "comfort" in compiling something one's self but the forum is open for development & bug reporting where the devs frequent. i communicate with the linux dev and i'm not a member of the development team. prolly thousands if not hundreds of thousands of people use skulltag.

trust... no one. 8-[

---

### Post by linuxguymarshall on 2009-07-11
> **disturbedite said:**
> 1. skulltag is awesome for single player too.

2. compiling skulltag isn't necessary because binaries are always released.


1.I frequent Skulltag singleplayer

2.You can't even compile. It's closed source.

---

### Post by linuxguymarshall on 2009-07-11
> **disturbedite said:**
> thats the silliest thing i've heard in a while. i understand the "comfort" in compiling something one's self but the forum is open for development & bug reporting where the devs frequent. i communicate with the linux dev and i'm not a member of the development team. prolly thousands if not hundreds of thousands of people use skulltag.


[B]
EDIT[/B] : That is was not me that was my friend whom likes to type for me. I never have been a memeber of the skulltag dev team but am currently working on getting into it. But I have seen older versions of the Skulltag source and there is nothing wrong with them

---

### Post by donkyhotay on 2009-07-12
I understand some devs reasons for going closed source rather then open source (though I disagree with them). I'll admit I'm not such a open-source purist that I won't ever use closed source software (flash, codecs, ETQW, etc.) when there isn't a good alternative. However if I do have a choice between a closed source program and an open source program I'll always choose the open source option. I don't really trust close source software, what do people have to hide in their program? Especially for something like doom where there are half a million versions out there. Maybe if I was a true doom connoisseur or something I'd realize how much better a closed source doom clone is compared to the open source prboom that I play when I want a doom fix. I just don't care enough about the game to try something else but I *do* care about whats running on my system and potential threats to it.

---

### Post by Qwerty_ on 2009-07-12
Also have a look at Odamex I had a play with this over a year ago.

---

### Post by disturbedite on 2009-07-12
> **donkyhotay said:**
> Maybe if I was a true doom connoisseur or something I'd realize how much better a closed source doom clone is compared to the open source prboom that I play when I want a doom fix. I just don't care enough about the game to try something else but I *do* care about whats running on my system and potential threats to it.

exactly. i prefer open source whenever possible as well. however, in this case skulltag is one THE BEST doom source ports imo. assuming it is a threat because it isn't open source is a huge stretch imo, in this case in particular.


> **Qwerty_ said:**
> Also have a look at Odamex I had a play with this over a year ago.

vavoom is better in my experience.

for my normal/2D dooming needs i have skulltag.

for 3D i have vavoom.

---

### Post by zoomy942 on 2009-07-14
so i downloaded skulltag.  but its in a tar format.  can anyone steer me on how to install it, get the WADS in the right place and then have a shortcut icon in the games menu?

PS - i tried skulltag in Windows and it worked great

---

### Post by disturbedite on 2009-07-15
> **zoomy942 said:**
> so i downloaded skulltag.  but its in a tar format.  can anyone steer me on how to install it, get the WADS in the right place and then have a shortcut icon in the games menu?

i gave a link. i'll post it *again*: [http://skulltag.com/wiki/Automatic_Installation_on_Ubuntu_and_Variants](http://skulltag.com/wiki/Automatic_Installation_on_Ubuntu_and_Variants)

---

### Post by zoomy942 on 2009-07-15
well crap.  this was at the top of that link.
> 
WARNING: This method of installation is only available for 32-bit users.
If you installed Ubuntu through Wubi and you have an Intel Core 2, Intel i7 or
AMD 64 processor you probably have the 64-bit edition of Linux installed.
Although not impossible, it is difficult to install Skulltag under 64-bit Linux.
You will have to wait until 97e in order to get 64-bit support at which time
packages will be available.

---

### Post by CharmyBee on 2009-07-15
There's no respect for 64-bit anywhere. It's treated like a monster. Because of that, I can't SNES or Genesis in linux either. It's horrible. :(

---

### Post by zoomy942 on 2009-07-15
so i guess i cant use skulltag

---

### Post by LinuxFox on 2009-07-15
You could also try PrBoom.  It's pretty easy to install and use, since it's in the repo, it might work.  I don't have a 64-bit system, but it wouldn't hurt to try.  I'll do a step-by-step...

[LIST=1]
[*]Go to Add/Remove, search for PrBoom and install it.  This installs PrBoom from the repo as well as the Freedoom iwad.
[*]After installing, place the iwad file (from your game) in the home folder.
[*]Go to the Terminal and type "prboom -iwad /home/user/DOOM.WAD" without quotes, and replacing user with your username.  Make sure you type the iwad's filename correctly, including caps if needed.
[/LIST]I just tried it out with the shareware Doom and it works for me.  It's not Skulltag, but it should help you play the game.  I hope this info is helpul.

---

### Post by ShadowTek on 2009-07-15
> **CharmyBee said:**
> There's no respect for 64-bit anywhere. It's treated like a monster. Because of that, I can't SNES or Genesis in linux either. It's horrible. :(

ZSNES works with 64-bit. I've been using it for a while.

Edit: lol   I hadn't installed it since Intrepid, and it looks like the 64-bit version hasn't been made for Jaunty yet.
[http://packages.ubuntu.com/search?keywords=zsnes&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=zsnes&searchon=names&suite=all&section=all)

Oh well, at least I know it *has* worked before. You'll just have to compile it yourself.

---

### Post by Grishka on 2009-07-15
> **CharmyBee said:**
> There's no respect for 64-bit anywhere. It's treated like a monster. Because of that, I can't SNES or Genesis in linux either. It's horrible. :(

I've been running snes and genesis emulators on 64-bit ubuntu for years, what problems do you have?

---

### Post by ShadowTek on 2009-07-15
Don't worry about compiling it. I just manually downloaded and installed the 64-bit package of ZSNES for Intrepid, installed it on Jaunty, and it works just fine.
[http://packages.ubuntu.com/intrepid-updates/zsnes](http://packages.ubuntu.com/intrepid-updates/zsnes)
\\:D/

---

### Post by disturbedite on 2009-07-16
there IS a 64bit version but that script is only for noobs or those too lazy to install skulltag normally.

instructions:
[http://ubuntuforums.org/showpost.php?p=4845224&postcount=3](http://ubuntuforums.org/showpost.php?p=4845224&postcount=3)

it requires the fmod audio library btw.

---

### Post by Sand &amp; Mercury on 2009-07-16
> **zoomy942 said:**
> what is skulltag?

and i tried dosbox and got this

GZDoom is for Windows, not DOS

---

### Post by zoomy942 on 2009-07-16
> **disturbedite said:**
> there IS a 64bit version but that script is only for noobs or those too lazy to install skulltag normally.

instructions:
[http://ubuntuforums.org/showpost.php?p=4845224&postcount=3](http://ubuntuforums.org/showpost.php?p=4845224&postcount=3)

it requires the fmod audio library btw.


okay.  im not a complete noob but i also want to be able to do it right also.  i looked at your link and i will look for the 64bit package on the sk site.  then can i have another step or 2?

EDIT : and you said about an fmod library...

EDIT2 : i havent seen a 64bit package.  do i just get the standard one?

---

### Post by disturbedite on 2009-07-17
actually, i beta test skulltag and use the 64bit package, but now that i think more about it, there might not be a 64bit bit package of the regular release (yet). you might have to wait for it (or request to become a beta tester, which is easy and they grant it to practically anyone). any way, download the architecture independent "Linux Base" & then the skulltag ubuntu release and try it.

also, in beta testing i use the "ubuntu" package on my opensuse distro, the "ubuntu" version actually just means the binary was produced on ubuntu, it can actually be run on any linux distro.

---

### Post by DoktorSeven on 2009-07-17
I'm very into Doom (I don't think I've gone very long between plays ever since Doom 1 was released :) ).

I use Doomsday (jdoom/deng, whatever you want to call it) for a nice modern engine (and the 1.9.0 betas have *finally* gotten to a fairly stable, playable state!) or Chocolate Doom for an authentic Doom experience.  Both compile cleanly in a 64bit environment and run well.

(But note [this bug](http://sourceforge.net/tracker/?func=detail&aid=2492813&group_id=144368&atid=758618) for Chocolate Doom, fixed in SVN.)

---

### Post by zoomy942 on 2009-07-17
> **DoktorSeven said:**
> I'm very into Doom (I don't think I've gone very long between plays ever since Doom 1 was released :) ).

I use Doomsday (jdoom/deng, whatever you want to call it) for a nice modern engine (and the 1.9.0 betas have *finally* gotten to a fairly stable, playable state!) or Chocolate Doom for an authentic Doom experience.  Both compile cleanly in a 64bit environment and run well.

(But note [this bug](http://sourceforge.net/tracker/?func=detail&aid=2492813&group_id=144368&atid=758618) for Chocolate Doom, fixed in SVN.)

with doomsday, does it have the original doom game?  i mean, you said its a modenr engine... but is it the original game still?  Also, i have the Hexen and Heretic wad files which is why skulltag was such a great fit

---

### Post by Grishka on 2009-07-17
> **zoomy942 said:**
> with doomsday, does it have the original doom game?  i mean, you said its a modenr engine... but is it the original game still?  Also, i have the Hexen and Heretic wad files which is why skulltag was such a great fit

you need the original Doom, Heretic or Hexen .WADs. custom .WADs are also supported, of course. you can turn off all extra options, filtering etc., and have Doom like it should be. but, if you want THE original Doom, why not just play in in DOSBox? or maybe under FreeDOS? or a DOS session in VirtualBox?

---

### Post by zoomy942 on 2009-07-18
so apparently doomsday isnt in the repos

---

### Post by zoomy942 on 2009-07-21
so i downloaded the 64bit skulltag tar in that first post, but im unsure what to do with it.

[http://skulltag.com/forum/viewtopic.php?f=77&t=20087&hilit=ubuntu]("http://skulltag.com/forum/viewtopic.php?f=77&t=20087&hilit=ubuntu")

---

### Post by disturbedite on 2009-07-21
ughhhhhh, i posted the instructions for the 32bit build twice and instructions for the 64bit build once. can't people read?

64bit instructions:
[http://ubuntuforums.org/showpost.php?p=4845224&postcount=3](http://ubuntuforums.org/showpost.php?p=4845224&postcount=3)

---

### Post by zoomy942 on 2009-07-21
okay

---

### Post by Grishka on 2009-07-21
> **zoomy942 said:**
> okay

```
./skulltag
```

---

### Post by zoomy942 on 2009-07-21
understood.

EDI : I see that its the audio library referenced a few posts ago.  Where can i get that library?

---

### Post by Grishka on 2009-07-21
> **zoomy942 said:**
> understood.

EDI : I see that its the audio library referenced a few posts ago.  Where can i get that library?

[http://www.fmod.org/index.php/release/version/fmodapi42404linux64.tar.gz](http://www.fmod.org/index.php/release/version/fmodapi42404linux64.tar.gz).

edit: direct link to the expected fmod version.

---

### Post by zoomy942 on 2009-07-21
okay.  it's DL'ed.  and its a folder with a makefile in it.  Guess that emans i have to complie it and i have never done that before.

---

### Post by zoomy942 on 2009-07-21
by the way, the reason i am so bullish on skulltag is because it uses a front end GUI and allows me to play hexen and heretic too.

---

### Post by Grishka on 2009-07-21
> **zoomy942 said:**
> okay.  it's DL'ed.  and its a folder with a makefile in it.  Guess that emans i have to complie it and i have never done that before.

no, these are precompiled libraries. just ```
make install
``` also, you'll have to make a symbolic link to the library.

doomsday engine also has a gui (snowberry), and runs hexen and heretic as well.

---

### Post by zoomy942 on 2009-07-21
> **Grishka said:**
> no, these are precompiled libraries. just ```
make install
``` also, you'll have to make a symbolic link to the library.

doomsday engine also has a gui (snowberry), and runs hexen and heretic as well.

a symcolic link?

and would i be better off just using doomsday?

---

### Post by zoomy942 on 2009-07-21
and it doesnt look like there is any 64bit love with doomsday

---

### Post by Grishka on 2009-07-21
> **zoomy942 said:**
> a symcolic link?

```
sudo ln -s /usr/local/lib/libfmodex64-4.24.04.so /usr/local/lib/libfmodex64.so
```

> and would i be better off just using doomsday?

idk, that's for you to decide.

> and it doesnt look like there is any 64bit love with doomsday

how come?

edit: oops, wrong version

---

### Post by zoomy942 on 2009-07-21
so 64 bit skulltag is all i get

---

### Post by zoomy942 on 2009-07-21
okay thanks for your help so far.  i went extracted the fmod stuff and did a make install on it.  no errors.  then i went back to the skulltag directory and got this.

```
zimmerman@zimmerman-tablet:~$ cd Desktop
zimmerman@zimmerman-tablet:~/Desktop$ cd Skulltag
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ ./skulltag
./skulltag: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ 


```

---

### Post by Grishka on 2009-07-21
> **zoomy942 said:**
> okay thanks for your help so far.  i went extracted the fmod stuff and did a make install on it.  no errors.  then i went back to the skulltag directory and got this.

```
zimmerman@zimmerman-tablet:~$ cd Desktop
zimmerman@zimmerman-tablet:~/Desktop$ cd Skulltag
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ ./skulltag
./skulltag: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ 


```

have you symlinked the library? if so, you may have to do ```
sudo ldconfig
```

---

### Post by zoomy942 on 2009-07-21
okay, so im starting to think maybe i just shouldnt mess with this.  i feel like it's really simple and i cant get it to work.

```
zimmerman@zimmerman-tablet:~$ sudo ldconfig
zimmerman@zimmerman-tablet:~$ cd Desktop
zimmerman@zimmerman-tablet:~/Desktop$ cd Skulltag
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ ./skulltag
./skulltag: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ 

```

---

### Post by Grishka on 2009-07-21
> **zoomy942 said:**
> okay, so im starting to think maybe i just shouldnt mess with this.  i feel like it's really simple and i cant get it to work.

```
zimmerman@zimmerman-tablet:~$ sudo ldconfig
zimmerman@zimmerman-tablet:~$ cd Desktop
zimmerman@zimmerman-tablet:~/Desktop$ cd Skulltag
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ ./skulltag
./skulltag: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory
zimmerman@zimmerman-tablet:~/Desktop/Skulltag$ 

```

check (with nautilus, for example) if libfmodex64.so and libfmodex64-4.24.04.so are in /usr/local/lib. if not, go back a few steps. or run nautilus with gksudo, and use the right-click menu to copy the library and make a proper symlink.

---

### Post by zoomy942 on 2009-07-21
yes sir

---

### Post by Grishka on 2009-07-21
you have a wrong version, it needs 4.24.04. I'm getting dizzy. :lol:

---

### Post by zoomy942 on 2009-07-21
lol.  didnt work.  screw it.  I'll just use my XP VM for my doom fix.  ScummVM works in linux for monkey island so im set

---

### Post by Grishka on 2009-07-22
> **zoomy942 said:**
> lol.  didnt work.  screw it.  I'll just use my XP VM for my doom fix.  ScummVM works in linux for monkey island so im set

I gave you a direct link to the right version, yet you managed to get the wrong one. ^^ I want some of what you're smoking.

---

### Post by Sand &amp; Mercury on 2009-07-27
I know this isn't directly related to the discussion at hand, but I just realised today that I've been playing Doom regularly for 14 years. I am firmly convinced that thanks to its modding community, it is the greatest game ever made.

---

### Post by ELD on 2009-07-27
Uhm instead of using emulation like dosbox you could always use a native port?

[http://www.gamingonlinux.info/viewitem.php?iid=23](http://www.gamingonlinux.info/viewitem.php?iid=23)

---

### Post by zoomy942 on 2009-07-27
> **ELD said:**
> Uhm instead of using emulation like dosbox you could always use a native port?

[http://www.gamingonlinux.info/viewitem.php?iid=23](http://www.gamingonlinux.info/viewitem.php?iid=23)

holy crap!  i'm goonna lok into this right now

---

### Post by ELD on 2009-07-27
Glad i could help :)

---

### Post by DoktorSeven on 2009-07-27
> **Sand & Mercury said:**
> I know this isn't directly related to the discussion at hand, but I just realised today that I've been playing Doom regularly for 14 years. I am firmly convinced that thanks to its modding community, it is the greatest game ever made.

This is exactly right.  And yes, so have I.  I don't think I've ever stopped playing the original Doom games since Doom 1 Shareware was released.

Best Game Ever. :)

---

### Post by zoomy942 on 2009-07-29
> **ELD said:**
> Glad i could help :)

so im poking around the site and the source site and im not seeing anything that tells me how to run it.  shed any light?

---

### Post by grossaffe on 2009-07-30
> **zoomy942 said:**
> so im poking around the site and the source site and im not seeing anything that tells me how to run it.  shed any light?
try this one.  I am a fan of the Enhanced Doom Gaming Engine.
[http://edge.sourceforge.net/](http://edge.sourceforge.net/)

---

### Post by n97ua on 2009-09-13
I loaded  ( FreeDoom )  and when it did not run on my system,  I googled the problem and someone posted that they also had issues that were resolved by loading the  ( TiMidity  ) sound package into Ubuntu.

Apparently it was not made a dependency for the app.  It should have been.

Anyway... Why run it in DOS when the full screen Linux version is just as good.  

Ubuntu is free remember.  So is that version of ID's Doom.  That's why its FreeDoom.

After my first cup of Ubuntu and the help I get out here I am hooked.

Never going back now.  Ubuntu is the best thing that I ever did.  I did not think so at first but now I am.  It takes only a few weeks to finally get away from Microsoft stuff, but boy am I glad I did.

Ubuntu keeps getting better every minute.

---

### Post by Twistedsnail on 2009-09-13
dosbox works for me with windows games....

have you got the newest version ( I was having similar problems but when i got the newest everything worked)

---

### Post by CharmyBee on 2009-09-13
> **Twistedsnail said:**
> dosbox works for me with windows games....
If those Windows games were for Windows 3.11 and had you set up that OS as well, then yes, it would.

---

