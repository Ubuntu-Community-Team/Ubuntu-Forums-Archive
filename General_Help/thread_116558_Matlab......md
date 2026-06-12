---
title: "Matlab....."
date: 2006-01-13
forum: General Help
---

### Post by AgonxOC on 2006-01-13
I know there is MATLAB for Linux, but can I use my Windows copy in Linux also, or do I need a copy for Linux?

Alex

PS Also is there a way to tell the system temperature in Linux?

---

### Post by zappa86 on 2006-01-13
There is a program called octave that is similar. which is free. just make sure you have all your repositories enabled then do:
```
sudo apt-get install octave
```
and you should be good to go

---

### Post by kingsidy on 2006-01-13
i think that you need a copy for linux. I use it in linux, and it is actually faster than its windows counterpart.

---

### Post by AirIntake on 2006-01-13
You do need a separate Linux version. But no, it won't run any faster. At least, not usually. kingsidy must have a spiffy Ubuntu config or a bogged Windows config :)

---

### Post by AgonxOC on 2006-01-13
[QUOTE=zappa86]There is a program called octave that is similar. which is free. just make sure you have all your repositories enabled then do:
```
sudo apt-get install octave
```
and you should be good to go[/QUOTE]

What there is a program like MATLAB and its free..... Tell me more... give me a link to read about it..

So guys I should keep my Windows Copy then... Also my XP machine is 5X faster than this machine.. Only because of FS9.... 

Alex

---

### Post by mvaniersel on 2006-01-13
Try the [octave homepage]("http://www.octave.org/")

---

### Post by kingsidy on 2006-01-15
[QUOTE=AirIntake]You do need a separate Linux version. But no, it won't run any faster. At least, not usually. kingsidy must have a spiffy Ubuntu config or a bogged Windows config :)[/QUOTE]
 actually not but it takes longer to load in windows, much longer. I have a gig of ram and pentium M. In ubuntu it starts much faster.

---

### Post by astronerd on 2006-01-15
Not to jack this thread, but is there a mathematica substitue that is similar for linux?   I am learning mathematica for school and want something at home so I can practice and learn with.

---

### Post by mips on 2006-01-15
There is no free equivalent to Mathematica.

Mathematica is available for Linux. I think the student version is $140. They also have semester & anual licensed versions.

Depending on where you are studying the Linux version might be available to you for use. Some universities make the software available to their students in a legal way.

If you have a original Windows copy you might wanna contact Wolfram Research to discuss licensing for Linux.

You might want to have a look at MuPAD & Maxima. I dont know what your requirements are. As far as i know MuPAD is not free but you can obtain a 30 day trial license.

[http://maxima.sourceforge.net/](http://maxima.sourceforge.net/)
[https://www.mupad.de/](https://www.mupad.de/)

[http://gd.tuwien.ac.at:8050/A/0/](http://gd.tuwien.ac.at:8050/A/0/)
[http://gd.tuwien.ac.at:8050/A/1/](http://gd.tuwien.ac.at:8050/A/1/)
[http://gd.tuwien.ac.at:8050/A/2/](http://gd.tuwien.ac.at:8050/A/2/)
[http://gd.tuwien.ac.at:8050/A/3/](http://gd.tuwien.ac.at:8050/A/3/)
[http://gd.tuwien.ac.at:8050/A/4/](http://gd.tuwien.ac.at:8050/A/4/)

Maybe do some googling....

---

### Post by bagel on 2006-01-15
Since Mathematica is no longer available at my university, I'm using Maple on Linux. It is also commercial(I paid ~10-15 Euro at our universities software shop for a student version), but for me a sufficient Mathematica replacement

Ciao, bagel

---

### Post by mips on 2006-01-19
You can also try Scilab as a Matlab replacement.

[http://scilabsoft.inria.fr/](http://scilabsoft.inria.fr/)

[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

---

### Post by garba on 2006-01-19
[QUOTE=AgonxOC]I know there is MATLAB for Linux, but can I use my Windows copy in Linux also, or do I need a copy for Linux?

Alex

PS Also is there a way to tell the system temperature in Linux?[/QUOTE]

be forewarned, matlab on linux sports an usability which is close to zero, i had an horrible experience: troubles with printing, horrible motif interface, java core-dumping like there's no tomorrow, and VERY sluggish performance... perhaps it's just me but i find the windows version to be waaaaaay more comfortable.

Yep, it all boils down to loading the proper kernel modules for your monitoring hardware, lmsensors is quite good at finding out which i2c chip (if any) your mobo comes with, then you can probe the sensors by simply "catting" the proper file in /sys/bus/i2c/...

---

### Post by AgonxOC on 2006-01-23
[QUOTE=zappa86]There is a program called octave that is similar. which is free. just make sure you have all your repositories enabled then do:
```
sudo apt-get install octave
```
and you should be good to go[/QUOTE]

where is the link to OCTAVE..... I did the terminal install and I cannot find it.....

Alex


PS which is better MAPLE or MATHEMATICA?

---

### Post by earobinson on 2006-01-23
going to check this out when I get home, I use a lot of matlab at work, maybe they will let me go linux!

Whay about the matlab toolkits, If i buy one can I install it in octave?

---

### Post by jpkotta on 2006-01-23
It should be in your path...mine's in /usr/bin/.  If not do one of the following:
```
sudo updatedb; locate octave | grep "octave$"
```
or
```
find / -name octave -type f
```

Also, I recommend Octave over Scilab.  Octave's syntax is almost identical to Matlab's.  If you get some experience, there's no problem writing .m files to run in both.

If you install octave, you'll want octave-forge as well.  It has TONS of extra packages (albeit of lesser stability than the core distribution).

I second the statement that the Linux Matlab sucks interface-wise.  It does indeed start faster, though.

---

### Post by phen on 2006-01-23
you should be able to execute octave in a terminal. note that it has no graphical user interface. so you won'T find any menu items related to it. try scilab if you need an click...click..click interface!

about matlab on linux: our matlab runs on a many year old solaris station (around 200mhz) better than on a 2 year old windows machine. but not faster: calculations are faster on the newer machine - but writing to and reading from files is ridiculous slow on windows!

[https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

---

### Post by AgonxOC on 2006-01-23
Ok so where and how can I ADD a link (Icon)... to accesories


Alex

---

