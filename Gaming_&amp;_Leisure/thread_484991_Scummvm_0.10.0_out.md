---
title: "Scummvm 0.10.0 out"
date: 2007-06-26
forum: Gaming &amp; Leisure
---

### Post by BoyOfDestiny on 2007-06-26
I don't think anyone posted this, so adventure gamers rejoice!

> 
    * Several new engines and thus new games supported:
          o Sierra AGI engine: Space Quest I & II, King's Quest I-III and many more, including a vast number of fan-made games,
          o Cinematique evo 1 engine: Future Wars,
          o GOB engine: Bargon Attack, Gobliins 2, Goblins 3, Ween: The Prophecy,
          o AGOS engine: Simon the Sorcerer's Puzzle Pack,
          o Parallaction engine: Nippon Safes Inc.,
          o Touche: The Adventures of the Fifth Musketeer engine. 
    * DXA movies (higher quality than MPEG2) can be compressed better now and can be used for the Broken Sword cutscenes.
    * Added 'Mass Add' feature to the Launcher, which allows you to scan for all games in all subdirectories of a given directory (to use it, press shift then click on "Add Game").
    * Many nice improvements to our ports.
    * And as usual a gazillion small fixes, tweaks and improvements. 


[www.scummvm.org](www.scummvm.org)

Screenshot below, running good old King's Quest III (just like old times, except no floppy swapping, and the PC Speaker sound is "simulated", and well using hq3x filtering... ;) )

---

### Post by hikaricore on 2007-06-26
gawd I hated floppy swapping...

---

### Post by lingnoi on 2007-06-26
GetDeb already [has the deb files]("http://www.getdeb.net/app.php?name=ScummVM") you need to install it.

---

### Post by BoyOfDestiny on 2007-06-26
> **hikaricore said:**
> gawd I hated floppy swapping...

Memories. :)

Please insert Disk 2 of 5, and press enter.
*drive makes noise* and hopefully continues.

The number one worst annoyance IMHO was the 640k conventional memory limitation. Playing with himem and all that stuff. That and toying with irq, dma, etc. coming a close second for me.

When I hear people say oh it's better to get an old box to run DOS games... I wonder if they ever owned one. Let's not get started on timing issues either, at least PC's had that "turbo" button for a while to slow things down...

Either way, I'm glad the games didn't disappear, and can be run with less hassle and/or extra features now.

---

### Post by hikaricore on 2007-06-26
> **BoyOfDestiny said:**
> Memories. :)
The number one worst annoyance IMHO was the 640k conventional memory limitation. Playing with himem and all that stuff. That and toying with irq, dma, etc. coming a close second for me.

When I hear people say oh it's better to get an old box to run DOS games... I wonder if they ever owned one. Let's not get started on timing issues either, at least PC's had that "turbo" button for a while to slow things down...


Ugghhh..... that first part reminds me of trying to get The 7th Guest to run on my old 386sx.  That was a nightmare.  >.<

And for some reason my step father always liked to have that turbo button pressed even though he had no idea what it did... lol

---

### Post by i23098 on 2007-09-04
> **lingnoi said:**
> GetDeb already [has the deb files]("http://www.getdeb.net/app.php?name=ScummVM") you need to install it.

Any change this gets to gutsy repositories? [-o<

---

### Post by rhombus on 2007-12-13
> **i23098 said:**
> Any change this gets to gutsy repositories? [-o<

Agreed.

---

### Post by hikaricore on 2007-12-13
With Gutsy already being released a while back there is next to no chance that this version will end up in the repos unless the last release has a serious bug or poses security risk.

---

### Post by Vadi on 2007-12-13
I always pressed the turbo button.

---

### Post by rhombus on 2007-12-17
> **hikaricore said:**
> With Gutsy already being released a while back there is next to no chance that this version will end up in the repos unless the last release has a serious bug or poses security risk.


Here's how to easily install scummvm 0.10.0 in Gutsy (for us noobs).

I had tried getting the .deb file from [www.getdeb.net](www.getdeb.net) (I forgot, you have to change your version to Feisty on get deb for this to work [http://www.getdeb.net/distro_select.php](http://www.getdeb.net/distro_select.php) . Alternately, I'm guessing the Debian Etch .deb on scummvm's site would probably work but I haven't tried it) but it gave me an error saying that "Dependancy is not satisfiable: libflac7." Evidently, it depends on libflac 7 and won't work with the libflac8 that ships with Gutsy. Rather than building it from source (I'm kind of a noob and this just seems like a pain in the ***), I went here [http://packages.debian.org/stable/libs/libflac7](http://packages.debian.org/stable/libs/libflac7) (Debian Etch libraries), chose my architecture, downloaded and installed libflac 7 in deb format (so I have both 7 and 8 now). After that, the .deb file on getdeb.net installed without a hitch and scummvm plays great.

You would think that there would be a way to make dependencies not rely on an older version like that. Shouldn't a new version work?  If it doesn't, shouldn't someone figure out how to make that sort of thing work? Seems kind of weak that it looks for an older version and won't accept a newer one.

Anyway. Enjoy.

---

### Post by danramos on 2007-12-22
I got a bit impatient and just compiled my own Ubuntu Gutsy package.  It's the first time I generated a package, so be forewarned.. but it seems to work well with my laptop and my mom's laptop.

[http://pleco.org/gutsy/scummvm_0.10.0-1_i386.deb](http://pleco.org/gutsy/scummvm_0.10.0-1_i386.deb)

---

### Post by danramos on 2007-12-22
I forgot to point out that this package was compiled for Gutsy--so I none of that flac library nonesense.

---

### Post by leech on 2007-12-22
> **BoyOfDestiny said:**
> Memories. :)

Please insert Disk 2 of 5, and press enter.
*drive makes noise* and hopefully continues.

The number one worst annoyance IMHO was the 640k conventional memory limitation. Playing with himem and all that stuff. That and toying with irq, dma, etc. coming a close second for me.

When I hear people say oh it's better to get an old box to run DOS games... I wonder if they ever owned one. Let's not get started on timing issues either, at least PC's had that "turbo" button for a while to slow things down...

Either way, I'm glad the games didn't disappear, and can be run with less hassle and/or extra features now.

Those were good times..... Mainly because I had an Atari Mega STe, where I didn't have to worry about all that crap.  :D  To this day, I still have a hard time understanding how DOS (and then Windows) came to be the most used Operating System.  Compared to using an Amiga, Atari ST or Macintosh, they were a nightmare until the Windows 9x days.  Even then they were unstable and you still occasionally had to deal with the dma / irq issues.  Especially when it came to those crappy sound card / modem combination ISA cards.  God, those sucked!  Stupid Packard Bells!

To be more on Topic.  This is great news.  I love ScummVM and I always wondered why they hadn't merged the other projects for the AGI games.

Leech

---

### Post by squell on 2008-01-16
ScummVM 0.11.0 is now out

How do we get this into the Hardy repositories?

---

### Post by Perfect Storm on 2008-01-16
Send a bug/request it to the Ubuntu devs

---

### Post by Perfect Storm on 2008-01-16
Here's a guide howto compile and install ScummVM latest for 64bit: [http://gaming.gwos.org/doku.php/guides:64bit](http://gaming.gwos.org/doku.php/guides:64bit)
Just remember to uninstall previous version first.

---

