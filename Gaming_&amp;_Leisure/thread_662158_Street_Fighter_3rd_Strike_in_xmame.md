---
title: "Street Fighter 3rd Strike in xmame"
date: 2008-01-08
forum: Gaming &amp; Leisure
---

### Post by stevothewise on 2008-01-08
Lately I began to switch from Windows to Linux a bit more and one thing I do a lot of the time is play Street Fighter 3 on Mame. Works near perfectly on the windows version of mame, but i've yet to get it working in xmame. Upon loading, I get:

- -
There are known problems with this game.

This game lacks sound. THIS GAME DOESN'T WORK. You won't be able to make it work correctly. Don't bother.

Type OK to continue.
- -

Is there any way to configure xmame to work so that this rom will work? Since I know you can on a normal mame emulator. I was going to try AdvanceMame but I have absolutely no idea how to go about doing it (i am uber noob).

---

### Post by DoktorSeven on 2008-01-08
xmame is an older version of MAME, development has stopped on it.  Therefore the version is way before CPS3 (SF3 games among others) worked in it.

Search for SDLmame; it has kept up with mainline MAME and SF3:3S should work in it.

---

### Post by MaximB on 2008-01-09
> **DoktorSeven said:**
> xmame is an older version of MAME, development has stopped on it.  Therefore the version is way before CPS3 (SF3 games among others) worked in it.

Search for SDLmame; it has kept up with mainline MAME and SF3:3S should work in it.


Actually SDL mames doesn't run SF3 either.
Same problem remains.

---

### Post by DoktorSeven on 2008-01-09
Does it not?  I know Mame does and I assumed SDLmame would as well.  

I don't have the SF3 stuff so I don't know myself.

**Edit:** tested it and it worked fine in SDLmame, so yes, SF3 does work in the latest versions of SDLmame.

---

### Post by disturbedite on 2008-01-09
specifically, sdlmame ubuntu packages are here:
[http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)
this same guy has an ubuntu repo you can add to your sources.list file here:
[https://launchpad.net/~c.falco/+archive](https://launchpad.net/~c.falco/+archive)

---

### Post by stevothewise on 2008-01-09
Thanks muchly for your help ^^.
Works perfectly.

---

### Post by inversekinetix on 2008-01-09
do those ubuntu packages contain the newest mame and does the repository contain an installer for MESS?  

I cant check as Im at work now.

---

### Post by disturbedite on 2008-01-10
yes those packages do include the newest mame, sdlmame **IS** simply a mame sdl port, so it is always the same as upstream.

no he does not maintain anything mess related tho...

---

### Post by BigSilly on 2008-01-10
> **DoktorSeven said:**
> Does it not?  I know Mame does and I assumed SDLmame would as well.  

I don't have the SF3 stuff so I don't know myself.

**Edit:** tested it and it worked fine in SDLmame, so yes, SF3 does work in the latest versions of SDLmame.

I knew I wasn't going crackers! I've been playing the beautiful Street Fighter 3 Third Strike for months on Ubuntu. 

SDLMame is amazing. I play all the crazy crap I used to play on Windows just the same on Ubuntu. It even works with my joypad. Why is it not in the repository? It would be great to see it in there.

---

### Post by disturbedite on 2008-01-10
i think the guy that runs the repo i posted (c.falco) is working to try to get it included.  i believe he said he needs more reviews before it gets it's own bug for inclusion consideration.

---

### Post by MaximB on 2008-01-10
mmm...so why can't I run it ? I use SDL mame from Ubuntu repros and this game gives me that same error as mentioned in the first post.

---

### Post by inversekinetix on 2008-01-10
mame version 1.21 is available for ubuntu now?

---

### Post by wana10 on 2008-01-11
> **MaximB said:**
> mmm...so why can't I run it ? I use SDL mame from Ubuntu repros and this game gives me that same error as mentioned in the first post.

if you get the default sdlmame from the repos you get .106 and cps3 support wasn't added until .116. just go [here](http://wallyweek.altervista.org/rel122.php), grab both packages for your version of ubuntu, and install sdlmame-tools first. now place your "legal" roms (roms are always technically illegal, even if you own the original arcade board or cartridge. i personally own the dreamcast release of sf3:third strike and second impact so all my guilt of having the sf3 rom is assuaged, not in a court of law of course, but just for me personally)...where was I?...oh yes, place the roms in ~/.mame/roms and then from the command line run 'sdlmame name-of-rom' and add a -w if you want to play the game in a window (ex: for sf3 third strike enter 'sdlmame sfiii3'). to pause press 'p' and to change key assignments press 'tab'.

---

### Post by disturbedite on 2008-01-11
no, you guys are incorrect.  the "MAME" in the ubuntu repo is XMAME, *not* SDLMAME.  they are two different projects.  XMAME is dead, SDLMAME is still actively developed alongside MAME.

@ inversekinetix
no, 0.122 is available in the repo i posted.

---

### Post by MaximB on 2008-01-12
Thanks , is the a GUI for it like kxmame had ?

---

### Post by DoktorSeven on 2008-01-12
The absolute latest kxmame beta (not in the repos, available on the [SF site](http://sourceforge.net/projects/kxmame) as "kxmame-2.0-svn20070603") will work with SDLmame just fine, which is what I use.  It's in source form only, though, which means you'll have to grab all that fun compiling stuff (build-essential) and KDE development packages (kde-devel) to build it.

Unless someone can provide a package.

---

### Post by disturbedite on 2008-01-12
thanks for saying that DoktorSeven.  you have no idea how many times i said that very thing last year!  lol

i've filed a bug to get around having to compile the latest kxmame:
[https://bugs.launchpad.net/ubuntu/+source/kxmame/+bug/165044](https://bugs.launchpad.net/ubuntu/+source/kxmame/+bug/165044)

---

### Post by MaximB on 2008-01-13
> **disturbedite said:**
> thanks for saying that DoktorSeven.  you have no idea how many times i said that very thing last year!  lol

i've filed a bug to get around having to compile the latest kxmame:
[https://bugs.launchpad.net/ubuntu/+source/kxmame/+bug/165044](https://bugs.launchpad.net/ubuntu/+source/kxmame/+bug/165044)

That's a nasty bug indeed ;)
Make a .deb already :D

---

### Post by DoktorSeven on 2008-01-13
Okay, I have *attempted* to make a Debian package (the correct way, not checkinstall), but since this is my first time in doing so, it might take on a life of its own and destroy everything you know and love ;) or it might actually work -- or it might just do absolutely nothing.

Therefore, ***download and install at your own risk!***.  

It was built on Ubuntu 7.10 so I don't know if it will work on anything previous.  Works well here, but again, note the warning above.  I had to build it with --disable-joystick so there's no joystick support in the GUI for selecting games (which is separate from joysticks working in SDLmame, so don't fret -- if SDLmame works with joysticks, this won't affect that!).

[Download here](http://sdcofer.googlepages.com/home), and sorry if it doesn't work. [color=red]Updated:[/color] new download location.

---

### Post by disturbedite on 2008-01-13
> **DoktorSeven said:**
> Okay, I have *attempted* to make a Debian package (the correct way, not checkinstall), but since this is my first time in doing so, it might take on a life of its own and destroy everything you know and love ;) or it might actually work -- or it might just do absolutely nothing.

Therefore, ***download and install at your own risk!***.  

It was built on Ubuntu 7.10 so I don't know if it will work on anything previous.  Works well here, but again, note the warning above.  I had to build it with --disable-joystick so there's no joystick support in the GUI for selecting games (which is separate from joysticks working in SDLmame, so don't fret -- if SDLmame works with joysticks, this won't affect that!).

[Download here](http://doktorseven.miskie.net/files/kxmame_2.0svn-1_i386.deb), and sorry if it doesn't work.

it works great on kubuntu hardy!  THANK YOU SO MUCH!  i hadn't compiled it even tho i know how cuz i was trying to avoid having to compile anything...
everything works as expected for me.

---

### Post by disturbedite on 2008-01-17
now i'm experiencing a problem.  but i'm fairly sure its not your fault.  now whenever i start kxmame and get to the UI, xorg spikes to using nearly all of my CPU!  this happens in kde3 and kde4.  (i don't use gnome).

but strangely enough, it works fine in enlightenment...

---

### Post by DoktorSeven on 2008-01-17
Can't say that I've seen the same, though I use fluxbox.  Maybe something happening with KDE running.  Perhaps I'll try running KDE and see what happens.

Edit: I don't see any problems under KDE3 either (KDE4 gave me a headache trying to even run anything; I don't think they should have released it yet!).  The only time KDE is resource-intensive is when it's scanning your ROMs to see what's available (does it when it first starts or anytime you do File->Audit All Games to refresh the Available games list), and that brings up a special little window anyway...

---

### Post by disturbedite on 2008-01-17
no, its as soon as i click the icon in my menu.  before i ever run a game!

---

### Post by DoktorSeven on 2008-01-18
What happens (does it print anything?) when you run it from a terminal?

---

### Post by disturbedite on 2008-01-18
i haven't done that yet, i will report back on it later.

UPDATE:
well, i tried it again with the same result, but this time i did it from term.  nothing unusual to report tho.  something about kxmame (or perhaps sdlmame) really does like my CPU...
i'll try running sdlmame from term and see if there is a difference.

---

### Post by MaximB on 2008-01-20
I cannot get kxmame to work with sdlmame as a front GUI.
Do you ?

---

### Post by disturbedite on 2008-01-20
> **MaximB said:**
> I cannot get kxmame to work with sdlmame as a front GUI.
Do you ?
yes, it does work.  you must not have the correct packages installed.
(use the kxmame deb package posted in this thread, not the package from the ubuntu repo).

as for the problem i reported on earlier, the problem seems to have resolved itself, which leads me to believe it may have been a temporary fluke.

---

### Post by squidfaceExtreme on 2008-01-21
Is there a command line option for it? I don't understand... I installed the beta kxmame, but if I run kxmame in the command line it still tries to load xmame.

---

### Post by disturbedite on 2008-01-21
ok.
INSTALL THE KXMAME PACKAGE FROM THIS THREAD.
then
INSTALL THE SDLMAME PACKAGE FROM [HERE]("http://wallyweek.altervista.org/rel122.php").

---

