---
title: "Does anyone use VICE?"
date: 2008-05-24
forum: Gaming &amp; Leisure
---

### Post by Despot Despondency on 2008-05-24
Hey. I've installed VICE, I think correctly. and have a copy of a game I want to play, but I don't know how to load it. It's an old commodore game. 

Once I've loaded VICE I take it I select -> attach a disk image, and then select the D64 file and press enter. What do I do after that? I know it's a really stupid question, but I've never used an emulator before? Cheers in advance.

---

### Post by anjilslaire on 2008-05-24
I use VICE on my PSP. When I load the image, the game just starts. Haven't used it on a PC in ages...

---

### Post by Grishka on 2008-05-24
just double click the file. it should boot up automatically. if not, you'll have to use the Commodore method, if I remember correctly, that was something along the lines of: "load" for games on tape and "load "*",8" for disk games.

---

### Post by Despot Despondency on 2008-05-24
Hey, thanks for your responses. I got it to work this time. I use the autostart option. Window seems to be really small though, so I'm going to have to sort that out.

---

### Post by anjilslaire on 2008-05-24
ah I remember the old days
load "*",8,1

There may be a resolution or screensize option buried in there somewhere...

---

### Post by Despot Despondency on 2008-05-24
OK, next stupid question. How do I maximize the screen? At the moment it's got a thick black border, so the actual graphics of the game are really small. Can't seem to find anything about it.

---

### Post by Grishka on 2008-05-24
> **Despot Despondency said:**
> OK, next stupid question. How do I maximize the screen? At the moment it's got a thick black border, so the actual graphics of the game are really small. Can't seem to find anything about it.

check out the options in VIC-II settings.

---

### Post by Despot Despondency on 2008-05-24
I've already put it on double size, but it's still got a large black border. Are there any other options under the VIC-II settings that I should change?

---

### Post by Grishka on 2008-05-24
> **Despot Despondency said:**
> I've already put it on double size, but it's still got a large black border. Are there any other options under the VIC-II settings that I should change?

you could try the fullscreen modes, but they don't work quite like they should. otherwise, the only other option that I'm aware of would be changing your desktop resolution.

---

### Post by Despot Despondency on 2008-05-25
Thanks for your response Grishka. How exactly do I put it on full screen mode?

---

### Post by Despot Despondency on 2008-05-25
OK, I may as well ask another question while I'm at it. How do I change the focus on the mouse once I've got the game loaded, i.e. how do I get it so that the drop down menus stop appearing when I click a mouse button and it recognizes that I'm selecting part of the screen instead? Also any good howto's on the basic stuff about VICE would be good. Don't seem to able to find any. Not that I can understand anyway.

---

### Post by Robin T Cox on 2008-05-25
> Also any good howto's on the basic stuff about VICE would be good.

There's lots of info here:
[http://www.viceteam.org/]("http://www.viceteam.org/")

and a VICE manual here:
[http://www.viceteam.org/vice_toc.html]("http://www.viceteam.org/vice_toc.html")

---

### Post by Despot Despondency on 2008-05-25
Cheers, I found those before but there's not a lot on how to actually set stuff up. Was looking for more of a tutorial on how to set up your keyboard and joystick etc.

---

### Post by Grishka on 2008-05-25
> **Despot Despondency said:**
> OK, I may as well ask another question while I'm at it. How do I change the focus on the mouse once I've got the game loaded, i.e. how do I get it so that the drop down menus stop appearing when I click a mouse button and it recognizes that I'm selecting part of the screen instead? Also any good howto's on the basic stuff about VICE would be good. Don't seem to able to find any. Not that I can understand anyway.

man, did you even look at the options? it's under Options/1351 mouse emulation/enable mouse. as for fullscreen modes, try clicking "fullscreen" and "fullscreen options". this just might do something. and here's a VICE manual: [http://www.viceteam.org/vice_toc.html](http://www.viceteam.org/vice_toc.html).

---

### Post by Despot Despondency on 2008-05-25
Well I must have different version to you because mine doesn't have a full screen option. Obviously I would have tried it otherwise. 

As for mouse emulation I have already tried that option and all it did was make the pointer invisible, not turn off the options menu I was talking about. 

I already have that manual but didn't find it particularly readable, especially as I never used an emulator before.

---

### Post by Grishka on 2008-05-25
> **Despot Despondency said:**
> Well I must have different version to you because mine doesn't have a full screen option. Obviously I would have tried it otherwise. 

As for mouse emulation I have already tried that option and all it did was make the pointer invisible, not turn off the options menu I was talking about. 

I already have that manual but didn't find it particularly readable, especially as I never used an emulator before.

I see, that's alright then. sorry for being harsh. mouse emulation should work well, try alt+m. for fullscreen mode, try alt+d. if it doesn't work, perhaps something's wrong with your version of VICE. what version do you have, then? installed it from where?

---

### Post by chochem on 2008-06-25
Does anyone know how to fix the problem when you smart-attach an image and it apparently loads quite correctly but doesn't do anything? As in the screenshot below:

[[IMG]http://pics.viharpander.dk/scrot/viceproblem-thumb.png[/IMG]](http://pics.viharpander.dk/scrot/viceproblem.png)

My C64 syntax is a little rusty so I pretty much just rely on the smartattach feature...

---

### Post by DoktorSeven on 2008-06-25
> **chochem said:**
> Does anyone know how to fix the problem when you smart-attach an image and it apparently loads quite correctly but doesn't do anything? As in the screenshot below:

My C64 syntax is a little rusty so I pretty much just rely on the smartattach feature...
Try the same command as it did (should be able to move the cursor up to it and edit it, then press return over it) except remove the last **,1**

Then do **RUN**

It could also be something else entirely -- it could have loaded a machine language program somewhere, so for this you'll just have to see if there's any instructions or something to run it.

---

### Post by chochem on 2008-06-25
Thanks for the suggestions. I tried repeating the 'LOAD' command line and then entering/repeating the RUN command. First part simple produced the same output as first time, the second part returned a syntax error (both with and without the semi-colon).

As for the other suggestion... Maybe I misunderstand you but surely 'Spy Hunter' is a rather crude car chase/shoot'em'up mashup and not a programming language... :confused:

---

### Post by RIchard James13 on 2008-06-25
> **chochem said:**
> As for the other suggestion... Maybe I misunderstand you but surely 'Spy Hunter' is a rather crude car chase/shoot'em'up mashup and not a programming language... :confused:

It is a car chase game but...

The early commodore series PET VIC C64 could not load machine code straight from the floppy drive only BASIC programs (unless you used a special trick). Cartridges could do this though. In order to get around this problem the programmers of the day made two programs one loads the machine code and then runs it and the other is the machine code game itself. 

Now there are several different ways to do that, one is to encode the program behind the BASIC program and save that to the disk as a whole, so that when you load the program the machine code is loaded into memory and then the BASIC portion at the start is executed and in turn executes the machine code.

The other way is to make the BASIC program load the machine code into RAM by either reading data statements or reading from the disk. Then the BASIC program executes the machine code.

Sometimes for some programs you have to start the machine code program manually by using the BASIC sys command. sys will start executing machine code at the location specified in decimal. Some programs might have documentation that says sys 346327 or similar. That will make the machine code execute.

As for your program I think the problem might be it is loading the wrong file off the disk.

To get the C64 to load the first program on the disk and run it type
```
load "*",8,1
```
* is a wildcard and finds the first program on the floppy disk. 8 is the number of the floppy drive. 1 means run this program after it loads.

To look at the directory of a disk type
```
load "$",8
```

from that type list and it will show all the entries on the disk. Each entry is inserted into a BASIC program and given a line number but the filename is inserted between two quotes "thefileyouwant".Line number 0 gives you the label of the disk, it is not a filename. You can load a file by doing the following command. Note insert the right filename I just made up "thefileyouwant"
```
load "thefileyouwant",8,1
```

so you might go through a process like this
```
LOAD "$",8
LIST
0 "LABEL OF DISK"
10 "PROGRAMYOUWANT"
20 "SOMEDATA"
258 BLOCKS FREE.
LOAD "PROGRAMYOUWANT",8,1
```

might even be
```
LOAD "$",8
LIST
0 "LABEL OF DISK"
10 "AUTOLOADER"
20 "PROGRAMYOUWANT"
30 "SOMEDATA"
258 BLOCKS FREE.
LOAD "AUTOLOADER",8,1
```

and some disks have multiple programs
```
LOAD "$",8
LIST
0 "LABEL OF DISK"
10 "GAME1"
20 "GAME2"
30 "GAME3"
258 BLOCKS FREE.
LOAD "GAME2",8,1
```


and that should run your game (note you only typed 3 lines LOAD, LIST, LOAD

If that fails your disk may be corrupt, it might not be a disk image could be a cartridge?

---

### Post by chochem on 2008-06-26
Thanks for that explanation - I was searching for something like that but didn't find anything. I'll give it a go, see if it helps.

---

### Post by chochem on 2008-06-26
As it turns out, the problem seems to have been one of zipping: the disk images (.d64) had been zipped and in some cases, this seems to have prevented the emulator from properly reading the image. Unzipped, the problem images work fine.

Still a big thanks to Richard James13 for your excellent commodore syntax explanation. Maybe I should start coding in basic again... :)

---

### Post by Jupp3 on 2008-06-27
> **Grishka said:**
> I see, that's alright then. sorry for being harsh. mouse emulation should work well, try alt+m. for fullscreen mode, try alt+d. if it doesn't work, perhaps something's wrong with your version of VICE. what version do you have, then? installed it from where?

I have version 1.22 from the ubuntu 8.04 repository, and indeed, the mouse emulation doesn't seem to work. I select alt-m which changes the pointer to show that it's in mouse mode, but C64 doesn't detect any movement. Found out the worst possible way (which is, after trying to get my C64 mouse reading routines working, untill I just gave up and tried on real hardware)

It seems to work on MorphOS port of the 1.21 version, so maybe it's just a temporary bug or something...

Guess I'll try compiling it from sources when I have time.

---

