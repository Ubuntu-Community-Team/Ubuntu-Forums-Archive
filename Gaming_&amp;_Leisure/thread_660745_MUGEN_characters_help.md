---
title: "MUGEN characters help"
date: 2008-01-07
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2008-01-07
I have about 1000 characters from the windows version of MUGEN.
I moved them all to the Linux MUGEN version and I have edited the select.def file to include some of the characters and stages, but MUGEN just quit after I select the new characters, with different errors for each character...

examples : 

```
maxim@maxim-ubuntu:~/maxddark/games/mugen$ ./mugen
Loading button config for P1 joystick.
Loading button config for P2 joystick.
Initializing keyboard.
Initializing sound...no midi device found.
Initializing graphics.
Error message: Can't load DarkW.act
Error loading chars/00DarkW/00DarkW.def
Error loading p1

Library error message: Can't access group scenedef
Cutscene error reading ./chars/00DarkW//

```

```
maxim@maxim-ubuntu:~/maxddark/games/mugen$ ./mugen
Loading button config for P1 joystick.
Loading button config for P2 joystick.
Initializing keyboard.
Initializing sound...no midi device found.
Initializing graphics.
Error message: Can't load 00G_rugal.snd
Error loading chars/00G_rugal/00G_rugal.def
Error loading p1

Library error message: Can't access group scenedef
Cutscene error reading ./chars/00G_rugal//

```

```
maxim@maxim-ubuntu:~/maxddark/games/mugen$ ./mugen
Loading button config for P1 joystick.
Loading button config for P2 joystick.
Initializing keyboard.
Initializing sound...no midi device found.
Initializing graphics.
Error message: 
Error in AI.st
Character needs to be updated. See docs/incompt*.txt.
Error loading chars/Ace/Ace.def
Error while precaching
Error loading storyboard: chars/Ace//
Error in AI.st
Character needs to be updated. See docs/incompt*.txt.
Error loading chars/Ace/Ace.def
Error while precaching
Error in AI.st
Character needs to be updated. See docs/incompt*.txt.
Error loading chars/Ace/Ace.def
Error loading p1

Library error message: Can't access group scenedef
Cutscene error reading ./chars/Ace//

```

and so on...
I got 1000 characters and fixing just afew won't do.
I need a global fix for them all.

What is wrong ?
How can I fix it ?

P.S
MUGEN is running in debug mode for some reason, how can I disable debugging ?

---

### Post by Vamp381 on 2008-02-02
Same problem ;< Help anybody ?

---

### Post by Perfect Storm on 2008-02-02
Perhaps it can't handle the character file because it contains upper-letter in the linux version.
(I had simiilar cases but with NWN).

---

### Post by mister_k81 on 2008-02-04
> **Artificial Intelligence said:**
> Perhaps it can't handle the character file because it contains upper-letter in the linux version.
(I had simiilar cases but with NWN).

Sort of. The Linux version of Mugen is  case sensitive, so you have to make sure that the definitions in the .def file match up properly with the character files.

for example, looking at this error here that was posted above: 

```

Character needs to be updated. See docs/incompt*.txt.
Error loading chars/Ace/Ace.def
Error while precaching
Error loading storyboard: chars/Ace//
Error in AI.st

```

Make sure that the Ace/Ace.def file in your chars folder is actually named Ace.def, and not something like ACE.DEF or ace.def. Also, you might want to open up the character .def files and make sure that the definitions match up with the character files that they come with.   

[QUOTE=MaximB]P.S
MUGEN is running in debug mode for some reason, how can I disable debugging ?[/quote]

Look for the system.def file located in your mugen/data/ directory and open it in text editor or whatever you use. Then do a search for this entry: 

```

debuginfo = 1

```

and change the one to a zero. That should turn debug mode off.

---

### Post by Auriono on 2008-02-24
That's odd, I'm having this problem too. Perhaps it's something in the Ubuntu coding since when I ran Winmugen using WINE, I get the same results.

---

### Post by jimmhoo on 2008-10-11
the problem is because ubutu/linux is case sensitive

I was having the same problem with goeniko2

you can rename all file names to lowercase but wont help until the <charname>.def have the same filenames 

for example in my case I opened /home/<username>/mugen/chars/goeniko2/goeniko2.def

and renamed the files in the directory as they are in the .def

if say .ACE, rename to .ace

if say NGoeniko.cns, open goeniko.def and check if thats the correct name if not rename it 

you can either rename all files as they are in .def or rename the files on the.def

that should do the trick


I use mugen for linux, "winmugen" don't work with wine in my pc, but I think that also corrects the wine problem  


sorry for my bad english

---

