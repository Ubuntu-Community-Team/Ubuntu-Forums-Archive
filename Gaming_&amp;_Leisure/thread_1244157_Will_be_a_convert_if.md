---
title: "Will be a convert if"
date: 2009-08-19
forum: Gaming &amp; Leisure
---

### Post by meatspaceman on 2009-08-19
I am assured i can do the following

-Play quake live.

-Overclock my usb to a stable 500hz(mouse: imo 1.1a).

-Completely remove mouse acceleration. 

-My monitor will refresh at 120hz in game, this is an issue in windows that is solved by 
refreshlock. Im not sure it applies to linux.

-Use my sound card and have positional audio work(SB-Xfi [EC00] v5.5).

-I have had issues with missing mouse clicks, would a real time kernel solve this problem? Is it a problem at all?

-An equivalent of the ASUS Epu-6 engine would be nice, so i can turn down case fans, but this is not critical.

If this is all possible short of writing my own code, i will be a very happy man.

Thank you.

---

### Post by meatspaceman on 2009-08-19
did i do something taboo

---

### Post by Bölvaður on 2009-08-19
> **meatspaceman said:**
> 
-Play quake live.

use the standard firefox that comes with the installation, not all newer (unstable/testing) are supported by the quake live website. 



> **meatspaceman said:**
> 
-My monitor will refresh at 120hz in game, this is an issue in windows that is solved by 
refreshlock. Im not sure it applies to linux.

It is just 1 line you will have to write in xorg.conf, check out the link to get idea how to accomplish this.
[http://ubuntuforums.org/archive/index.php/t-83973.html]("http://ubuntuforums.org/archive/index.php/t-83973.html")


> **meatspaceman said:**
> 
-I have had issues with missing mouse clicks, would a real time kernel solve this problem? Is it a problem at all?


That could be what you'd need.
But you can also alter and compile the kernel your self with more suitable configuration.



Please google the solutions of the other problems I couldn't answer at the moment.

---

### Post by juancarlospaco on 2009-08-19
Theres a Script to control fan speeds.
*Search the forum...*
:)

---

### Post by sempronius on 2009-08-19
> **meatspaceman said:**
> I am assured i can do the following

-Play quake live.


Yes, it works for me, though on my not so up to date hardware fps is rather low compared to the stand-alone game quake3.

> 
-Overclock my usb to a stable 500hz(mouse: imo 1.1a).


My main mouse is the same: MS Intellimouse Optical 1.1A, excellent mouse in my opinion.

Overclocking the usb port to stable 500 hertz is easy.


> 
-Completely remove mouse acceleration. 


Hm, I think so. At least, I don't experience problems that appear to be related to acceleration. My issues are different ones (see below).

> 
-My monitor will refresh at 120hz in game, this is an issue in windows that is solved by 
refreshlock. Im not sure it applies to linux.


CRT monitor? If the monitor supports 120 hertz, this should be possible in Linux, too.

> 
-Use my sound card and have positional audio work(SB-Xfi [EC00] v5.5).


I don't have a clue.

> 
-I have had issues with missing mouse clicks, would a real time kernel solve this problem? Is it a problem at all?


BINGO! (in a negative way, though)!

Another Linux user who talks about this annoyance - did you read my thread before? ;-)

As to the suggestion of real-time kernels:
I am not convinced this will help a lot...
Well, actually, to a degree, maybe.

But my current kernel is a self-compiled kernel with all kinds of real-time settings enabled. In the past, I used kernels with Ingo Molnar's real-time patches.

But it does not seem to matter:
I have several kernels here that I can boot from: RT enabled ones and others: the problem with lost mouse clicks has happened with all of them, if I am not mistaken... :-(

> 
-An equivalent of the ASUS Epu-6 engine would be nice, so i can turn down case fans, but this is not critical.

If this is all possible short of writing my own code, i will be a very happy man.

Thank you.

Part of it is, as I wrote.


sempronius

---

