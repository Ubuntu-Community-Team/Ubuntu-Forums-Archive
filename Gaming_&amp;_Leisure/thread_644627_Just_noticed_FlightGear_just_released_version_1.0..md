---
title: "Just noticed FlightGear just released version 1.0.0, do you think it's any good."
date: 2007-12-19
forum: Gaming &amp; Leisure
---

### Post by feisty_hot_lover on 2007-12-19
I see that the FlightGear people have just released version 1.0.0.  Has anybody tried the new version out.  Are there any deb files available yet?  How does the new version 1.0.0  compare with 0.9.10.

---

### Post by FokkerCharlie on 2008-01-07
I haven't tried it out myself yet, but it does seem that there are debs out on the fg website.

I'm an Ubuntu novice, however, and haven't downloaded an installer because of the warnings about using apt or synaptic instead.

Can you point me in the right direction?

---

### Post by Sockerdrickan on 2008-01-07
I didn't notice any graphical improvements. However flying helicopter was fun and not as hard as everyone says (especially with a mouse) *brag brag*

---

### Post by Vadi on 2008-01-07
I've filed a repot on getdeb.net, they should be out with a version soon.

I couldn't use the debian .deb from the flightgear site, complained about libc6..

---

### Post by FokkerCharlie on 2008-01-07
I have just tried installing with the deb, same result:

Error:  Dependency is not satisfiable: libc6.

Synaptic tells me that it is installed!

Maybe I'll just hang on until it appears in the repos.

Charlie

---

### Post by feisty_hot_lover on 2008-01-08
> **FokkerCharlie said:**
> I have just tried installing with the deb, same result:

Error:  Dependency is not satisfiable: libc6.

Synaptic tells me that it is installed!

Maybe I'll just hang on until it appears in the repos.

CharlieI'm going to wait until Hardy as thats only a few months away.  I tried in Windows and it's good.

---

### Post by Sockerdrickan on 2008-01-08
I'd suggest you all to learn how to compile instead of waiting on other people doing it for you. It's not hard at all.

---

### Post by FokkerCharlie on 2008-01-10
> **Tux0r said:**
> I'd suggest you all to learn how to compile instead of waiting on other people doing it for you. It's not hard at all.

I'm sure that it's not hard.  However, for novice Linux users like me, learning how to compile a large, complicated package, with lots of dependencies, such as flightgear might not be the cleverest place to start.

In fact there's a decent chance that a good proportion of those of us who attempt it would end up here within a few minutes asking for help with un-doing what we have been failing to do!

Rgds
Charlie

---

### Post by Vadi on 2008-01-10
I agree with you. "It's not hard at all" if you know exactly what you're doing. Then, it's not hard!

I'm waiting on the getdeb.net package.

---

### Post by FokkerCharlie on 2008-01-18
No getdeb.net package out yet.  :(

Anyone have an alternative solution?

---

### Post by Vadi on 2008-01-18
Hrm.. I just searched getdeb's launchpad, and the bug report wasn't there. I suspect I closed the browser or something before it managed to go through..

So, I reported it again here: [https://bugs.launchpad.net/getdeb.net/+bug/184013](https://bugs.launchpad.net/getdeb.net/+bug/184013)

Please reset that timer!

---

### Post by Sockerdrickan on 2008-01-18
How is that a bug?

---

### Post by Vadi on 2008-01-18
It's a "create package" type of a bug.

---

### Post by EXCiD3 on 2008-01-18
Has anyone tried installing FlightGear from the debian packages? [http://packages.debian.org/sid/flightgear](http://packages.debian.org/sid/flightgear)

---

### Post by Vadi on 2008-01-18
Yes, they don't work.

---

### Post by EXCiD3 on 2008-01-18
Just wondered, thought there might be a chance...i'd like to try this out myself, however i dont really want to have to compile it either. What about using alien on rpm's?

---

### Post by verb3k on 2008-01-18
Guys it's easy to compile it yourselves....
I didn't fownload the source and don't know if there is a special way to compile it, but I think the usual way of compiling should be:

1-  Enter:
```
sudo apt-get build-dep flightgear
```
this will get you all the dependencies needed to compile the game.

2-  Go in the source directory and enter:
```
./configure
```

3-  Enter:
```
make
```
to compile the game

4-  Enter:
```
sudo make install
```
to install the game.
[SIZE="4"][COLOR="Red"]
WARNING: I don't know if this way will work with FlightGear, it's just the "usual" or "standard" way of compiling programs on ubuntu, FlightGear may require a different way of compiling, so you must consult the flightgear documentation first.[/COLOR][/SIZE]

---

### Post by Vadi on 2008-01-18
I don't like compiling because I can't use synaptic to remove apps then. And it gets messy after I delete the original folder or something.

---

### Post by Lord Illidan on 2008-01-18
Use checkinstall to create debs of your compiled code. Honestly guys, do some work for yourselves..

---

### Post by xtang on 2008-01-18
I think you also have to compile and install SimGear if you want to compile FlightGear. 

Its very impressive but then again this is the first time I have ever played a flight simulator before so I can't really compare it to anything. Maybe it could be due to my settings but I was a bit unimpressed with the graphics, those screenshots on the website look much nicer. Anyway, its still a great piece of work.

---

### Post by Vadi on 2008-01-18
Hrm, yes. It looks like getdeb can't make the flightgear package because the simgear one in gutsy is *way* too old.

---

### Post by FokkerCharlie on 2008-01-21
OK- I've managed to compite FG 1.0.0.

I had to do quite a lot of fiddling about, but here is what I remember what worked:

Install Simgear with the instructions from this thread:
[http://ubuntuforums.org/showthread.php?t=647518](http://ubuntuforums.org/showthread.php?t=647518)
ensuring that you have the dependencies listed.  When I compiled, there was something else that it asked for, but I found it in synaptic, so it's OK.

Then it's time to download the flightgear source, from the flightgear.org website.
Download it to a folder, mine is in usr/share/games/FlightGear. No idea if that's right, but it seems to work for me.

Now, here's the interesting bit.  Normally, FG uses FreeGlut.  Ubuntu comes with this, and indeed the desktop seems to depend on it.  Unfortunately, the latest version (2.4, which is shipped with Ubuntu) has a bug which crashes FG.  Apparently, it's possible to downgrade to ver 2.2, or get a new (CVS) version, but I didn't fancy messing about with something that looked really important.

So the workaround is to do this:
./configure --enable-sdl

I think that it asked for an extra dependency here, something to do with SDL.  If it did, it was in synaptic!

I couldn't get checkinstall to work on this bit, either, so had to just make install.

The final piece of the puzzle is the base package.  See the flightgear website again, and install it using ./configure, make, install to the folder I mention above.

You will probably want FGRUN, too- try as detailed on the thread mentioned above.

I know it's pretty vague, but I hope it helps a little.

Cheers
Charlie

---

### Post by snickers295 on 2008-03-16
this thread looks dead but if i found it on google then others will too.
getdeb.net does have a flightgear 1.0.0 deb now.

---

### Post by von Stalhein on 2008-04-02
Well, I just found it, and I then checked Synaptic and found it's in the package manager at version 0.9.102Ubuntu2

Knowing that there was a newer version out, I went to [http://packages.debian.org/sid/i386/flightgear/download](http://packages.debian.org/sid/i386/flightgear/download) to get it. Noticing the instructions about adding it to the package manager, I had a crack.

Below is what I put into sources.list.

```
# FlightGear open source flight simulator
deb http://ftp.au.debian.org/debian/pool/main/f/flightgear/
```

I keep getting an error message when I open Synaptic

```
E: Malformed line 46 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report. 
```

As a relative Ubuntu n00b, can someone tell me what's wrong in my syntax please?

thanks   :)

Anybody

---

