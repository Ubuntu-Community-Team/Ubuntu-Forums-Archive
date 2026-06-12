---
title: "[SOLVED] Found a weird bug when starting SDL mame 122u7"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by heatblazer on 2008-01-27
Here is what happened when I installed SDL mame 122u7. Any ideas what`s the problem and a way to solve it?

---

### Post by FranMichaels on 2008-01-27
Okay, I just downloaded SDLMame 122u7 and built it from source.

It works fine for me. 

I think something with your mame.ini?
Try running sdlmame with the argument 
-createconfig

Then modify the ini as appropriate for your machine (make it point to your roms etc.) 

:)

---

### Post by BigSilly on 2008-01-27
Could it possibly be Compiz-Fusion that's causing the problem? If you have it enabled, try disabling it and then running your MAME again. I had a similar problem when I used version 120u1.

---

### Post by Vadi on 2008-01-27
So where does the coin go?

---

### Post by FranMichaels on 2008-01-27
> **BigSilly said:**
> Could it possibly be Compiz-Fusion that's causing the problem? If you have it enabled, try disabling it and then running your MAME again. I had a similar problem when I used version 120u1.

I'm running sdlmame with compiz-fusion on the whole time. I put the yuvmode to none so I could take a screencap. I'm pretty sure something in the ini file is problem. Those terminal errors about display look fishy.

---

### Post by FranMichaels on 2008-01-27
> **Vadi said:**
> So where does the coin go?

By default in MAME, the "insert coin" switches are mapped to the keyboard keys 5, 6, 7 and 8. 

[http://mamedev.org/devwiki/index.php/FAQ:Running#How_do_I_start_the_game.3F](http://mamedev.org/devwiki/index.php/FAQ:Running#How_do_I_start_the_game.3F)

;)

---

### Post by heatblazer on 2008-01-27
I have tried various things from the ini file... It`s the same again... Pretty weird...

---

### Post by FranMichaels on 2008-01-27
> **heatblazer said:**
> I have tried various things from the ini file... It`s the same again... Pretty weird...

Even from a new ini file? 
This didn't happen with previous version?

Do you have video output set to soft?

---

### Post by heatblazer on 2008-01-28
I have tried with entirely new ini file and with the soft video render. It`s the same. The console video output shows frames but when I start the game they stop.

---

### Post by disturbedite on 2008-01-28
> **FranMichaels said:**
> Okay, I just downloaded SDLMame 122u7 and built it from source.

It works fine for me. 

I think something with your mame.ini?
Try running sdlmame with the argument 
-createconfig

Then modify the ini as appropriate for your machine (make it point to your roms etc.) 

:)
you didn't have to compile it.  there are up-to-date ubuntu packages of it available here:
[http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)

---

### Post by heatblazer on 2008-01-29
[delete_me]

---

### Post by heatblazer on 2008-01-29
I have confirmed the error on another PC. My mom`s PC. I`ve never installed SDL mame there, but the same bug happened and there. My mom`s pc is Duron 999 MHz nVidia/ GeForce 3 Titanium/ 1 G RAM DDR, so this is totally different from mine machine... The problem is not in the hardware.

---

### Post by FranMichaels on 2008-01-29
> **disturbedite said:**
> you didn't have to compile it.  there are up-to-date ubuntu packages of it available here:
[http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)

If it's not an official Ubuntu package, I prefer to just build from source. It's trivial after getting the dependencies. And justifies my dual core. It'll be a sad day when I can't get a processor to use 100% ;)

For sdlmame I literally do
make -j2

Personal preference though. Also, sometimes I like to run the mecurial or git or svn versions of things, less downloads that way too :)

Anyway, what package is the OP using? Is it possible a pre-compiled package is problem? Maybe some feature was disabled/enabled causing issues?

If not, maybe time to let the sdlmame devs know about the issue (if the op hasn't already)

---

### Post by heatblazer on 2008-01-29
What, what :) Please can you give more complicated instrucitons? When I download the source I shall do sudo make&&make install ? or any other options???

---

### Post by disturbedite on 2008-01-29
> **FranMichaels said:**
> If it's not an official Ubuntu package, I prefer to just build from source.
thats cool if you want to.  but the package is up for review to become an official ubuntu package, fwiu.

---

### Post by heatblazer on 2008-01-30
SLD mame has began to work. Duuno how... It was an update of KDE lib files and after that SDL mame is working. It really does not make any sense... But since it is working I don`t care :) Thanx all for the sympathy and for the assistance.

---

### Post by FranMichaels on 2008-01-30
> **heatblazer said:**
> What, what :) Please can you give more complicated instrucitons? When I download the source I shall do sudo make&&make install ? or any other options???

It is really that simple, but you'll probably need to install some dependencies the first time through. It should give a useful error while building in that case.

You can change options in the makefile, just read through SDLMAME.txt (although I just stick with default)

Other than that, it's basically just make :) No autogen.sh or ./configure :KS

> **disturbedite said:**
> thats cool if you want to.  but the package is up for review to become an official ubuntu package, fwiu.

Very cool. it'll be nice to have something newer than xmame in the repos. I mean, I like to build some apps, but the less the better :KS

> **heatblazer said:**
> SLD mame has began to work. Duuno how... It was an update of KDE lib files and after that SDL mame is working. It really does not make any sense... But since it is working I don`t care :) Thanx all for the sympathy and for the assistance.

Cool, guess it wasn't the binary for sure, but, does the same update fix your mother's machine too? Is she running KDE? Either way, glad it is working :)

---

### Post by disturbedite on 2008-01-30
> **FranMichaels said:**
> Very cool. it'll be nice to have something newer than xmame in the repos. I mean, I like to build some apps, but the less the better :KS
same here.  call me lazy if you want...  :)

---

