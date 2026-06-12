---
title: "Benchmark Wiki"
date: 2006-01-07
forum: Gaming &amp; Leisure
---

### Post by smoon on 2006-01-07
Hi all!

Since every now and then someone asks for benchmarking software for linux and the most common answer is he should try glxgears, I recently decided to set up a wiki that describes different methods of how one can benchmark his system. Every benchmarks page includes a section where results can be posted. Currently there a pages about Wolfenstein Enemy Territory, Nexuiz and nbench along with some other pages explaining common things like how to get information about the systems hardware. You can find the wiki at [http://nooms.de/benchwiki/](http://nooms.de/benchwiki/), maybe someone finds it useful. And please feel free to contribute in any form, it's a wiki!

---

### Post by Perfect Storm on 2006-01-07
You might add this: [http://www.unrealmark.net/](http://www.unrealmark.net/)

---

### Post by dsierpin on 2006-01-14
Hey all-

Dumb question, I want to know how my video card is doing.  I tried using the benchmarking tool glxgears, but I guess I'm not doing it right.  I get a little window with some turning gears.  I let it sit there for a few hours, but I don't get any information on how fast it's displaying frames.  How can I get this to work?  :confused: 

Thanks in advance.

---

### Post by curuxz on 2006-01-14
[QUOTE=dsierpin]Hey all-

Dumb question, I want to know how my video card is doing.  I tried using the benchmarking tool glxgears, but I guess I'm not doing it right.  I get a little window with some turning gears.  I let it sit there for a few hours, but I don't get any information on how fast it's displaying frames.  How can I get this to work?  :confused: 

Thanks in advance,

dsierpin[/QUOTE]

lol....all it does is give you an FPS reading (should be in the corner). I hope you did not watch while it ran for a few hours :S

---

### Post by dsierpin on 2006-01-14
> lol....all it does is give you an FPS reading (should be in the corner). I hope you did not watch while it ran for a few hours :S


oops......I'll take a look.  Thanks for the quick reply!

---

### Post by TheForumTroll on 2006-01-14
[QUOTE=curuxz]lol....all it does is give you an FPS reading (should be in the corner). I hope you did not watch while it ran for a few hours :S[/QUOTE]

At my machine its in the console behind it.
And remember its "glxgears -printfps" now :rolleyes:

---

### Post by handy on 2006-01-15
If you add this alias, to the bottom of your **/etc/bash.bashrc** file:

alias glxgears='glxgears -printfps'

You will see the fps output in your bash terminal everytime you run **glxgears**.

No need for the -printfps argument anymore! :D

---

### Post by mcduck on 2006-01-15
There is also Linux version of superpi.. Running a 1M or 8M test works nice as CPU benchmark :D 

[http://www.xtremeresources.com/forums/showthread.php?t=35790]("http://www.xtremeresources.com/forums/showthread.php?t=35790")

edit: for glxgears I prefer 'glxgears -iacknowledgethatthistoolisnotabenchmark'. It's easier to remember ;)

---

### Post by dsierpin on 2006-01-15
Thanks everyone, got my video card up to a screaming 600 fps (it does 9000 in Windows).  I suppose I'm not using the right drivers.  I've messed around a bit and found that the latest ATI driver works the best (makes sense given my ATI Radeon Xpress 200M video card), but it's still pretty terrible.  I'll keep messing with it.  Forum search reveals that this is an issue with the card I have.  Thanks again!

---

