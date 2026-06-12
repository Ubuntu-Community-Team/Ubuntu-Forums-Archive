---
title: "An error occurred while loading the archive"
date: 2009-07-05
forum: Desktop Environments
---

### Post by Vadim vanZant on 2009-07-05
[/home/vadim/Documents/Downloads/FlyffUsaSetupXFire.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/vadim/Documents/Downloads/FlyffUsaSetupXFire.exe or
          /home/vadim/Documents/Downloads/FlyffUsaSetupXFire.exe.zip, and cannot find /home/vadim/Documents/Downloads/FlyffUsaSetupXFire.exe.ZIP, period.

This popped up on Archive Manager when I tried to run an .exe. Can anyone help me a little bit and explain to me how to fix this. I would like to get this install working.

---

### Post by ajgreeny on 2009-07-05
Firstly, you can't run an exe file without wine or another "emulation" package to do so.

Secondly, it seems fromthe error that this .exe is possibly a self extracting zip file, and it may also possibly need another part of the total in order to work at all.

More info is needed about the file; where did it came from, what it is supposed to be, ie, what do you think it should end up doing, and lastly, do you fully trust it, or the producer of it?

OK, I see it is a windows game.  Do you know if it will run in wine or another of the "emulators", eg crossover, cedega or other?

---

