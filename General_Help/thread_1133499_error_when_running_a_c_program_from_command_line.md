---
title: "error when running a c program from command line"
date: 2009-04-23
forum: General Help
---

### Post by ubun_tut on 2009-04-23
hi,

i am trying to run a small c program from the terminal command line, by typing

./readraw.exe somthing.dat something_else.dat

where the second argument is the input data file and third argument is the name of the output data file. i get the following message error:

run-detectors: unable to find an interpreter for ./readraw.exe

can someone please tell me what this means?

thanks in advance!

---

### Post by Arndt on 2009-04-23
> **ubun_tut said:**
> hi,

i am trying to run a small c program from the terminal command line, by typing

./readraw.exe somthing.dat something_else.dat

where the second argument is the input data file and third argument is the name of the output data file. i get the following message error:

run-detectors: unable to find an interpreter for ./readraw.exe

can someone please tell me what this means?

thanks in advance!

Hard to say, but what does this command say?

```
$ file readraw.exe

```

It should tell you if it's an executable file, or something else. (It can't tell you that it comes from C, but that's no going to be important.)

---

### Post by ubun_tut on 2009-04-23
after typing in that command, it says

```

readraw.exe: MS-DOS executable PE  for MS Windows (console) Intel 80386 32-bit

```

i normally run the code on windows by using Xwin server + Xterm. now i am trying to run it in ubuntu...it should not be a problem right, since ubuntu can compile and execute c programs?

---

### Post by Arndt on 2009-04-23
> **ubun_tut said:**
> after typing in that command, it says

```

readraw.exe: MS-DOS executable PE  for MS Windows (console) Intel 80386 32-bit

```

i normally run the code on windows by using Xwin server + Xterm. now i am trying to run it in ubuntu...it should not be a problem right, since ubuntu can compile and execute c programs?

As far as I know, that's not possible at all. There exist emulators which allow you to run Windows programs under Linux, and perhaps the other way around. The program is likely to use operating system dependent calls for doing I/O, at least, and the very conventions for starting it (the part done before 'main' is called) are sure to differ. Still, it may be easier than I think, so perhaps someone else will answer something more positive.

If you have the source code, use gcc to compile and link on Ubuntu, then you can run it.

---

### Post by ubun_tut on 2009-04-23
hey thanks for the suggestion... it all works now after i re-compiled in ubuntu using gcc. haven't thought of going back to the source code.

---

