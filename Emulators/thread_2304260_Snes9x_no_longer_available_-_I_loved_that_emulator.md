---
title: "Snes9x no longer available - I loved that emulator!"
date: 2015-11-25
forum: Emulators
---

### Post by michael-piziak on 2015-11-25
Anyone know how I can get Snes9x again?
I know it had not been worked on in a long time, but it was still my favorite SNES emulator - and I've used them all.

The following 3 terminal commands can no longer find it:

[COLOR=#333333][FONT=Verdana]sudo add-apt-repository ppa:bearoso/ppa[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]sudo apt-get install snes9x-gtk[/FONT][/COLOR]

---

### Post by michael-piziak on 2015-11-25
I believe the user "adec2" has solved my problem by posting a link to Snes9x downloads in this thread:  [http://ubuntuforums.org/showthread.php?t=2296918](http://ubuntuforums.org/showthread.php?t=2296918)

I will have my desktop back up and running in a few days (faulty monitor being replaced asap).  Then I'll mark this thread as solved if it works out!

It's one of the main reasons I stick with Ubuntu 12.04 lts - just couldn't get it to work with 14.04 lts on 2 computers.

Thanks adec2 !

Michael

---

### Post by G_Muh on 2016-08-09
Next question: **why** is snes9x no longer available?

---

### Post by deadflowr on 2016-08-10
> **G_Muh said:**
> Next question: **why** is snes9x no longer available?

Ubuntu pulls a vast majority of the packages it uses from Debian.
If a package has no Debian developer or maintainer to help take care of it, it'll be dropped in Debian. And then it won't make it into the base of Ubuntu's packages that are pulled from Debian.
It can make it into the Ubuntu package base as a package not imported from Debian, but then someone from Ubuntu developers would have to take over the it's direct maintenance/packaging.
If the package does not get someone willing to take over it's maintenance/packaging then the package is dropped.

As such no Debian developer is willing to keep maintaining snes9x, and no Ubuntu developer is either.
So it has been removed.

Why does no one want to keep working on snes9x? 
Perhaps it is because the last version is 5 years old and a lot of changes have come to Ubuntu/Debian since then, making dealing with the older emulators code to work within Ubuntu/Debian's newer code a hassle.

---

### Post by adec2 on 2017-01-13
This is still updated quite regularly and is easy to compile for linux

[https://github.com/snes9xgit/snes9x](https://github.com/snes9xgit/snes9x)

---

