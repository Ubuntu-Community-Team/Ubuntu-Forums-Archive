---
title: "how to run Linux Evolution Soccer?"
date: 2010-11-28
forum: Gaming &amp; Leisure
---

### Post by DMKryl on 2010-11-28
hi, searching far and wide for a soccer game for linux (since pes2009 doesn't run with wine) i spotted a game called Linux Evolution Soccer* in this forum but the thread is too old, anyway i've downloaded the game,unpacked but it doesn't run.  maybe my laptop(acer aspire 4736z - ubuntu 10.10) isn't suited for the game or i'm doing something wrong? 

*[http://senior.ceng.metu.edu.tr/2010/kontrpiye/downloads.html](http://senior.ceng.metu.edu.tr/2010/kontrpiye/downloads.html)

---

### Post by Perfect Storm on 2010-11-28
Post the output of the actions you made and the terminal output.

---

### Post by DMKryl on 2010-11-29
kryl@Sasha:~/Desktop$ ls
0verkill-0.15  linuxDoukutsu-1.01  n_v1linux       SDL
f4l-0.2.1      linux-wbfs-manager  REC0002.WAV     wbfuse
LES            MPxConverterL (1)   Screenshot.png
kryl@Sasha:~/Desktop$ cd LES
kryl@Sasha:~/Desktop/LES$ ls
[COLOR="RoyalBlue"]ball[/COLOR]   [COLOR="RoyalBlue"]forma[/COLOR]      [COLOR="RoyalBlue"]image[/COLOR]     [COLOR="lime"]LES[/COLOR]  [COLOR="Lime"]Player.b3d[/COLOR]   [COLOR="RoyalBlue"]sound[/COLOR] 
[COLOR="RoyalBlue"]flag[/COLOR]   gmon.out   [COLOR="RoyalBlue"]include[/COLOR]   [COLOR="RoyalBlue"]lib[/COLOR]   [COLOR="RoyalBlue"]sky4[/COLOR]         [COLOR="RoyalBlue"]stadium[/COLOR]
kryl@Sasha:~/Desktop/LES$ LES
No command 'LES' found, did you mean:
 Command 'LS' from package 'sl' (universe)
LES: command not found
kryl@Sasha:~/Desktop/LES$ bash LES
LES: LES: cannot execute binary file
kryl@Sasha:~/Desktop/LES$

---

### Post by Perfect Storm on 2010-11-29
Right click on the binary file ---> Properties ---> Permissions

Set Allow executing file as a program.

```
./<binary>
```
eg. 
```
./LES
```

---

### Post by BigSilly on 2010-11-29
I'm no expert and I'm not wanting to put anyone off running the program, but looking at the schedule on the game's website I'm guessing the project's dead. It looks to be stuck in a very early stage.

I had some success running an old PES on WINE, though admittedly it wasn't perfect. I don't think PES 2009 runs too well as you say, but isn't 2010 supposed to be a bit better?

---

### Post by alaukikyo on 2010-11-29
You could use playonlinux it has automatic installation of of pes 2010

---

### Post by DMKryl on 2010-11-29
The file has the permit to execute as a program, pes 2010 doesn't run in my laptop T_T, I've already tried to run pes 6 w/o any luck,

**Terminal** 
kryl@Sasha:~/Desktop/LES$ ./LES
./LES: error while loading shared libraries: libIrrKlang.so: cannot open shared object file: No such file or directory
kryl@Sasha:~/Desktop/LES$

---

### Post by DMKryl on 2010-12-04
Finally i made the game work, idk if this is going to have a further development (i hope so), anyway i add the libraries if anyone want to try the game

---

### Post by DMKryl on 2010-12-04
forgot to upload the attachment

---

### Post by randolf_ambrose on 2010-12-23
> **DMKryl said:**
> forgot to upload the attachment

Can you tell me how did you manage to get it working, with these files???

i got the same result when i tried to run LES via terminal...

so... can you please tell how you did it??? step by step please???

thanks...

---

### Post by marl30 on 2010-12-24
If you desperately want to play a soccer game on Linux. Fifa 08 works perfectly in Wine. I have been playing it on Linux ever since I completely switched over.  I haven't tried any of the newer versions, as this is the only copy I own, so can't say that the others will work. 

The Wine site has Fifa 11 as gold and Platinum. This suggests that it also runs perfectly using Wine.

---

### Post by DMKryl on 2010-12-24
> **randolf_ambrose said:**
> Can you tell me how did you manage to get it working, with these files???

i got the same result when i tried to run LES via terminal...

so... can you please tell how you did it??? step by step please???

thanks...

well i copied those files to /usr/lib with sudo nautilus, and in the terminal i just ran the game

---

### Post by randolf_ambrose on 2010-12-25
> **marl30 said:**
> If you desperately want to play a soccer game on Linux. Fifa 08 works perfectly in Wine. I have been playing it on Linux ever since I completely switched over.  I haven't tried any of the newer versions, as this is the only copy I own, so can't say that the others will work. 

The Wine site has Fifa 11 as gold and Platinum. This suggests that it also runs perfectly using Wine.

So, you were able to apply the crack too??? or just ran the setup???
with daemon tools or something similar???

coz, the only windows s*** i have in my lucid is office 2007... so i dont know what its like to try games...

---

### Post by randolf_ambrose on 2010-12-25
> **DMKryl said:**
> well i copied those files to /usr/lib with sudo nautilus, and in the terminal i just ran the game

so you just copied the .so files to usr/lib and just ran LES from terminal???

my LES folder is in Desktop... i copied .so files to usr/lib but LES not working thru terminal... what to do???

---

### Post by DMKryl on 2010-12-25
i guess you have changed the properties of the les binary to executable, and put in the terminal ./LES, if that doesn't work show us the terminal output

---

