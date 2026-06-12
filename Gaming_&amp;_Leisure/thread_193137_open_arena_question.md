---
title: "open arena question"
date: 2006-06-09
forum: Gaming &amp; Leisure
---

### Post by cowley on 2006-06-09
hi, im not a gamer by heart but thought id have a go wih open arena.  i have installed and it works but im a bit bored of not having anything to kill.  how do i join other players or at least set it so i have something to shoot at!

thanks

simon

---

### Post by cowley on 2006-06-10
anyone?

---

### Post by dmn_clown on 2006-12-12
You update to the latest version and enjoy the bot frag fest and ignore the fact that this forum is biased against games released under the GPL, some people care about freedom and understand that community driven software can be improved with that freedom and others do not. ](*,)

---

### Post by lamego on 2006-12-12
You can get the latest version here:
[http://www.getdeb.net/app.php?name=openarena](http://www.getdeb.net/app.php?name=openarena)

---

### Post by dmn_clown on 2006-12-12
Why is it only packaged for x86?  The engine builds on amd64, ppc, and alpha (cross compile!!!).

---

### Post by lamego on 2006-12-12
Because I don't have the time and resources to build to all those archs, yet :)

---

### Post by dmn_clown on 2006-12-13
You should also consider modularization, split the game engine out from the game data and package both separately. That would allow the packaging of all the arches separately without cluttering the repo with multiple versions of the game data.

Check out the [Debian Games Project]("http://wiki.debian.org/Games/Development") and see how they did it if you need ideas.

---

### Post by lamego on 2006-12-13
Splitting data from code makes senses for apt repositories, the idea behind GetDeb is to package whenever possible into a single .deb to make the installation easier for the users.

---

### Post by Lord Illidan on 2006-12-13
> **dmn_clown said:**
> You update to the latest version and enjoy the bot frag fest and ignore the fact that this forum is biased against games released under the GPL, some people care about freedom and understand that community driven software can be improved with that freedom and others do not. ](*,)

Why are we biased against games released under the GPL? I see a lot of fans for Wesnoth, Warsow, and Tremulous here, all GPL games.

Just because I like NVIDIA drivers doesn't mean I am anti-GPL. Come to think of it, I cannot play Warsow nor Wesnoth under GPL drivers..

---

### Post by dmn_clown on 2006-12-13
> **lamego said:**
> Splitting data from code makes senses for apt repositories, the idea behind GetDeb is to package whenever possible into a single .deb to make the installation easier for the users.


On the Contrary, it makes perfect sense to split the Game Data off from the engine, without doing so you end up with 3 huge 80 meg debs, one for each arch that Ubuntu supports when you only really need to package the game data once for all archs, at the same time packaging the engine individually for each seperate arch.  You use a meta package to pull not only the game data but the engine for the required architecture.  Doing the above will save ~145 megs of server space and the meta package keeps it easy for the end user.

---

### Post by lamego on 2006-12-16
> On the Contrary, it makes perfect sense to split the Game Data off from the engine, without doing so you end up with 3 huge 80 meg debs, one for each arch that Ubuntu supports when you only really need to package the game data once for all archs, at the same time packaging the engine individually for each seperate arch. You use a meta package to pull not only the game data but the engine for the required architecture. Doing the above will save ~145 megs of server space and the meta package keeps it easy for the end user.
If you are using a dependency capable system like APT yes that makes sense, if your goal is to provide a single click standalone package it does not make sense, disk space on a server is not that much a concern nowadays ;)
It is far more complex to properly manage dependencies for several packages unless you have a numerous and skilled team mananing it...

---

### Post by Gargamella on 2006-12-29
I downloaded now the 0.60 version that should be a stand alone game...

but how do i run it?

---

### Post by leilei on 2006-12-29
just type ./ioquake3.i386

---

### Post by rajeev1204 on 2006-12-30
hi

i am running a 64 bit OS too. 

I am also trying to get openarena installed

i managed to do a force install of this . but it needs openal 32 bit libs which i somehow managed to install . so now i have a new error

cant find libvorbisfile.so.3 . Now why do i need vorbis for this?

i cant do a 32 bit vorbis install cos it will mess up my system

Is it possible to bypass the vorbis check when running the game? I am desparate to get this up and running.


regards

rajeev

---

### Post by Gargamella on 2006-12-30
> **leilei said:**
> just type ./ioquake3.i386

$ ./ioquake3.i386
./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot op en shared object file: No such file or directory

any idea?

---

### Post by MadMan2k on 2006-12-30
go into your open arena directory and type "cat LINUXNOTES".

---

### Post by Gargamella on 2006-12-30
$ cat LINUXNOTES
if it doesn't start up at all, you may need libopenal installed.

---

### Post by Gargamella on 2006-12-30
ok now works...I downloaded libopenal0  from synaptic

---

### Post by MadMan2k on 2006-12-30
;)

---

### Post by rajeev1204 on 2006-12-30
hi

I solved my 64 bit problem

i downloaded the installer from [www.ioquake3.com](www.ioquake3.com) which has a common installer for all versions.

then i copied the openarena pak files into the baseq3 folder and voila


It runs great .

Because openarena is based on ioquake3 engine we can run it 



haha nice

---

### Post by rajeev1204 on 2006-12-30
hi

For all those who need openarena on 64 bit , download the tarball from [www.openarena.ws](www.openarena.ws) .This has the installer for 64 bit as well

---

### Post by leilei on 2006-12-31
Or you can head to the [svn](http://openarena.ws/svn/bin/).

(I'm lazy so I stick binaries in there)

---

### Post by rajeev1204 on 2006-12-31
hi

i am grateful to all those responsible behind the open arena project/

Is there any new maps i can download for this?


Anyway keep up the good work guys 

I was very keen to run quake 3 and u guys have made it possible.

Thanks a million


regards

rajeev

---

