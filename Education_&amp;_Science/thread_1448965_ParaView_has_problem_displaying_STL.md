---
title: "ParaView has problem displaying STL?"
date: 2010-04-07
forum: Education &amp; Science
---

### Post by lars.modig on 2010-04-07
Hi,

I just played around with a tutorial I got from a fellow, using Blender and a script to create a STL file that I then should use OpenFoam to calculate on.

The problem is that when opening the STL in paraview (by paraFoam) I cant see it, starting paraview alone doesn't help. But then I downloaded the latest paraview to my virtualbox with xp and copied over the stl file to my "shared" folder. And then it was working as it should. The stl file was clear and visible!

Anyone know about this problem? Could it be my graphical driver that is the issue ( I know their had been alot of problems with (i915) as I understand. Are their any fix?

I hope that someone could help, I really would like to get going with the tutorial again...

Br,
Lars

---

### Post by Azrael3000 on 2010-04-08
Can you send me the file via mail (I'll send you the address via note).

A few questions in the meantime
Did you compile parview yourself?
Did you launch it from the terminal? If yes are there any errors appearing in the terminal?

Best,
Arno

---

### Post by Azrael3000 on 2010-04-09
> Hi,

I used a script by Mads Reck that I found on the net ([http://ubuntuforums.org/showthread.php?t=1219156](http://ubuntuforums.org/showthread.php?t=1219156)), and it installed both OpenFoam and paraView. And yes I launch it from the terminal and ...(must check) no it actually doesn't display anything (the terminal)...

Is it possible to install paraview 3.6.2 to my configuration? (it's now running 3.6.1) Could that work or do you think it is the graphic drivers? I mean isn't it strange that it works from my VirtualBox XP?

Br,

Lars

Yeah I have installed PV 3.6.2 on my machine here. I had problems with crashes when using certain filters using the ubuntu version. So my suggestion to you is to get the sources and do a clean installation. It will take some time to compile but its worth it. If you need any help with compiling let me know. Since I have a compiled version you could send me the stl file and I'll check if it runs here. It would help to chase down the error.

BR,
Arno

**I'm talking nonsense above**
Sorry I misunderstood you. You are not actually using ParaView. Sorry about that.
So what can I do to help you. Well did you check the make.log which was produced by the script? Are there any errors occurring [post them here]? Did the foamInstallationTest yield any criticals?

---

### Post by lars.modig on 2010-04-10
Hi,

No you're not talking nonces... The OpenFoam works fine (at least I guess that it works fine but I have not seen the final result in paraView).

No what I have done is just used Suzane(the monkey) in blender and then exported it as a STL (I attach a part of it at the end so you can see if that looks alright...) via the script "Named ASCII STL" and as mention copied that to my VirtualBox I can view it in ParaView 3.6.2 for Windows (XP). 

So I would love to get your help in building the 3.6.2 from source and also integrate it to the openFoam environment (I.e. when I use the paraFoam command it starts paraview with the correct openfoam files loaded.)

Br,

Lars

```
solid Suzanne
facet normal 0.675752520561 -0.255332618952 0.691493868828
  outer loop
    vertex 0.453764170408 1.36665487289 0.939108848572
    vertex 0.429975390434 1.32974863052 0.948739409447
    vertex 0.450372010469 1.30157244205 0.918392241001
  endloop
endfacet
facet normal 0.675752520561 -0.255332618952 0.691493868828
  outer loop
    vertex 0.453764170408 1.36665487289 0.939108848572
    vertex 0.450372010469 1.30157244205 0.918392241001
    vertex 0.481386274099 1.34943509102 0.905768036842
  endloop
endfacet
facet normal 0.741133213043 -0.0931775718927 0.664860486984
  outer loop
    vertex 0.465661019087 1.40962064266 0.931732058525
    vertex 0.453764170408 1.36665487289 0.939108848572
    vertex 0.481386274099 1.34943509102 0.905768036842
  endloop
endfacet
facet normal 0.741133213043 -0.0931775718927 0.664860486984
  outer loop
    vertex 0.465661019087 1.40962064266 0.931732058525
    vertex 0.481386274099 1.34943509102 0.905768036842
    vertex 0.497058302164 1.40475714207 0.896187901497
  endloop
endfacet
facet normal 0.68932056427 -0.269486904144 0.672468602657
  outer loop
    vertex 0.481386274099 1.34943509102 0.905768036842
    vertex 0.450372010469 1.30157244205 0.918392241001
    vertex 0.474969506264 1.26841795444 0.87987858057
  endloop
endfacet
...
```

---

### Post by Azrael3000 on 2010-04-10
Hi Lars,

I installed the export script for Blender and exported Susanne. Loaded the file without any problems in ParaView 3.6.2. So far so good.

Now the problem is ParaFoam. I understand that it is ParaView with an extension the so called PV3FoamReader. However I'm not entirely sure how they are actually combined. Is the reader something that is additional to the PV source code? Or is it a program that can be compiled separately? If the later is true how is it actually linked to PV?

I will try to find out if you can't provide me the answers. But that'll probably be tomorrow.

BR,
Arno

P.S: It was funny in the thread where the export script is discussed I saw Mr. Pei. He had a mail conversation with me about a year ago. The world of CFD is small :)

---

### Post by lars.modig on 2010-04-10
Hi, sadly I cant help with the paraFoam things, I still see me as a newbie in the Ubuntu world and with the CFD I believe I'm not even a born yet...

But if you need some details from my computer or anything else please just ask. I'm right now actually installing the openFoam on on another computer running ubuntu in virtualBox. See if that works..

Br,

Lars

---

### Post by Azrael3000 on 2010-04-10
Ok so what I figure the most easiest way for now is the following:
Use openFoam to simulate your models. Then use a utility called FoamToVTK (should be included with openFoam, try to find it). VTK files can then be read from ParaView as it's its native format.

So assuming that you have openFoam up and running (as you said) and that you can find the FoamToVTK utility the only thing left is installing ParaView.
There is actually a pretty good tutorial on how to do this on the PV website: [http://paraview.org/Wiki/ParaView:Build_And_Install](http://paraview.org/Wiki/ParaView:Build_And_Install)
If you do everything in a new folder as described there you shouldn't have any problems. Be sure to have all the dependencies listed there (build essentials, cmake, qt...). If you experience any troubles let me know and I'll get you through. Also look out for any errors appearing that you don't understand. Google them or ask here. You don't have to sit in front of your computer though, it will take quite some time to finish :)

Good luck,
Arno

---

### Post by lars.modig on 2010-04-11
Hi, now it works!!!!

I found the issue here... [http://www.cfd-online.com/Forums/openfoam/74250-paraview-does-not-show-any-images.html](http://www.cfd-online.com/Forums/openfoam/74250-paraview-does-not-show-any-images.html)

Strange but you need to add ```
export LC_ALL=C 
``` in paraFoam file and then it works. I open paraview in a Foam case and then I can inlclude stl files and see them.

I add the complete reply by sebware so if someone else has the same failure as I they get the answer here also.

> Hey, i had the same problem with paraView and ubuntu karmic in former times.

paraView opens the files but don't show something in the 3d view.

the solution is very easy.

1. you must open the file

```
$/HOME/OpenFoam/OpenFoam-1.6/bin/paraFoam
```
2. you must add the following line to the the begin of the file. I put it after the header comments in the file.
```
export LC_ALL=C
```

I don't know the effect of this codeline, but it works.

have fun with paraFoam

Sebastian


Br,

Lars

---

### Post by Azrael3000 on 2010-04-11
Very nice. Good luck in starting your CFD career ;)

---

