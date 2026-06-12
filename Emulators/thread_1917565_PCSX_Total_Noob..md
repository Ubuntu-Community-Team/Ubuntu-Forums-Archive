---
title: "PCSX Total Noob."
date: 2012-01-30
forum: Emulators
---

### Post by chulex67 on 2012-01-30
So i got Pcsx runing but iam having 2 problems.

1.- I cant Save game in memory card but i can save them wth f1 and load them with f3.

2.- Cant Convert ECM files to Bin or Iso.

I go to terminal and write

UNECM Einhander [NTSC-U] [SCUS-94243].img.ecm   Then i Press Enter and i Get this error or this

usage: unecm ecmfile (outputfile) 

after this i really dont know what to do lol. 

HALP

---

### Post by satanselbow on 2012-01-30
> **chulex67 said:**
> 

2.- Cant Convert ECM files to Bin or Iso.

I go to terminal and write

UNECM Einhander [NTSC-U] [SCUS-94243].img.ecm   Then i Press Enter and i Get this error or this

usage: unecm ecmfile (outputfile) 

after this i really dont know what to do lol. 

HALP

You need to provide the full path to your file and put it in single quotes due to the spaces in the filename ;)


unecm '~/myPSXroms/Einhander [NTSC-U] [SCUS-94243].img.ecm'

Change the location of your memorycard folders to somewhere under your home folder as you may not have the correct permissions to save where they are at present.

---

### Post by chulex67 on 2012-01-31
Moving Folder under Home, Fixed the Memory Card Problem Thx.

Here is a kitty for u : [http://www.cutecats.com/fuzzball.html](http://www.cutecats.com/fuzzball.html)

I cant work with ecm =( here is the error.


luis@luis-Vostro-1320:~$ unecm '~/Mypsxrooms/Einhander [NTSC-U] [SCUS-94243].img.ecm'
UNECM - Decoder for Error Code Modeler format v1.0
Copyright (C) 2002 Neill Corlett

Decoding ~/Mypsxrooms/Einhander [NTSC-U] [SCUS-94243].img.ecm to ~/Mypsxrooms/Einhander [NTSC-U] [SCUS-94243].img.
~/Mypsxrooms/Einhander [NTSC-U] [SCUS-94243].img.ecm: No such file or directory

The folder is In the Desktop inside a folder called Mypsxrooms. I know im doing something wrong.

---

### Post by satanselbow on 2012-01-31
you will need to incude ' Desktop' in your path.

open a terminal and type unecm followed by a space 

navigate to the folder with your .iso.ecm file in it and drag n drop it into the terminal

that will ensure the path is correct :popcorn:

---

### Post by chulex67 on 2012-01-31
Thank you Master. Now i see the Terminal  and I was supposed to write this

unecm '/home/luis/Desktop/MyPsxroms/Einhander [NTSC-U] [SCUS-94243].img.ecm' 


Now i Understand.  So easy just needed to Specify The Path Of the File, Lol. Have been using Ubuntu for 3 days now, Is Freaking Awesome but i still have alot to Learn. 

Thank you you Solved All my Problems =)

---

### Post by satanselbow on 2012-02-01
Glad to help ;)

It would make the forum a better place (slightly ;) ) if you could mark your orginal post as [SOLVED] and maybe change the title to something more description - such as "Psx ISO unecm Path Problem" - so that anyone else with the same trouble might find the solution easily ;)

---

