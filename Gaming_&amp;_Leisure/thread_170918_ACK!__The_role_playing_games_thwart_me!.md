---
title: "ACK!  The role playing games thwart me!"
date: 2006-05-05
forum: Gaming &amp; Leisure
---

### Post by Mookawaka on 2006-05-05
In an effort to maximise my time wasting (and learn some more about Ubuntu along the way) I am attempting to install some games but I have had some difficulties along the way.

1) After downloading RPM packages for games such as xu4 and Lost Labyrinth I go through the Ubuntu guide instructions for converting them to .deb packages and proceed to install them.  I am then left with some folders that have documentation but no game/executable files that I can locate.  Am I missing a step in the installation?

2) Falcon's Eye, when installed through Synaptics, seems to work fine.  I start with some character creation menus, but when the dungeoneering is set to begin it crashes and leaves me with a blank window that cannot be closed short of rebooting.

3) I stumbled through the [How To guide]("http://www.ubuntuforums.org/showthread.php?t=157770") to install FreedroidRPG.  Though successful, the game is incredibly choppy, slow, and unresponsive.  I have my doubts this has to do with a lack of system resouces, but you never know (PIII 1.1 MH, 512 RAM, 16 meg video card.)

4) The Orcs in Wesnoth are very good at slaying my armies and demoralizing their leader.  I do not think I will ever make a good field general in a militaristic fantasy world.

---

### Post by Engnome on 2006-05-05
You mean .deb huh? Are you using alien to? It almost never work for me either:(  
To find your apps you may want to install debian menu, its in the repositories. Search for it in synaptic, its called just "menu" for some reason...

---

### Post by Mookawaka on 2006-05-05
I did indeed mean ".deb" . . . TYPO FIXED!

---

### Post by leech on 2006-05-05
Go to [http://debian.frodo.looijaard.name/](http://debian.frodo.looijaard.name/) for Debian packages of XU4.

Falcon's Eye works here.  I just tested it on my laptop, and while it's acting quite odd since I have XGL/Compiz running, it is working.  Just a bit too much transparency going on...

Haven't tried the other games yet.

Leech

---

### Post by Perfect Storm on 2006-05-05
If I'm not mistaken, there's a dynamic binary version of Lost labyrinth. Try that one.

---

### Post by mike998 on 2006-05-06
The FreeDroid one is a bit of an annoyance.
I have emailed the developers about my random crashes and have also sat in the IRC channel and asked questions.
Both times I have not got any response.

Pretty annoying...

---

### Post by charlieg on 2006-05-08
[QUOTE=Mookawaka]2) Falcon's Eye, when installed through Synaptics, seems to work fine.  I start with some character creation menus, but when the dungeoneering is set to begin it crashes and leaves me with a blank window that cannot be closed short of rebooting.[/quote]
Let's start with telling you that Falcon's Eye is not the most current version of that game!  It was forked into the Vulture's Eye/Claw project which has developed tremendously since then.  I too had the Falcon's Eye crashing problem but Vulture's works just fine for me.

I found the unix installer from here worked fine:
[http://www.darkarts.co.za/projects/vultures/downloads/](http://www.darkarts.co.za/projects/vultures/downloads/)

[QUOTE=Mookawaka]4) The Orcs in Wesnoth are very good at slaying my armies and demoralizing their leader.  I do not think I will ever make a good field general in a militaristic fantasy world.[/QUOTE]
Practise makes perfect, I'm afraid.  Just get used to consolodating your positions properly and letting their units come to you split up rather than taking them on all at once.  Killing isolated units is easy.  Just focus on getting the right position on the map and holding it - i.e. defend near or on houses and rotate your units around healing units.

---

### Post by Mookawaka on 2006-05-11
First off, thank you for the helpful responses from the experts.

Here is an update as to my efforts to install games outside of the Ubuntu repositories:

1)  I have given up on FreedroidRPG.  It was very exciting as the first tarball that I figured out how to compile (of course with the extensive How To guide by mike998 ), but the game was unplayable on my machine due to being incredibly slow and choppy.

2)  I have gotten Lost Labyrinth to work with the advice of Artificial Intelligence, even though I was ignorant as to the meaning of "a dynamic binary version."  JOY!

3)  I was aware of the newer Nethack version called Vulture's something or other, but thought that I would go the easy way and install the earlier Falcon's Eye through the repositories.  Of course it did not work out and now I get to learn how to use a Unix installer instead.  Help me CHARLIEG!  Which one should I use:  claw, eye, or full?  What do I do with it now that it is sitting on my desktop?

4)  There still exists some difficulties between myself and xu4.  This pains me as I am of the opinion that Ultima 4 is the best computer game ever and I would love to revisit it.  In my attempt to install the xu4 .deb I encounter an error demanding the ultima4 data package, leaving the package unconfigured.  Upon attempting to install the ultima4 data it demands configuration of xu4.  A vicious cycle indeed.  Does Leech (he of vast NWN installing knowledge . . .) know a way out of this loophole?

5)  The Orcs  of Wesnoth are quite stubborn.  They call me names, shoot poisoned arrows at my comrades, and refuse to accept my conquest of lands they have occupied.  Will we ever be able to find a diplomatic solution?

---

### Post by charlieg on 2006-05-12
Just go with Eye for the moment.  Claw has extra stuff, but KISS for now.  The full package simply contains both although I've never tried it so don't know how you activate either one.

There are two ways to install it.  Either use the unix installer or use alien and the rpm.

**The unix installer**

This simply tries to compile it for you.  It's really just a shortcut for downloading a tar.gz and running ./configure && make && make install.
```
$ chmod +x vultures_eye_file.sh
$ ./vultures_eye_file.sh
```
It will probably fail to compile first try due to unmet dependencies.  If it fails, you need the various relevant -dev packages (e.g. libsdl-dev).  The configure script should fail for each dependency so you should be able to easily find out each one.

**Alien and RPM**

Install alien if you haven't through synaptic.

Download the RPM from the [downloads](http://www.darkarts.co.za/projects/vultures/downloads/):
[http://www.darkarts.co.za/projects/vultures/downloads/2.0.0/RPM/nethack-vultures-2.0.0-5.fc3.i386.rpm](http://www.darkarts.co.za/projects/vultures/downloads/2.0.0/RPM/nethack-vultures-2.0.0-5.fc3.i386.rpm)
```
alien nethack-vultures-2.0.0-5.fc3.i386.rpm
```
That should give you a .deb to install - use dpkg -i to install it.

---

### Post by benplaut on 2006-05-12
i could've sworn i already posted in this thread...

get yourself a good n64 emulator and play zelda :D

---

