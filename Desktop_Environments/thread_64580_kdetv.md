---
title: "kdetv"
date: 2005-09-11
forum: Desktop Environments
---

### Post by dc2447 on 2005-09-11
Anybody advise of a repository for getting[ kdetv](http://www.kdetv.org/) please?

---

### Post by Altmenorg on 2005-09-12
Is it a joke ?
Did you really look into the official website you're giving the link ?

---

### Post by dc2447 on 2005-09-12
[QUOTE=Altmenorg]Is it a joke ?
Did you really look into the official website you're giving the link ?[/QUOTE]

I need a repository not source - but cheers for being an arse - it suits you

---

### Post by mlomker on 2005-09-12
The have repositories listed on their website for debian:  [http://www.kdetv.org/download.html](http://www.kdetv.org/download.html) 

Just be careful that it doesn't try to install additional packages that might overwrite other things...

---

### Post by dc2447 on 2005-09-12
[QUOTE=mlomker]The have repositories listed on their website for debian:  [http://www.kdetv.org/download.html](http://www.kdetv.org/download.html) 

Just be careful that it doesn't try to install additional packages that might overwrite other things...[/QUOTE]Don't work for me - 404

---

### Post by rcerreto on 2005-09-12
You can get version 0.8.8-1 from the following repository:

deb [http://bonca.hu/~rizsany/debian/](http://bonca.hu/~rizsany/debian/) sarge/

it's an unknown source though.
Your choice!!   8)

---

### Post by dc2447 on 2005-09-12
[QUOTE=rcerreto]You can get version 0.8.8-1 from the following repository:

deb [http://bonca.hu/~rizsany/debian/](http://bonca.hu/~rizsany/debian/) sarge/

it's an unknown source though.
Your choice!!   8)[/QUOTE]

That 404's for me

---

### Post by skyboy on 2005-09-13
Why dont you try compiling it ?? it took me few minutes :S and dont need to freek out about where it is coming from nor if it is debian and not ubuntu .... it just work

I forgot, sure you will have to install few library but not a hard work, just ask if you have trouble compiling it.

---

### Post by dc2447 on 2005-09-13
[QUOTE=skyboy]Why dont you try compiling it ?? it took me few minutes :S and dont need to freek out about where it is coming from nor if it is debian and not ubuntu .... it just work

I forgot, sure you will have to install few library but not a hard work, just ask if you have trouble compiling it.[/QUOTE] You are missing the point - I want to install it using apt - as this is how I manage my packages on my workstation.

If I wanted to compile every package by hand I'd use BSD

---

### Post by Thulemanden on 2005-09-13
[QUOTE=mlomker]The have repositories listed on their website for debian:  [http://www.kdetv.org/download.html](http://www.kdetv.org/download.html) 
[/QUOTE]

Broken dependencies etc.

---

### Post by skyboy on 2005-09-13
I think you are missing the point. Not every application is ported to every OS so if you want something in particular, do it yourself. And a bit of "relax pal" and politness would not kill you either.

cheers

---

### Post by dc2447 on 2005-09-13
[QUOTE=skyboy]I think you are missing the point. Not every application is ported to every OS so if you want something in particular, do it yourself. And a bit of "relax pal" and politness would not kill you either.

cheers[/QUOTE]  I'm not missing the point at all. I asked if there was repositories for the application as I want to control packages via apt.

If I wanted to compile by hand then that is what I would do.

---

### Post by mlomker on 2005-09-13
[QUOTE=dc2447]If I wanted to compile every package by hand I'd use BSD[/QUOTE]

Then why don't you use checkinstall or read the how-to's on how to build a package?  I think you're being pretty rude to people that aren't being paid to help you.

---

### Post by dc2447 on 2005-09-14
[QUOTE=mlomker]Then why don't you use checkinstall or read the how-to's on how to build a package?  I think you're being pretty rude to people that aren't being paid to help you.[/QUOTE]

With respect, I don't believe I am being rude.  I don't believe pointing me to building from source is actually helping anyone, I was and concise in all my posts.  Compiling from source is very easy but is isn't something I want to do; I want to use apt to manage my packages  so that I do not have to worry about dependancies, upgrades and the like.

---

### Post by Potemkin on 2005-09-14
Checkinstall creates and installs a Debian package from the source code. It then shows up in apt and in Synaptic, so that you can easily manage it. What's wrong with that?

---

