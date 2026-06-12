---
title: "Matlab vs Octave"
date: 2011-07-08
forum: Education &amp; Science
---

### Post by tommpogg on 2011-07-08
Hi guys,

In many discussions and posts about Matlab people suggest to switch to Octave.
Now, I would like you guys to help me making a comparison.

In my opinion, these are the features of Matlab missing in Octave:

[LIST]
[*]It is very popular between the scientific community
[*]A lot of toolboxes to solve different problems are available
[*]Interfaces to numerical software written in C/C++
[*]it comes with Simulink
[/LIST]
 On the other hand, Octave is

[LIST]
[*]Free
[*]Open Source
[/LIST]

---

### Post by PC_load_letter on 2011-07-10
> **tommpogg said:**
> 
It is very popular between the scientific community

It doesn't matter because the syntax is almost identical. Almost any Matlab code will run under Octave with no or very little changes. Besides, I think Octave is gaining a lot of popularity due to it's being free & open-source. 

> 
A lot of toolboxes to solve different problems are available

Octave has a LOT of toolboxes as well, check the repos!

> 
Interfaces to numerical software written in C/C++

Octave does that too, check the SWIG project's Octave page: [http://www.swig.org/Doc1.3/Octave.html](http://www.swig.org/Doc1.3/Octave.html)
and
[http://wiki.octave.org/wiki.pl?CategoryExternal](http://wiki.octave.org/wiki.pl?CategoryExternal). 

> 
it comes with Simulink

True, and as of now I don't think Octave has an equivalent. In my case, I don't use Simulink at all, so it depends whether this is important to you or not.

My biggest beef with Matlab is that it costs an arm and a leg and if you get the student academic version, it comes with  certain limitations IIRC.

---

### Post by tommpogg on 2011-07-11
> **PC_load_letter said:**
> It doesn't matter because the syntax is almost identical. Almost any Matlab code will run under Octave with no or very little changes. Besides, I think Octave is gaining a lot of popularity due to it's being free & open-source. 

An "almost identical" syntax is handy if you have to port a few scripts and functions from Matlab to Octave. But I am afraid that porting a project with hundreds of m files would be a really hard task.

> **PC_load_letter said:**
> 
Octave has a LOT of toolboxes as well, check the repos!

Of course it is possible to find equivalent toolboxes in the repositories.
Nevertheless, a lot of useful (free) stuff has been developed for Matlab only (e.g. optimisation tools like [YALMIP]("http://users.isy.liu.se/johanl/yalmip/pmwiki.php?n=Main.WhatIsYALMIP"), control toolboxes like [MPT]("http://control.ee.ethz.ch/%7Empt/") and many more).
You still have to pay for the Matlab license, which is expensive.

By the way, if someone could tell me a way to run YALMIP and MPT on Octave, I would be happy.

> **PC_load_letter said:**
> 
Octave does that too, check the SWIG project's Octave page: [http://www.swig.org/Doc1.3/Octave.html](http://www.swig.org/Doc1.3/Octave.html)
and
[http://wiki.octave.org/wiki.pl?CategoryExternal](http://wiki.octave.org/wiki.pl?CategoryExternal).

Thank you, I'll take a look.

> **PC_load_letter said:**
> 
My biggest beef with Matlab is that it costs an arm and a leg and if you get the student academic version, it comes with  certain limitations IIRC.

True. This is definitively the weakest point of Matlab.

---

### Post by Random_Dude on 2011-07-11
The Matlab GUI is very good, it's something that Octave also lacks.

> **PC_load_letter said:**
> 
My biggest beef with Matlab is that it costs an arm and a leg and if you get the student academic version, it comes with  certain limitations IIRC.
If you are short, they also ask for one kidney.

Cheers :cool:

---

### Post by PC_load_letter on 2011-07-12
> **Random_Dude said:**
> The Matlab GUI is very good, it's something that Octave also lacks.


There is QToctave in the repos, it may not be as feature rich as Matlab (I say not as bloated) but you may like it more than the terminal.

I don't use Matlab GUI, the editor (at least in the version installed at work) is a nightmare. So I use Geany to edit the m.files and "matlab -nodesktop -nosplash" in terminal.

> 
If you are short, they also ask for one kidney.
Cheers :cool:

LOL

---

### Post by PC_load_letter on 2011-07-12
Another thing to mention so to be completely fair. Octave does have a few more bugs than you might find in Matlab, but the good news is you can always send an email to the dev team and you could get a batch to fix the problem, you'll then have to batch the source, compile, and reinstall..etc. 

In my line of work, I recently stumbled upon a very serious bug in Octave 3.2. Simply, you may sometimes get a wrong answer when numerically integrating certain functions over certain intervals with **quadgk**. The devs knew about it when I emailed them and sent me the link to download a fixing batch. YMMMV in a situation like this, so you may want to stick with Matlab for the mission critical projects.

---

### Post by Random_Dude on 2011-07-12
> **PC_load_letter said:**
> There is QToctave in the repos, it may not be as feature rich as Matlab (I say not as bloated) but you may like it more than the terminal.


I didn't know there was a GUI for Octave, I've got to give it a try. :o

Cheers :cool:

EDIT:
I've done some googling and I found another Octave GUI, this one seems similar to the MATLAB GUI.
[http://sites.google.com/site/guioctave/screenshots](http://sites.google.com/site/guioctave/screenshots)

---

### Post by PC_load_letter on 2011-07-13
Looks nice, but it's a Windows only app, so I'm out of luck :D
On their forum page, the dev says that the software utilizes Microsoft Foundation classes, which I guess it means there is no way it gets ported to Linux (or OSX). 

QToctave is pretty good IMO and it's already in the repos. There is also KOctave but I don't have any experience with it.

---

### Post by Random_Dude on 2011-07-13
> **PC_load_letter said:**
> Looks nice, but it's a Windows only app, so I'm out of luck :D
On their forum page, the dev says that the software utilizes Microsoft Foundation classes, which I guess it means there is no way it gets ported to Linux (or OSX).

Damn I didn't notice that. That's too bad.
Well I'll give QToctave a chance when I get the time.

Cheers :cool:

---

