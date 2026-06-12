---
title: "KGoldRunner"
date: 2011-12-18
forum: Gaming &amp; Leisure
---

### Post by yoramdavid on 2011-12-18
hello all,

I installed kglodrunner on gnome desktop, it has sounds as .wav but when playing the game, they do not get reproduced.

Any idea why?

---

### Post by yoramdavid on 2011-12-22
Nobody plays that game?

---

### Post by Erik1984 on 2011-12-22
Just installed it from the software center and it plays sound after checking "Play Sounds" in the settings menu.

---

### Post by yoramdavid on 2011-12-22
> **Euroman said:**
> Just installed it from the software center and it plays sound after checking "Play Sounds" in the settings menu.

Thank you Euroman,

I do not have that option on the settings, when I start the game I get a message saying that "This copy of Kgoldrunner does not have sounds. This happens because there were not OpenAL e SndFile library versions available when it was compiled and created executable."

I am running Kgoldrunner 4.7 installed from the software centre.
Which version are you using?

Regards,

Yoram

---

### Post by yoramdavid on 2011-12-28
Please?

---

### Post by Erik1984 on 2011-12-29
I use the version from the Lucid repos, you seem to be on Oneiric Ocelot so that could explain the difference. It seems like a bug AFAIK software doesn't get compiled when you install from the Software Center. So compilation has already happened before packaging and installation and a mistake was made when compiling (not by you).

Possible solutions:
- Uninstall your version of KGoldrunner, find .deb file of older version and install that. You might try the lucid version. this seems to be the one I have: _[http://launchpadlibrarian.net/60768174/kgoldrunner_4.4.5-0ubuntu1_i386.deb](http://launchpadlibrarian.net/60768174/kgoldrunner_4.4.5-0ubuntu1_i386.deb)_ (that's the 32 bit version)
- Get the source and compile yourself with the proper libraries. Probably you need some *-dev packages.

---

### Post by yoramdavid on 2011-12-30
> **Euroman said:**
> I use the version from the Lucid repos, you seem to be on Oneiric Ocelot so that could explain the difference. It seems like a bug AFAIK software doesn't get compiled when you install from the Software Center. So compilation has already happened before packaging and installation and a mistake was made when compiling (not by you).

Possible solutions:
- Uninstall your version of KGoldrunner, find .deb file of older version and install that. You might try the lucid version. this seems to be the one I have: _[http://launchpadlibrarian.net/60768174/kgoldrunner_4.4.5-0ubuntu1_i386.deb](http://launchpadlibrarian.net/60768174/kgoldrunner_4.4.5-0ubuntu1_i386.deb)_ (that's the 32 bit version)
- Get the source and compile yourself with the proper libraries. Probably you need some *-dev packages.

Thank you Euroman

---

### Post by Erik1984 on 2011-12-31
Does it work now? If so could you mark the thread as solved?

---

### Post by yoramdavid on 2011-12-31
> **Euroman said:**
> Does it work now? If so could you mark the thread as solved?

No, it still does not work. Unfortunately.

I have problems compiling from the source (I have no experience with that, last time I tried with Rubrica2, it gave me errors. I confess I did not try with KGoldrunner) so I tried to find other .deb packages. I found 3 newer versions (64bit) :KGoldrunner4.7.2, KGoldrunner4.7.3 and KGoldrunner4.7.4 but they all have no sounds. :(

Regards,

Yoram

---

### Post by Arthur_D on 2011-12-31
I suggest contacting the developer. I did so quite a few years back, and got a nice answer which worked around the problem I had back then with the game.

Game devs are usually awesome people. :)

---

### Post by yoramdavid on 2012-01-01
> **Arthur_D said:**
> I suggest contacting the developer. I did so quite a few years back, and got a nice answer which worked around the problem I had back then with the game.

Game devs are usually awesome people. :)

Thank you Arthur_D,

I just did, hopefully I will receive an answer and who knows they compile it again and there will be an update soon?

Regards,
Happy  new year every body.

Yoram

---

