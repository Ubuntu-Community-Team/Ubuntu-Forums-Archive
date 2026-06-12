---
title: "GBA emulator"
date: 2006-04-08
forum: Gaming &amp; Leisure
---

### Post by Morbett on 2006-04-08
Is there a GBA emulator with a GUI ?  I installed VisualBoyAdvance but I can't find any tutorials on how to use it.

---

### Post by slipk487 on 2006-04-09
get gnomeboy advance and leave vba because gnomeboy is a gui program that uses the vba

---

### Post by Toxicity999 on 2006-04-11
I think its just:
visualbyadvance "whatever.gba" anyway... for future reference to playingg with undocumented applications... open up synaptic find the thing you installed... right click it>properties then goto the installed file tabs... look for somethign a in a bin directory... generally thats what you'll type to use it.

---

### Post by Toxicity999 on 2006-04-11
I think its just:
visualbyadvance "whatever.gba" anyway... for future reference to playingg with undocumented applications... open up synaptic find the thing you installed... right click it>properties then goto the installed file tabs... look for somethign a in a bin directory... generally thats what you'll type to use it.

Oh, then theres always man whatever... if you want a paradox use man man!

---

### Post by DoktorSeven on 2006-04-11
VisualBoyAdvance does have a GTK+ interface for it, but it's not enabled in the version in Universe.  

You can compile a version using GTK (sources are [here](http://sourceforge.net/project/showfiles.php?group_id=63889)) using **./configure --enable-gtk=2.0** (in the extracted directory, then **make** and **sudo make install**, assuming you've installed the necessary packages to compile programs).  You'll need at least libsdl, libgtkmm and libglademm (and the corresponding -dev package for each) to compile.  This willl get you the **gvba** binary which runs VBA in a GUI.

---

### Post by Adrian_b on 2006-04-11
I just did 'apt-get install visualboyadvance' and i can do gvba..
(gvba is WAY better then gnomeboyadvance, it's UI is exactly the same like the windows versions AND you can make it select .gb/.gbc's in it's browser)

---

### Post by fng on 2006-04-11
hmmm?
```
fng@butters:~/work/python$ sudo apt-get install visualboyadvance
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  visualboyadvance
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 355kB of archives.
After unpacking 1184kB of additional disk space will be used.
Get:1 [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) breezy/universe visualboyadvance 1.7.2-1build1 [355kB]
Fetched 355kB in 2s (121kB/s)

Preconfiguring packages ...
Selecting previously deselected package visualboyadvance.
(Reading database ... 117547 files and directories currently installed.)
Unpacking visualboyadvance (from .../visualboyadvance_1.7.2-1build1_i386.deb) ...
Setting up visualboyadvance (1.7.2-1build1) ...
fng@butters:~/work/python$ gvba
bash: gvba: command not found
fng@butters:~/work/python$ apt-file search gvba
fng@butters:~/work/python$
```

---

### Post by DoktorSeven on 2006-04-11
The VisualBoyAdvance from apt I have available doesn't give me gVBA either.  Is it in a special repository you added, or in Ubuntu 6.0x? (I run 5.10)

---

### Post by Denta on 2006-04-12
I have a problem with visualboyadvance using 100% of my cpu all the time, none of the builtin settings for frameskip and so on does help. Quite disturbing when  I have a 3600mhz proc with a noisy fan on high loads. It shouldn't need all that power... :-k

---

### Post by DoktorSeven on 2006-04-12
It always does that.  Since it only uses plain SDL it doesn't use direct rendering so it works the processor like mad.

Wish someone would make a GL-accelerated version (passing the onscreen drawing of the GBA screen to the video card instead of being done by the main CPU).  It'd certainly run VBA better on my older system.

---

### Post by Danielson1218 on 2006-06-03
I've been dying for that too. The windows version has opengl support and it flies. Im surprised it hasnt been added yet, i wish i knew how to do it myself.

---

### Post by Dryer Lint on 2006-06-04
I'm using Mednafen ([www.mednafen.com](www.mednafen.com)), which is a multi-system emulator that includes GBA emulation. It doesn't have a GUI, but it runs SO smooth. Extremely smooth.

---

### Post by kellogs on 2006-06-04
The version I used to use in windows was visual boy advance and used Direct draw rendering(accelerated 2d I think) but it used 100% cpu for sure and it was smooth. 
well, some demos were really slow. Is this emulator based on vba? I think in ubuntu if you havent got direct rendering activated it does it all by software hence slow emulation.

---

### Post by Bragador on 2006-08-07
-Warning, I'm a first week linux user-

Ok so I am tinkering with visual boy avance on my laptop and the graphics are good but the sound is jittering. You know, like when you want to talk and someone is hitting you really fast on your back or neck ?

So I don't know how to fix this. Perhpas this "mednafen" would be better. How does one install this "mednafen" you are all talking about. I can't find it in synaptic.

EDIT: User_Program helped me with mednafen. What a great community :mrgreen:

---

### Post by thenriques45 on 2006-09-25
I decide to run the Visual Boy Advance under Cedega. This solve the sound issue and allow me to use OpenGL, wich is supported on the windows version of emulator.


PS: Sorry by the english.

---

### Post by d16174l4n63l on 2008-02-11
the package for the gui is visualboyadvance-gtk you then use gvba to play.

Figured I would pass that along

---

### Post by heatblazer on 2008-02-12
Get VBA from synaptic. It works great and you can emulate GBC and GB games too... they run on 3x or 4x speed however

---

