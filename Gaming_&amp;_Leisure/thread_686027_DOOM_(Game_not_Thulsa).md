---
title: "DOOM (Game not Thulsa)"
date: 2008-02-02
forum: Gaming &amp; Leisure
---

### Post by diddler on 2008-02-02
OK, finally decided to try gaming again.  Still have no luck with WINE, so I downloaded ALL the DOOM files I could find on synaptic.  When I finished I had a new icon in the game folder "LXDoom Shoot 'em Up" but, needless to say clicking on it accomplishes NOTHING.  Any way to get the game to run?  I have looked at the other posts on this subject, but they are all over a year old, so I figured something new may have happened in that time to make doing this possible.  I realize it's a long shot, but I thought I would try.  If the old posts are still the way to go, just link me to the best one.  Thanks.

---

### Post by suziequzie on 2008-02-02
I'm sorry to say I don't know how to solve your problem. I just wanted to give you Kudos for the Conan reference!:KS

---

### Post by gigaferz on 2008-02-02
did you get the wad files?

 i tried that a while and i run it from command line only,

---

### Post by disturbedite on 2008-02-02
yes, the wads contain the actual game data, so you need them to run any doom client.  if you don't have the original doom series/wads then you need to purchase it/them.

don't use lxdoom or prboom from the ubuntu repo, they're SERIOUSLY outdated.  use a newer doom source port/client.
i'd highly, highly recommend skulltag.
install fmod (a requirement) from here:
[http://ppa.launchpad.net/rzr/ubuntu/pool/main/f/fmod3/](http://ppa.launchpad.net/rzr/ubuntu/pool/main/f/fmod3/)
then grab & install the skulltag ubuntu downloads here:
[http://skulltag.com/download/](http://skulltag.com/download/)

place the wad(s) in the place you install skulltag.

---

### Post by diddler on 2008-02-03
How do I install these things?  I have down loaded them to the desktop.

---

### Post by disturbedite on 2008-02-03
i told you already how to "install".  but to elaborate...
1.  install the fmod package i mentioned before.
2.  extract the skulltag ubuntu download & create a skulltag folder (anywhere) and put the extracted files in that folder.
3.  put your wad(s) in the same folder as the skulltag folder you created.
4.  run skulltag

---

### Post by Jay Jay on 2008-02-09
Did all of that, doesn't start... 

```
Cannot find a game IWAD (doom.wad, doom2.wad, heretic.wad, etc.).
Did you install Skulltag properly? You can do either of the following:

1. Place one or more of these wads in the same directory as Skulltag.
2. Edit your skulltag-username.ini and add the directories of your iwads
to the list beneath [IWADSearch.Directories]

```

I placed the wad file into the same directory :confused:

---

### Post by sfgreenwood on 2009-02-09
> **Jay Jay said:**
> Did all of that, doesn't start... 

```
Cannot find a game IWAD (doom.wad, doom2.wad, heretic.wad, etc.).
Did you install Skulltag properly? You can do either of the following:

1. Place one or more of these wads in the same directory as Skulltag.
2. Edit your skulltag-username.ini and add the directories of your iwads
to the list beneath [IWADSearch.Directories]

```

I placed the wad file into the same directory :confused:

The wad file name needs to be lower case. If you've just pulled it off a CD (like I have) it will be in upper case.

In the terminal type
```
mv FILENAME.WAD filename.wad
```

---

### Post by grossaffe on 2009-02-09
I'm a fan of EDGE (Enhanced Doom Gaming Engine)

---

