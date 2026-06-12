---
title: "Amazed-some games better under Ubuntu!"
date: 2006-11-26
forum: Gaming &amp; Leisure
---

### Post by kvonb on 2006-11-26
I've been playing an old copy of Unreal.  I tried it under XP and also using WINE in Edgy.

It actually runs smoother, faster, and with better graphics* than XP!

*apart from the shadow overlay which for some reason isn't transparent!

Also the old DOS games I have run perfectly under DosBox whereas XP won't even give them the time of day.

Very impressed :)

Have a look at this screenshot:

---

### Post by hikaricore on 2006-11-26
Not too suprising, system resource management and dos emulation in XP is aweful.  Microsoft hasn't bothered with decent dos emulation since about windows 2000.

---

### Post by po0f on 2006-11-26
kvonb,

Nice Dune II screenshot.  :)  How easy is it to install under DosBox?  I've never used it before.

---

### Post by leech on 2006-11-26
Oddly enough there are projects for native ports of all the games you mention (in your post and your screenshot.)

Unreal already has a native version, though you need unreal tournament.

Wolf3D is open sourced now and Dune 2 and Ultima Underworld both have projects that try to make them run native, using the original data files.

Leech

---

### Post by hikaricore on 2006-11-26
> **leech said:**
> Oddly enough there are projects for native ports of all the games you mention (in your post and your screenshot.)

Unreal already has a native version, though you need unreal tournament.

Wolf3D is open sourced now and Dune 2 and Ultima Underworld both have projects that try to make them run native, using the original data files.

Leech

I've yet to find any wolf3d versions that will compile for me :(

(tried 4 or 5 different projects on 4 different systems: dapper, edgy, kubuntu (dapper), and xubuntu (dapper))

someone should make a deb archive for wolf3d :)  *hint nudge hint*

---

### Post by kvonb on 2006-11-26
> Nice Dune II screenshot.  :smile:  How easy is it to install under DosBox?  I've never used it before.

Easy as!  Mine is just a directory copy I had as a backup, I just made a folder called dos-games, copied them all into there and in a terminal:

cd to the game folder, then: dosbox game.exe

The best thing to do is write a config file, I think it's:

dosbox config -writeconf (check the manual)

Then edit the file and in the autoexec section at the end, put your mount stuff (see the attached archive which contains dosbox.conf and a simple shell script to launch it).

For free games, see these places:

[http://www.freeoldies.com](http://www.freeoldies.com)
[http://www.classicpcgames.com](http://www.classicpcgames.com)
[http://www.abandonia.com](http://www.abandonia.com)

If you have any "special" questions you can always PM me ;)

Regards, Kev :)

---

### Post by zgornel on 2006-11-26
Yeah, that dune 2 screenshot really brought up memories...

---

### Post by leech on 2006-11-27
> **hikaricore said:**
> I've yet to find any wolf3d versions that will compile for me :(

(tried 4 or 5 different projects on 4 different systems: dapper, edgy, kubuntu (dapper), and xubuntu (dapper))

someone should make a deb archive for wolf3d :)  *hint nudge hint*

Got to love apt-get.org.  Too bad Ubuntu doesn't have something like it quite yet.

Please note, these packages are made for Debian, but I just installed the wolf3d ones and they work fine.

deb [http://home.icequake.net/~nemesis/debian](http://home.icequake.net/~nemesis/debian) binary/
deb-src [http://home.icequake.net/~nemesis/debian](http://home.icequake.net/~nemesis/debian) source/ 

That repository has lots of games actually, bit it is rather slow.

Leech

---

### Post by hikaricore on 2006-11-28
> **leech said:**
> Got to love apt-get.org.  Too bad Ubuntu doesn't have something like it quite yet.

Please note, these packages are made for Debian, but I just installed the wolf3d ones and they work fine.

deb [http://home.icequake.net/~nemesis/debian](http://home.icequake.net/~nemesis/debian) binary/
deb-src [http://home.icequake.net/~nemesis/debian](http://home.icequake.net/~nemesis/debian) source/ 

That repository has lots of games actually, bit it is rather slow.

Leech

Yea ubuntu's archives are a bit slow on getting wolf3d... considering there's 8 different versions of doom availible.  lol.

I'll check it out thank much :)

---

### Post by leech on 2006-11-28
No problem.  The packages are over a year old, but still work even under Edgy Eft.  

Other games I'd love to see in the Ubuntu repositories, though I don't think they will be due to licensing issues, are xu4 (Ultima 4 recreation for native Linux), Dungeon Master (again, someone ported this to Linux), gens (Genesis emulator, which has a package in the repositories that I posted and also a newer package in these very forums).

Leech

P.S.  This is my 1700th post, which means either I am a very helpful person for Ubuntu Linux and Canonical should give me a job, or I just really have no life but Ubuntu and they should give me a job :D

---

### Post by edemark on 2006-11-28
Hi i just would like to share my experience with dosbox.
GOOOD
I would also like to suggest anyone interested in using dosbox to try out dos box game launcher that can be found here [http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/](http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/)
it is really easy to and set up is made for every game separately. really you only need java to be able to use it

good luck

---

