---
title: "what is segmentation fault?"
date: 2005-05-27
forum: Gaming &amp; Leisure
---

### Post by veritas366 on 2005-05-27
I'm on my second game now that has failed due to:

> Fatal signal: Segmentation Fault (SDL Parachute Deployed) 

First was a Robin Hood Demo...I installed that myself, so I didn't expect it to work.  But I just tried Penguin Command.  I got thru a bunch of levels and then it crashed to desktop with the above error.  What is a segmentation fault and how do you go about looking for the cause of the problem?

---

### Post by Sam on 2005-05-27
[Wikipedia is your friend](http://en.wikipedia.org/wiki/Segmentation_Fault) :wink:

---

### Post by veritas366 on 2005-05-27
Well, I had a general idea, but is there a way to find the offending file or part of the program?  The last part of that entry about the "backtrace" looked like maybe it was diagnostic in some way but I didn't know how to interpret it.

---

### Post by ltmon on 2005-05-27
You probably won't be able to interpret it without a good knowledge of the source of the program in question.  Even then, unless the source was compiled with debugging symbols (which they often aren't for releases as it slows things down a bit) the backtrace is pretty much useless.

Your best bet is to report a bug with the maintainer of Penguin Command (there is probably a bugzilla or mailing list).

L

---

### Post by meldroc on 2005-06-04
[QUOTE=ltmon]You probably won't be able to interpret it without a good knowledge of the source of the program in question.  Even then, unless the source was compiled with debugging symbols (which they often aren't for releases as it slows things down a bit) the backtrace is pretty much useless.

Your best bet is to report a bug with the maintainer of Penguin Command (there is probably a bugzilla or mailing list).

L[/QUOTE]
 It is possible to fix segfaults, though it takes a fair bit of programming knowledge.  Usually, what you do is you recompile the program with an option added to include debugging symbols.  Basically, that encodes the program's source code straight into the binary.

Then, you run your program in a debugger.  The standard tool is gdb, if you're curious, apt-get install gdb and gcc.  When your program dies with a segmentation fault, if you have core-dumps enabled, you'll end up with a core file - a memory dump of your program at the time of death.  You can then perform a post-mortem upon the core dump in gdb and run a backtrace, which will show you _exactly_ what line of code the system was executing when it died, along with a list of what functions called what functions with what parameters all the way up to main().  Then you start digging through source code to figure out what the program was trying to accomplish when it died at that line of code, and why it died.  Usually, the problem's fairly straightforward - dereferencing a null pointer, or trying to access a piece of memory that has been freed.

Quite handy actually.  If you're not familiar with a particular piece of source code, you can try compiling with debug symbols, try to reproduce the bug, and get a backtrace to email to the developers.  They like that.

---

