---
title: "is there a fighting game for linux ?"
date: 2006-08-10
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2006-08-10
is there a fighting game for linux - except open-mortal

---

### Post by DoktorSeven on 2006-08-10
Not really -- fighting games are mostly on consoles and arcade games; there's not really a lot of fighting games for PC, even for Windows.

You could install XMame and run some of the older arcade fighting games, though of course you'd have to provide it with the ROMs (which you'll have to find yourself -- it's not proper to download copyrighted ROMs from the Internet for free by searching Google for them, nudge nudge wink wink).

---

### Post by MaximB on 2006-08-11
and that drings me to my other question :
how can I play with xmame ?
I have 2 threads about it in this forum with my problems but without answers
can you help ?
search them and answer....
thanx ahead

---

### Post by Perfect Storm on 2006-08-11
Can you use something like this? [http://doc.gwos.org/index.php/Beats_of_Rage](http://doc.gwos.org/index.php/Beats_of_Rage)

---

### Post by patrick295767 on 2006-08-11
there is game like Mortal kombat, i forgot the name
not really good

Or there is great fighting games with N64 mupen64 (, if the rom is working) !
 
I have killer instinct 1 rom  for Arcade box 
but still cannot use it under linux
only under windoze 
 
but you know linux & gaming, not soo easy

---

### Post by MaximB on 2006-08-11
it's called "open mortal"
can you help me install xmame or somthing like  that ?

---

### Post by patrick295767 on 2007-01-20
> **MAXDDARK said:**
> is there a fighting game for linux - except open-mortal

Killer instinct !!!!!!!!!!!
  
(with mame)
(download ki1.img or ki.img)
  
I wrote a bit a quick howto, but that hangs with chd file

---

### Post by RomeReactor on 2007-01-20
Aside frome the ones already mentioned, only [Mugen]("http://randomselect.i-xcell.com/") and [Toribash]("http://www.toribash.com/") come to mind at the moment.

---

### Post by haxer on 2007-01-20
Mugen looks nice :) rom or easy install?

---

### Post by RAV TUX on 2007-01-20
> **MAXDDARK said:**
> is there a fighting game for linux - except open-mortalCastle Wolfenstein

---

### Post by burek on 2007-01-20
look at that max, [http://www.mame.net/screenshotsK1.html#kof95](http://www.mame.net/screenshotsK1.html#kof95)

---

### Post by haxer on 2007-01-20
How to use roms and stuff like that?

---

### Post by burek on 2007-01-20
> **haxer said:**
> How to use roms and stuff like that?

look howto mame xmame 2 threads above :D

---

### Post by RomeReactor on 2007-01-20
> **haxer said:**
> Mugen looks nice :) rom or easy install?

For Mugen, just untar the file, change to the mugen directory and double click the mugen executable. Or make a launcher: Let's say you have mugen in "home/haxer/games/mugen"; then right-click on the desktop, select "Create Launcher" and fill the "Command" section like this:

```
sh -c "cd /home/haxer/games/mugen && /home/haxer/games/mugen/mugen"
```

---

### Post by MaximB on 2007-01-20
thanks guys
I know mames and mugen
I have a problem with mugen - I can't add new characters (I add the characters at the config file but it doesn't recognize them).
I hoped Linux had a native games and not an emulators.

P.S
jozef - Castle Wolfenstein is NOT a fighting game, it's a FPS (first person shooter).

---

### Post by RomeReactor on 2007-01-21
Make sure the name of the character you add in "mugen/data/select.def" matches the name of the ".def" file in "mugen/chars/name_of_char". Remember it's case sensitive.

---

