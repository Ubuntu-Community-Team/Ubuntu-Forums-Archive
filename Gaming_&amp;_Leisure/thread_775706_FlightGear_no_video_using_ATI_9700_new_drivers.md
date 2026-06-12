---
title: "FlightGear no video? using ATI 9700 new drivers"
date: 2008-04-30
forum: Gaming &amp; Leisure
---

### Post by stoer on 2008-04-30
Hi all,
Flightgear:
I read a recent review in a Linux magazine recently and went looking...
Found it in the Repo's for Hardy and have installed via Add/Remove.

I get a panel with a picture of a plane ans see the various components being read and loaded.

The game window then opens, but it's just a gray screen with some flashing colour now and again.  Lots of aircraft motor noise.
Along the top of the screen are the various menu buttons - also grey.
I can for example, click on the first greyed out menu, it opens (also grey, no words) and choose the last item (where you'd expect Quit to be), and the program quits.

Everything appears to work, thus. Just no video.

I'm using a laptop with a pentium mobility 1.6 Ghz, with 1.5 Gb ram and an ATI radeon mobility 9700 (256mb) graphics card.  The driver i'm using was loaded by ENVY (vs. 8.03) and i'm getting direct rendering. I have Kubuntu 8.04 installed and have turned Extra effects/compiz off. Other open gl games all work fine.

Can anybody shed some light on why i'm not able to get video?
Please

---

### Post by stoer on 2008-05-01
No FlightGear fans?

Would really appreciate any tips at all to get this working...

---

### Post by cubeist on 2008-05-02
> **stoer said:**
> No FlightGear fans?

Would really appreciate any tips at all to get this working...

Flightgear does not work for me without ensuring metacity is the working window manager (I normally use compiz)
So before launching fgfs I do a alt-f2 and type
```
metacity --replace
```
then I drop my resolution down to 1024x768 to get really decent frame rates...

when done I bring compiz back up with another alt-f2
```
compiz --replace
```

I'm not sure if this will help you or not... I use gnome with compiz with ati...so we have similar settings except for kde/gnome...

---

### Post by stoer on 2008-05-10
Hey thanks for th ereply, sorry for taking so long in getting back to this but
I've been working solidly the last week so i''ve not been arround much.

I tried from within compiz and from metacity, same sort of result i'm afraid.

I did find the following post which does improve things, at least i get video output an dcan see th escenery, controls etc.

" 
Hi

I don't know if you/anyone else is still having the same problem, but I found a solution to mine:

Start FG in the normal way. Select 'View' drop-down menu (one from the left- you may not be able to read the labels!) Select 'Rendering Options' (fourth choice) Uncheck 'Use Point Sprites for Runway Lights' (fourth check-box)

When you come to quit FG, do so by menu: File...Exit, rather than closing the window to save this setting.

I hope that this works for you, and you can enjoy FlightGear.

Charlie

[http://ubuntuforums.org/showthread.php?t=627314&highlight=flight+gear](http://ubuntuforums.org/showthread.php?t=627314&highlight=flight+gear)
"


Only thing is everything is soooo very slow and also after a few minutes locks solid not allowing me to do anything other than killing the game and restarting the laptop.

Thought i was getting somewhere...  I suspect there's something wrong with my ATI driver setup as i'm getting some occaisional problems with other opengl/3d games, even with supertux (2d scroller) :(

cheers

---

