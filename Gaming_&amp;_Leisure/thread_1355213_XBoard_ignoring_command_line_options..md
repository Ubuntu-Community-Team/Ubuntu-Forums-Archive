---
title: "XBoard ignoring command line options."
date: 2009-12-14
forum: Gaming &amp; Leisure
---

### Post by jwbrase on 2009-12-14
I installed XBoard because, while I'm not a big time chess enthusiast the Synaptic description mentioned that it supported several variants that, when I looked them up on Wikipedia, looked interesting. Unfortunately, GNU Chess 5.07 doesn't seem to support any of those variants, and, despite the fact that I have installed several other chess engines, I cannot find any way to change the chess engine from the GUI, and the program is not responding to any of the command line options documented in its man page for controlling which engine to run with, such as -fcp, -scp, and -ncp. In fact, it is not responding to *any* command line options whatsoever. It's not even outputting errors when given bad options. It simply runs, without errors, using GNU Chess 5.07 as its engine, and ignores everything on the command line following the call to xboard itself.

The following commands all appear to have identical results:

```
xboard
xboard -fcp crafty
xboard -fcp fairymax
xboard -ncp
xboard qwertyuiop
```

---

### Post by Jimtuv on 2010-01-02
I have the same problem. Hope to see a solution to this.

---

### Post by Jimtuv on 2010-01-02
Just found the solution. Here it is. You wont believe how simple it is.

instead of this:

```
xboard -fcp fairymax
xboard -fcp crafty

```

This is what works:

```
xboard.real -fcp fairymax
xboard.real -fcp crafty
```

Hope this helps you out. :)

---

