---
title: "Freeciv 2.0.0"
date: 2005-04-18
forum: Gaming &amp; Leisure
---

### Post by cannibalbob on 2005-04-18
[http://games.slashdot.org/games/05/04/18/0433230.shtml?tid=209&tid=117&tid=206&tid=10](http://games.slashdot.org/games/05/04/18/0433230.shtml?tid=209&tid=117&tid=206&tid=10)

how long until i can install it with synaptic?  :grin:

---

### Post by Burgundavia on 2005-04-18
In hoary? Not until someone backports it. In Breezy, it needs to hit Debian Sid first.

Corey

---

### Post by ubuntu UsER on 2005-04-18
You can compile it, it is really easy :-)

---

### Post by skoal on 2005-04-18
Anybody actually play the 2.0 version yet?  I love FreeCIV but went back to pre-2.0 release mainly because I can't move right/left/up/down anymore, only diagonals.  I've tried every different tileset too.  I don't know if it's a bug or a feature change.

---

### Post by MaX on 2005-04-19
[QUOTE=Burgundavia]In hoary? Not until someone backports it. In Breezy, it needs to hit Debian Sid first.

Corey[/QUOTE]
 Is it worth running breezy whats the difference from hoary??

Is hoary only bugfixes or is it only security fixes now?

---

### Post by jdodson on 2005-04-19
[QUOTE=MaX]Is it worth running breezy whats the difference from hoary??

Is hoary only bugfixes or is it only security fixes now?[/QUOTE]

hoary is a completly updated(featurewise and security/buxfix wise) ubuntu desktop.  new features include: xorg, gnome 2.10, kernel 2.6.10.5.

i would snag the source, and compile it.  the only dependicy i had to install was the gtk2-dev meta package.  after that it compiled fine.  then i made a .deb that installs like a charm.

---

### Post by ubuntu_demon on 2005-04-19
[QUOTE=MaX]Is it worth running breezy whats the difference from hoary??

Is hoary only bugfixes or is it only security fixes now?[/QUOTE]
 no it's not worth running breezy unless you understand the risk of breakage and don't use it for your main desktop

---

### Post by MaX on 2005-04-19
[QUOTE=demon666_nl]no it's not worth running breezy unless you understand the risk of breakage and don't use it for your main desktop[/QUOTE]
 Well I ran a fully bleeding edge Gentoo-system (breakmygentoo) and it worked OK, but that was when things happened in the gnome community (2.1-2.8) so I belive I know what breakage mean.. I tried to do an upgrade today but since they had a pretty severe evolution dependency bug I'll pass for now... when breezy is 2 months to be completed I'll take a look again.

---

### Post by ubuntu_demon on 2005-04-20
you can get the .tar.gz package here : [http://www.freeciv.org/index.php/Freeciv](http://www.freeciv.org/index.php/Freeciv)

Installing this package probably won't be very difficult.

In my case this are the last two lines I get when I do ./configure :
```

checking for gzgets in -lz... no
configure: error: Could not find zlib library.

```

Now I have to figure out which zlib library I have to install. (apt-cache search zlib gives a couple of results)

---

### Post by Happy on 2005-04-20
zlib1g-dev 
gtk2-engines-dev

these are the two packages I had to get via apt before ./configure gave no error messages.
now I am compiling it.
I'll report any additional errors


> 
happy@ubuntu:~$ civclient
2: No real audio plugin present, proceeding with sound support disabled
2: For sound support, install either esound or SDL_mixer
2: Esound: [http://www.tux.org/~ricdude/EsounD.html](http://www.tux.org/~ricdude/EsounD.html)
2: SDL_mixer: [http://www.libsdl.org/projects/SDL_mixer/index.html](http://www.libsdl.org/projects/SDL_mixer/index.html)

gah... which one do you reckon I should install?
Esound or SDL_mixer =)

but it does look nice
I'm a zulu

---

### Post by leech on 2005-04-20
The Freeciv 2.0.0 packages are in Debian experimental now.  You may be able to just install it through there.

Leech

---

### Post by jdodson on 2005-04-20
[QUOTE=leech]The Freeciv 2.0.0 packages are in Debian experimental now.  You may be able to just install it through there.

Leech[/QUOTE]

WARNING, WARNING!  Mixing package repositories is pretty though to do right.  I would urge anyone away from that as an option that is not a hefty debian guru.

---

### Post by ubuntu_demon on 2005-04-20
[QUOTE=Happy]zlib1g-dev 
gtk2-engines-dev

these are the two packages I had to get via apt before ./configure gave no error messages.
now I am compiling it.
I'll report any additional errors



gah... which one do you reckon I should install?
Esound or SDL_mixer =)

but it does look nice
I'm a zulu[/QUOTE]
 In my case these were the only ones too

---

### Post by ssam on 2005-04-20
its making its way into hoary backports

[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by MaX on 2005-04-21
[QUOTE=ssam]its making its way into hoary backports

[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)[/QUOTE]
 it is?? where do you see that?
We're all dreaming right now... heck the backports server doesn't work.

---

### Post by DJ_Max on 2005-04-24
I've never played the game, but heard of it. I'm compiling it right now, I'll let you know what it's like.

---

### Post by ubuntu_demon on 2005-04-24
[QUOTE=DJ_Max]I've never played the game, but heard of it. I'm compiling it right now, I'll let you know what it's like.[/QUOTE]
 i really like it !
I'm playing it right now with a friend of mine.

---

### Post by dolny on 2005-05-12
dolny@milkshake:~$ sudo dpkg -i freeciv-client-gtk_2.0.1-1_i386.deb
Zaznaczenie poprzednio niezaznaczonego pakietu freeciv-client-gtk.
(Odczytywanie bazy danych ... 91962 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie freeciv-client-gtk (z freeciv-client-gtk_2.0.1-1_i386.deb) ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie freeciv-client-gtk:
 freeciv-client-gtk zale&#380;y od libsdl-mixer1.2 (>= 1.2.6); jednak&#380;e:
  Wersja libsdl-mixer1.2 w systemie to 1.2.5-9.
dpkg: b&#322;&#261;d przetwarzania freeciv-client-gtk (--install):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 freeciv-client-gtk
dolny@milkshake:~$

It basically says that i need libsdl mixer 1.2.6 or newer and I have 1.2.5-9 installed. How can I update it? 

Kubuntu 5.04.

---

### Post by gil-galad on 2005-05-12
I built freeciv debs for ubuntu, you can get them at [http://web.umr.edu/~erprz9/freeciv/](http://web.umr.edu/~erprz9/freeciv/).  Have fun!

---

### Post by dolny on 2005-05-12
[ post edited ]

---

### Post by Goober on 2005-05-13
Ok, i just successfully installed FreeCiv, however, I have a slight problem when trying to open it up.

When i click on it, it comes up with a little Box telling me to "Connect to FreeCiv Server".  In there, it has spaces for me to put in my Name, Host, and Port.  It comes up with those spaces filled already, the Name with my Name, the Host as "localhost", and the Port as "5555".  I click "Connect", and it says connection refused.  

So, what is going on?  Why doesn't it work?  And how do I get it working?

---

### Post by henriquemaia on 2005-05-15
[QUOTE=gil-galad]I built freeciv debs for ubuntu, you can get them at [http://web.umr.edu/~erprz9/freeciv/](http://web.umr.edu/~erprz9/freeciv/).  Have fun![/QUOTE]

Thanks a lot, gil-galad!

---

