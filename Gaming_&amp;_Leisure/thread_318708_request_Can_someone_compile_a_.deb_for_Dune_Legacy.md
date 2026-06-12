---
title: "*request* Can someone compile a .deb for Dune Legacy?"
date: 2006-12-14
forum: Gaming &amp; Leisure
---

### Post by ed_agamemnon on 2006-12-14
Could anyone who knows how please compile a .deb package for Dune Legacy? Or provide compilation instructions?

Thank you

---

### Post by ed_agamemnon on 2006-12-23
please please please!

---

### Post by Naegling23 on 2006-12-24
im running dune on a genesis emulator.  Its not quite the same, but its similar enough.  (and the genesis version is the one I first played anyway)

---

### Post by ed_agamemnon on 2006-12-26
i think i could make it run in wine... but i'm quite keen on the new features (multi-player, etc) that Dune Legacy has added.

Genesis - is that a Mega Drive over here in Europe?

---

### Post by Stemp on 2006-12-26
Dune Legacy ? 
I use Dune and Dune 2 with Dosbox.
[http://ubuntu-tutorials.com/2006/12/25/dos-emulation-with-dosbox-get-your-old-school-game-on/](http://ubuntu-tutorials.com/2006/12/25/dos-emulation-with-dosbox-get-your-old-school-game-on/)

---

### Post by ed_agamemnon on 2006-12-31
But as I said, the original game doesn't offer multiplayer. I want multiplayer. I want Dune Legacy! :)

---

### Post by diepruis on 2007-01-01
Is this free? Open-source? A dos game? Could you provide some more information and perhaps a link?

---

### Post by Frem on 2007-01-03
First hit on google: [http://dunelegacy.sourceforge.net/wiki/index.php/Main_Page]("http://dunelegacy.sourceforge.net/wiki/index.php/Main_Page")

Looks kinda like Wargus.

---

### Post by diepruis on 2007-01-04
I'm having a look to see if it compiles over here. I don't have the Dune 2 data files though. I wonder if Dune2k's files will work?

---

### Post by diepruis on 2007-01-04
Well looks like the Dune2K files won't work.

Here's what I did to get it as far as I could without the files:
```

wget http://surfnet.dl.sourceforge.net/sourceforge/dunelegacy/dunelegacy-0.94.1-bin.bz2
bzip2 -d dunelegacy-0.94.1-bin.bz2
./dunelegacy-0.94.1-bin

```

It needs some libraries though, of which I only have outdated copies. If you are using Edgy your mileage might vary. This is what I had to do to get the dependencies:
```

sudo aptitude install libzzip-0-12 libsdl-gfx1.2-4
sudo ln -s sudo ln -s /usr/lib/libSDL_gfx.so.4 /usr/lib/libSDL_gfx.so.13
sudo ln -s /usr/lib/libzzip-0.so.12 /usr/lib/libzzip-0.so.13

```
You might have the updated libraries in your repositories, try to find them.

A caveat: I'm not sure if those symlinked / kludged libraries are going to hold up. If they don't and you can't find the updated versions on the repo's, you will need to compile the correct versions of libzzip and libsdl-gfx from source. Remove the symlinks created above before you try that though.

Wish I could be more help. Good luck and have fun.

---

