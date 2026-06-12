---
title: "quake3 no sound :\"
date: 2005-02-28
forum: Gaming &amp; Leisure
---

### Post by blunt on 2005-02-28
hi there. 
im running a P4 2.4 with a geforce FX 5200, 512MB and a **sound blaster AudigyLs**. 
Im having some problems related to the sound card part, but i believe that this is not related. 

**I dont have sound on quake3** with the sound blaster, but i used to when i used my onboard soundcard. this is the error that i get on startup...

```
------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
```

due to my noobness i dont have a clue on what this is.. i have sound on video, mp3 and all other stuff, but my duplex isnt working.. (cant have 2 apps @ the same time  using sound).

Anyways, if any of u gamers can help it would be great. 
btw, check [truecombat](http://www.truecombat.com) site. this mod rocks  =)

thanks.

---

### Post by Moobert on 2005-02-28
right find the quake 3 config file in...
~/.q3a/baseq3

you may need to chown from root to your normal user

then edit the line
seta snddevice "/dev/dsp"

to say
seta snddevice "/dev/adsp"

I've found i have to do this in enemy territory as well to get sound.

---

### Post by m6mb3rtx on 2009-08-01
I found a solution it worked for my ubuntu 8.10, give it a try!
 

> 
Step One:

Make sure that /proc/asound/card0/pcm0p/oss is writeable (if you trust your system enough, you can chmod to 777). 

Step Two:

Create the following launcher:

```
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss && quake3
```

Granted, once the echo "quake3.x86...0p/oss part is run once, it probably doesn't need to be run again, but this way it runs each time before you launch the game just in case something somewhere else on the system changed something. The "&& quake3" part just runs the quake3 launcher once it's done w/ the first part.



Here is the original link:
[http://www.linuxquestions.org/questions/linux-games-33/no-sound-quake-3-linux-260975/page3.html]("http://www.linuxquestions.org/questions/linux-games-33/no-sound-quake-3-linux-260975/page3.html")

---

### Post by claw1 on 2009-08-09
> Step One:

Make sure that /proc/asound/card0/pcm0p/oss is writeable (if you trust your system enough, you can chmod to 777). 

Step Two:

Create the following launcher:

 ```
Code:
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss && quake3 
```Granted, once the echo "quake3.x86...0p/oss part is run once, it probably doesn't need to be run again, but this way it runs each time before you launch the game just in case something somewhere else on the system changed something. The "&& quake3" part just runs the quake3 launcher once it's done w/ the first part.I did this to my OSS archive and it worked, but when i start battle the game stops completely, it keeps looping to a frame.

How can i get back my "oss" to what it was before? :( please.

I mean, without the  *"quake3.x86 0 0 direct"* that's now written on it

---

### Post by TheJeffsta on 2009-12-18
I am currently trying to get Quake to work for me also, I am assuming that you do this in the Terminal using sudo?

---

### Post by JayKay3000 on 2009-12-18
[http://www.quakelive.com/#home](http://www.quakelive.com/#home)

Full 3D quake 3 in a browser, no install needed. Worked in firefox anyway.

---

### Post by jcer93705 on 2010-07-19
> **JayKay3000 said:**
> [http://www.quakelive.com/#home](http://www.quakelive.com/#home)

Full 3D quake 3 in a browser, no install needed. Worked in firefox anyway.

Sorry but its a modified quake 3 its not original. Original you can do so much, add maps, try different mods, create you're own mode and load it to quake 3. Quake live is so limited on doing stuff.

---

### Post by getphuture on 2010-10-17
I explained a little bit on my post. The best way is to use the sdl output solution: [http://ubuntuforums.org/showthread.php?p=9986973](http://ubuntuforums.org/showthread.php?p=9986973)
I think it can help you.

---

### Post by flying sheep on 2010-10-17
why don’t you use ioquake3?
it’s the original gaming experience with modernized and maintained codebase

---

