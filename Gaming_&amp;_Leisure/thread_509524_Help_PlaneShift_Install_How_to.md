---
title: "Help PlaneShift Install How to"
date: 2007-07-25
forum: Gaming &amp; Leisure
---

### Post by sprwaka on 2007-07-25
Can someone please write a tutorial for Planeshift? More than anything how to install, files need it by the game, the need of graphics card, step by step "how to" for ./compile, make install, and  I know is a lot of info in the page and some info in the forum but trying to put it together is getting complicated. Plus it will make a lot easier the install for newbees like me. Of course I'm not asking to do the job for me but at least be point to the right direction not just go to the home page, install the necessary files, compile and done.


Thanks...

---

### Post by donkyhotay on 2007-07-25
Don't know why you would need a tutorial since the instructions on the planeshift website are sufficient. It's just a matter of running the binary installer like any other program. Make certain you have permission to execute and:
./planeshift_CBV*
will install locally for your account or of course use sudo for system-wide install. The only issue I've ever had with planeshift is the GUI updater which doesn't work quite right under linux. I've found the best way to update is to use the CLI version and skip the GUI. 
./updater --auto
that will update the program without bringing up the GUI, and works much better IMO.

---

### Post by skeeterflea on 2007-07-25
Its not working for me either... I've been searching the web for an hour, and everything i've tried so far hasn't worked.  The file shows up as green in terminal, and i thought the chmod a+x would allow me to run it, but it's still giving me the Cannot execute binary file message, I'm on dapper drake btw.


chmod a+x PlaneShift_CBV0.3.019-x64.bin

./PlaneShift_CBV0.3.019-x64.bin: ./PlaneShift_CBV0.3.019-x64.bin: cannot execute binary file

---

### Post by hikaricore on 2007-07-25
> **skeeterflea said:**
> Its not working for me either... I've been searching the web for an hour, and everything i've tried so far hasn't worked.  The file shows up as green in terminal, and i thought the chmod a+x would allow me to run it, but it's still giving me the Cannot execute binary file message, I'm on dapper drake btw.


chmod a+x PlaneShift_CBV0.3.019-x64.bin

./PlaneShift_CBV0.3.019-x64.bin: ./PlaneShift_CBV0.3.019-x64.bin: cannot execute binary file\

That looks like a 64bit binary.  Are you indeed on a 64bit system out of curiosity?

---

### Post by skeeterflea on 2007-07-25
Hmm very good question =D

When I issue uname -p I get "unknown"

But...

```
user@ubuntuhom:~/Desktop$ uname -a
Linux ubuntuhom 2.6.15-28-686 #1 SMP PREEMPT Wed Jul 18 22:57:30 UTC 2007 i686 GNU/Linux
```

i686 wouldn't work on a 32 bit system would it?  

Sorry for my novice'ness...

---

### Post by skeeterflea on 2007-07-25
yep i'm an idiot...

Thanks

---

### Post by DrMoxie on 2007-07-28
I'm having a slightly different problem.  The install went fine and the game launches but the fonts are completely garbled.  xorg.conf is set for 24bit color depth and I am using Intel GMA 940 chipset ([the laptop is from ZaReason]("http://www.zareason.com/shop/product.php?productid=16140&cat=0&page=1")).  I've tried launching the game with sudo thinking maybe I bungled the rights during install but it is the same result.  

Any ideas? Thanks!

---

### Post by eyeofthebeholder on 2007-07-28
I'm having the same issue as Dr.Moxie.
Apparently, its a mesa issue but, I haven't had any success getting an updated version installed on feisty.
I've tried both 6.5.3 and 7......

Edit - - Same issue with Penguin Racer

---

### Post by sejwan on 2007-07-29
For the garbled font issue do this it worked for me. open up the file Planeshift3D/data/config/r3dopengl.cfg in a nd find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.
Also after you use the pdater make sure to do this again.

---

### Post by eyeofthebeholder on 2007-07-29
> For the garbled font issue do this it worked for me. open up the file Planeshift3D/data/config/r3dopengl.cfg in a nd find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.

Thanks for the response but, that did not fix the issue.

---

### Post by DrMoxie on 2007-07-29
> **sejwan said:**
> For the garbled font issue do this it worked for me. open up the file Planeshift3D/data/config/r3dopengl.cfg in a nd find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.
Also after you use the pdater make sure to do this again.
 Hey! That did the trick for me! Eye, could it be that you've upgraded versions of mesa?

---

### Post by eyeofthebeholder on 2007-07-29
> Hey! That did the trick for me! Eye, could it be that you've upgraded versions of mesa?

I did try to upgrade mesa but, both versions 6.5.3 and 7 crashed my machine.
When I check glxinfo - mesa version is still showing original version (see below). 

OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

---

### Post by bradleee on 2007-08-10
> **sejwan said:**
> For the garbled font issue do this it worked for me. open up the file Planeshift3D/data/config/r3dopengl.cfg in a nd find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.
Also after you use the pdater make sure to do this again.

This fixed my garbled font issue, thank you for your help.

-Brad

---

