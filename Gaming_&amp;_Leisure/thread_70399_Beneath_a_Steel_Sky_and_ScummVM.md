---
title: "Beneath a Steel Sky and ScummVM"
date: 2005-09-29
forum: Gaming &amp; Leisure
---

### Post by DariusTriplet on 2005-09-29
I just recently installed BASS and ScummVM off of APT, but have no idea how to run BASS.  When I open ScummVM, it asks for the path to BASS, of which I have no idea.

Where would APT install BASS to?

(On a related note, while running the HOTU version of BASS under WinXP via ScummVM, the sounds were really garbled.  Does this bug exist in the version off APT?)

---

### Post by twowheeler on 2005-09-29
I don't have BASS installed right now so I can't check, but on a previous PC my BASS was in /usr/games/bin/bass I believe.  See if that works.  Once you find the executable, it should start BASS directly and you should not need to start scummvm first.

---

### Post by jasay on 2005-09-29
Mine seems to be located here:
/usr/share/scummvm/beneath-a-steel-sky

Hope it helps.:)

---

### Post by DariusTriplet on 2005-09-30
I was able to find a sh that'll run it in /usr/games, and bypass the ScummVM "Choose a Game" screen.

Thanks for the help!

---

### Post by snowjunkie on 2005-10-03
I've just installed it also, it loads and displays the logos "Virgin" and "Revolution" and then the screen just goes black.  Any ideas?

Correction: it's working now.  Think it's because I killed esd first.

---

### Post by brentoboy on 2005-10-03
run it from command line inside a terminal, if there are errors, it will display them in the terminal as is crashes.

Also, you can use synaptic to find out where files are located, the top setting on the first tab says something about show package details or something (i'm not at home to check)  Anyway, then select the package and there are tabs in the details area - one of them tells you which files are installed with that package. - and where they are.

I'm guessing your problems are with opengl. but who knows.

---

### Post by fishfork on 2005-10-05
The command you need to run is 'sky'. Once you're in, F5 gives you the menu (in case you can't figure out how to quit!)

It runs great here. Problem is, I'm totally stuck on the first screen! Is it supposed to be this hard? Or am I just being a bit slow here...

---

### Post by fishfork on 2005-10-05
Aha, I've figured it out! You just have to be observant...

---

### Post by patrick295767 on 2006-07-03
How to pass the game Beneath a Steel Sky  into a fullscreen ??
  
I have it into a small window 
and there is nothg into scummvm to change to fullscreen. 

thx !!

---

### Post by Cylence on 2006-11-27
You can either edit global or game options inside ScummVM, or just press alt+enter when the game starts.

---

### Post by takuhii on 2007-06-16
does anyone know how to access the inventory in Beneath a Steel Sky??? I pick things up and that's it, I never see them again... Please help.

---

### Post by Saoshyant on 2007-07-09
> **takuhii said:**
> does anyone know how to access the inventory in Beneath a Steel Sky??? I pick things up and that's it, I never see them again... Please help.

I believe you either use the "?" key or the "Tab" key.

---

### Post by oldsmobile_mike on 2008-02-27
> **Saoshyant said:**
> I believe you either use the "?" key or the "Tab" key.

To access the inventory you move the mouse pointer to the top of the screen, and it slides down from the top.

Other keys:
P = Pause
Alt + Enter = make game fullscreen
F5 = in-game menu to load, save, etc.
I think Esc aborts the game and kills you, but since I'm right in the middle of something I don't want to test it.  ;-)

Awesome game, btw!

---

### Post by ugm6hr on 2008-04-01
I had a demo of this game on my old Amiga - and I don't think I even managed to finish the demo.

Hopefully I'm smarter now :)

Thanks for the keyboard controls.

PS: I can get to the inventory by just moving my mouse to the top of the screen.

---

### Post by DoriftuEvo on 2008-06-21
I am having trouble getting this game to work.  I type the following in the terminal...

```
/usr/games/scummvm -p /usr/share/scummvm/beneath-a-steel-sky sky
```

and get...

```
Could not initialize SDL: No available video device!
```

I'm not exactly sure what this means.  I couldn't find anything called SDL in synaptic.

---

### Post by superplasmafist on 2009-04-15
> **snowjunkie said:**
> I've just installed it also, it loads and displays the logos "Virgin" and "Revolution" and then the screen just goes black.  Any ideas?

Correction: it's working now.  Think it's because I killed esd first.

how did you make it work?

i have the same problem can anyone help please

thanks

---

### Post by R33D3M33R on 2009-04-15
Try this in terminal:

```
killall esd
```

or

```
killall artsd
```

---

### Post by superplasmafist on 2009-04-16
> **R33D3M33R said:**
> Try this in terminal:

```
killall esd
```

or

```
killall artsd
```

i wasnt really sure where to type it but i typed it in a second bash window

it didnt work

the screen still black after the company logos

---

### Post by parke on 2011-01-27
To access the inventory, move the mouse near the top of the window/screen.  The inventory bar will appear.

---

### Post by Perfect Storm on 2011-01-28
Necromancing. Thread closed.

---

