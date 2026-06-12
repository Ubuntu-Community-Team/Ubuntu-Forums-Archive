---
title: "glchess doesn't start"
date: 2008-12-13
forum: General Help
---

### Post by RoseKnight on 2008-12-13
recently switched my laptop to ubuntu after a HD wipe.

I just installed the driver for my ati x300 video card. And wanted to test it using the chess game in 3D.

The game gave me this: "no python-openGL support" (common bug I guess)
(that error where you have to install 2-3 different openGL variations for it to go away."

I had to do this to make it go away:

```

sudo apt-get install python-opengl
sudo apt-get install libgtkglext1 
sudo apt-get install python-gtkglext1

```

after that and a reboot, the glChess will display "Starting Chess" in the taskbar and then disappear.
So I wen to the terminal and ran

```

glChess

```

which out-put's this:

```

The program 'glchess' recieved an X Window System error.
This probably reflects a bug in the program
The error was 'BadRequest (invalid request code or no such operation)'.
(Details: serial 108 error_code 1 request_code 143 minor_code 10)
(note to programmers: (ommited note to programmers))

```

help is much appreciated!

---

### Post by RoseKnight on 2008-12-13
Almost forgot, I'm using ubuntu 8.10 (intrepid).

And one more note, it seems that the "python-gtkglext1" is causing the problem, I removed it and chess works (but no 3D) I add it and chess doesn't work.

---

### Post by RoseKnight on 2008-12-14
I'm guessing this is an openGL or python update thing, thats what I've been reading.

Anyone have any ideas?

---

### Post by jukzh on 2009-06-06
Hello!
Before installing python-opengl python-gtklext1 chess worked(not in 3D)
Now I want play
```

$ glchess 
Traceback (most recent call last):
  File "/usr/games/glchess", line 16, in <module>
    import pygtk
ImportError: No module named pygtk

```
Help me please, what does it means? 
Regards,

JK

---

