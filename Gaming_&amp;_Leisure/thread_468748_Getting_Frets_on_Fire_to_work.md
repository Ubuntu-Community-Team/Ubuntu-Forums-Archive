---
title: "Getting Frets on Fire to work"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by synd7 on 2007-06-09
Anybody know how to get Frets on Fire to work? It looks awesome but it refuses to work for me

Right now its complaining about svg not being loaded. I'm guessing this pertains to amanith and pyamanith. The problem its pyamanith seems dead, no links, and amanith looks complicated to compile. Are there debs for these out there?
Or some help on compiling amanith at least?

Thanks in advance

---

### Post by synd7 on 2007-06-10
So nobody has gotten frets on fire to work???

---

### Post by Iarwain ben-adar on 2007-06-10
Euhm,

it would be helpful if you posted the complete error (commands entered and output)

That way we can see what's going awry :D

On what system are you trying it to run? Dapper, Edgy, Feisty?


Iarwain

---

### Post by chuckyp on 2007-06-10
Frets on fire works fine for me.  Just straight download from their site.  I haven't tried getting the xbox 360 guitar to work with it yet in ubuntu.  But I will be fiddling in July with that.

---

### Post by synd7 on 2007-06-10
Sorry, i havent had internet at home over the last few days so i couldnt get the error

```
File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/console.py", line 27, in ?
File "src/FretsOnFire.py", line 60, in ?
File "src/Gameengine.py", line 187, in _init_
File "src/Data.py", line 48, in _init_
File "src/Data.py", line 108, in loadSvgDrawing
File "src/Svg.py", line 579, in ConvertToTexture
File "src/Svg.py", line 599, in _render
OpenGL.GLerror: [errono 1281] invalid value
```

i'm not sure if thats exactly it, i get a black screen then resized to 640x480 and locks my mouse so i cant copy and paste

In the changelog, the most recent version has "linux packaging fixes" maybe that inadvertantly ruined something?

---

### Post by chuckyp on 2007-06-10
What type of video card do you have?  You need opengl working to have frets on fire work.  i.e. if you have nvidia you need to install nvidia-glx package or the binary drivers from their site.

---

### Post by synd7 on 2007-06-10
I've got a Radeon 9800 & i'm using the open source drivers, i get direct rendering and i can use aigx(yay :D )

I'mm try the fglrx drivers and see if that helps

Oh and i'm using Feisty

Edit: Weird,  it works with fglrx, but not the opensource drivers. Oh well i guess its just one of those linux quirks :D

---

### Post by BeardlessForeigner on 2007-06-10
When i was running fglrx FoF worked fine, but then i reinstalled feisty and have the open source drivers running with aiglx since this works much better than XGL for me, adn FoF just goes to a black screen and then to low resolution with no mouse movement. I guess I won't be able to get it to run without fglrx >_<. i might just try it in windows.

---

### Post by xanium4332 on 2007-06-16
I also have the exact same problem, but with my laptop (which is also using the opensource radeon drivers), it's fine!

My laptop has a radeon 9200, but my desktop is a radeon x850 xt pe. I think it might be due to the experimental side of the opensource radeon drivers for later cards.

---

### Post by synd7 on 2007-06-18
I think that must be it, ive got a 9800 (r300 series) and i believe thats one of the "experimental" direct rendering cards. 

Has anybody had success running FoF with the open source drivers on a fairly new card?

---

