---
title: "Does anybody know any good mame frontend that works with sdlmame?"
date: 2008-10-25
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2008-10-25
As the title says, also it needs to work with 64bit architecture since most of them don't, also it needs to have detailed options for video and sound and such things. I tried compiling kxmame (the version that supports sdlmame) but for the life of me I can't (I was never able to compile anything) and I've been on countless forums and posting my errors and either nobody replies or they give me solutions that never work in my case.

I'm using Kubuntu 8.10 Intrepid Ibex release candidate (I also tried compiling with older versions of that matters at all) with KDE 4.1.2 with all updates.

---

### Post by markinf on 2008-10-25
I use QMC2, it's serves me a lot because it's has a beautiful and very intuitive interface. And it's allways updated with sdlmame. So you won't worry to use old features of sdlmame in the front-end.

I'm using Ubuntu 8.04.1 64bit and the negative points of QMC2 are: 

* Is on Qt, so you'll like it :) (I preffer GTK+)
* And you have to compile, but don't worry they have an excellent tutorial in their site there teaching how to compile and install the dependency's.

QMC2
[http://www.mameworld.net/mamecat/](http://www.mameworld.net/mamecat/)

---

### Post by FranMichaels on 2008-10-25
That's odd that nothing compiles, you've installed build-essential?

Anyway, with this mamepgui, did you right click the binary, Properties and click allow executing. 
It's a feature in nautilus, so I don't know the Kubuntu equivalent.

You could run something like 
```
chmod 777 mamepgui
```
To make it executable.

P.S. My dream front-end would include the following
* Be open source
* Be GTK (would be nice)
* Support roms in sub-directories
* Allowed to specify a directory as a "system"
* Take strings for custom launcher commands on said systems, with an option to list/index recognized file types per system (i.e. in my dos folder, only show .exe, .com, and .bat.
* Allow sub folder to be qualified as genre or region in filtering (i.e. Folder called Japan, or Platform Shooter)
* make searching simple (i.e. list below games that match, let's say I enter final,
list final fight, final fantasy, so on and so forth, so one can just click it.
* not choke on 60,000+ files.
* Some sort of artwork based on filename thing would be nice too.
* Also gives the option to kill compiz on game launch, then restore it.

I whipped up a tiny script for doing most of that, except not real indexing. Just put in a few terms and it uses the locate command. The system per directory is hard coded. It's not a true front-end though. But it works if you know what you want to play... No graphics preview no "going back" have to click cancel and launch it again...

---

### Post by Moonfrost on 2008-10-25
> **markinf said:**
> I use QMC2, it's serves me a lot because it's has a beautiful and very intuitive interface. And it's allways updated with sdlmame. So you won't worry to use old features of sdlmame in the front-end.

I'm using Ubuntu 8.04.1 64bit and the negative points of QMC2 are: 

* Is on Qt, so you'll like it :) (I preffer GTK+)
* And you have to compile, but don't worry they have an excellent tutorial in their site there teaching how to compile and install the dependency's.

QMC2
[http://www.mameworld.net/mamecat/](http://www.mameworld.net/mamecat/)

What's the big difference between Qt and GTK+ anyway? I mean, performance-wise they both seem really good, I've ran Qt programs (KDE programs) on Gnome and I've ran GTK+ programs on KDE before and no big difference if they are not running on their native desktop enviroment.

---

### Post by Moonfrost on 2008-10-26
I'm trying to compile QMC2 but I get an error:

```
moonfrost@moonfrost-PC:~/Desktop/qmc2$ make
/bin/sh: /bin/qmake: not found
Error: Wrong QMake version. QMake version 2 (Qt 4) required!
```

The thing is I have Qt4 development tools, is qmake-Qt4 not included in that package?

---

### Post by disturbedite on 2008-10-26
> **Moonfrost said:**
> As the title says, also it needs to work with 64bit architecture since most of them don't, also it needs to have detailed options for video and sound and such things. I tried compiling kxmame (the version that supports sdlmame) but for the life of me I can't (I was never able to compile anything) and I've been on countless forums and posting my errors and either nobody replies or they give me solutions that never work in my case.

I'm using Kubuntu 8.10 Intrepid Ibex release candidate (I also tried compiling with older versions of that matters at all) with KDE 4.1.2 with all updates.

no need to compile it: doktorseven made a deb package of it a long time ago. last time i checked it was still available at his site.

---

### Post by Moonfrost on 2008-10-26
> **disturbedite said:**
> no need to compile it: doktorseven made a deb package of it a long time ago. last time i checked it was still available at his site.

kxmame? I downloaded it but it's for 32bit only.

---

### Post by disturbedite on 2008-10-26
> **Moonfrost said:**
> kxmame? I downloaded it but it's for 32bit only.
yeah i know. just force the architecture.

---

### Post by Moonfrost on 2008-10-26
> **disturbedite said:**
> yeah i know. just force the architecture.

How do I do that? I knew I could do it but don't know how.

EDIT: Never mind, tried it but it still gives me errors saying that there was a problem forcing the architecture, then it says it installed but when I try to start it gives me some weird errors and a missing library which is not on the repos.

---

### Post by Moonfrost on 2008-10-26
> **markinf said:**
> I use QMC2, it's serves me a lot because it's has a beautiful and very intuitive interface. And it's allways updated with sdlmame. So you won't worry to use old features of sdlmame in the front-end.

I'm using Ubuntu 8.04.1 64bit and the negative points of QMC2 are: 

* Is on Qt, so you'll like it :) (I preffer GTK+)
* And you have to compile, but don't worry they have an excellent tutorial in their site there teaching how to compile and install the dependency's.

QMC2
[http://www.mameworld.net/mamecat/](http://www.mameworld.net/mamecat/)

How did you compile it? it asks me for Qt 4 which I have, and it says I have the wrong version of qmake even though I already installed the Qt4 development packages. Maybe qmake=qt4 is not included in that package? do you know where I could get it? the Ubuntu repos don't have it.

---

### Post by JMac82 on 2009-07-30
did you ever get an answer to this?  I can at least share what happened with me - I had the same problem with the 32-bit deb package not working on 64-bit once installed with --force-architecture (needing some library I couldn't find). Then I compiled the svn 2.0-beta-2 kxmake version on 64-bit ubuntu...did ./configure, which worked after installing a few libraries i didn't have.  then tried to make and I noticed the configure script made an empty make-file.  I gave up after that.

---

### Post by disturbedite on 2009-07-30
my revised recommendations are QMC2 or MAME Executor.

---

### Post by wingnux on 2009-07-31
QMC2 requires qt4.5 and the latest version on the repositories is 4.4 =/

---

### Post by mocha on 2009-08-02
Maybe it's just my system, but the only way I could ever get QMC2 to compile on Ubuntu is to go in the /qmc2/arch/ directory and change the file Linux.cfg to look like this:

```
QMAKE    = /usr/bin/qmake-qt4
LUPDATE  = /usr/bin/lupdate-qt4
LRELEASE = /usr/bin/lrelease-qt4
OSNAME   = Linux
SED      = sed -r
```

---

