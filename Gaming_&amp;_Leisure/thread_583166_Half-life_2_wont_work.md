---
title: "Half-life 2 wont work"
date: 2007-10-20
forum: Gaming &amp; Leisure
---

### Post by linux-loser on 2007-10-20
half-life 2 on fiesty... i finnally after several days got steam to work yesturday with some help.  through steam i downloaded half-life 2.  the first time i tried to run it it froze up and quit in the middle of the first loading screen.  so i closed everything and restarted the computer.  now the game is running insanely slow, its horrible.  anyone know how to fix this?

---

### Post by Alex Carroll on 2007-10-20
Press Alt+F2 and type winecfg

Go to the Audio tab and tick the OSS sound driver box. Uncheck ALSA as well. That should work.

---

### Post by linux-loser on 2007-10-20
nope, thanks for trying but all that did was turned the games sound off.  still runs the logos just as slow and the game still freezes.

---

### Post by shad0w_walker on 2007-10-20
Can we get some system details from you? Graphics card, processor, RAM, that sort of thing. Also, have you tried tweaking any of your graphics settings both in game and using wines registry?

I had horrible performance with HL2: Episode 2 until i tweaked a couple of things. I'l have a look in my links and history and see if i can't dig up the fixes i used.

P.S.

Have you checked out this page? It might have a few bits of information that are useful to you.

[http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/)

Update:

[http://wiki.jswindle.com/index.php/Wine_Registry#Graphics](http://wiki.jswindle.com/index.php/Wine_Registry#Graphics)  This site might help you out. It lists various edits you stick in the wine registry to enable things such as GLSL (Shader model 2 i believe)

You may also want to set the startup options of HL2 to:

-novid -dxlevel 80

---

### Post by linux-loser on 2007-10-20
fiesty 7.04 x64.
amd 3800+
geforce 8600GT with the Envy Nvidia drivers installed.  
1GB ram

i have a wide screen monitor so i set the ingame video to 1680x1050, everything was preset to high.  i changed the reflections from simple to reflect all.  this is the way i had it run on windows and it ran perfectly with no lag or glitches.

i have not made any changes to wine, im so new to linux that im not even sure on how to that.

---

### Post by shad0w_walker on 2007-10-21
Do you know how to use regedit on windows? The wine version works just the same, all you need to do from there is put in the entries it shows on link. To access the wine registry just hit Alt+F2 and run the command:

```
regedit
```

As for setting the options for HL2.

1. Open Steam and goto the Games tab.
2. Right click on HL2 and select Properties
3. When the Properties dialog opens, click Set launch options.
4. In the text box on the Launch options dialog, try entering these options

```
-novid -dxlevel 80
```

5. Give the game another go, hopefully it should work ok now.

---

