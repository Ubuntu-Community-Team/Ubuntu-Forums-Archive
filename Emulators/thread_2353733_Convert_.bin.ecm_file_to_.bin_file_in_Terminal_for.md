---
title: "Convert .bin.ecm file to .bin file in Terminal for macbook?"
date: 2017-02-24
forum: Emulators
---

### Post by jaywolf on 2017-02-24
Hello. So I'm trying to follow this websites directions ([https://github.com/OpenEmu/OpenEmu/wiki/User-guide:-CD-based-games#q-i-have-an-ecm-or-ape-file](https://github.com/OpenEmu/OpenEmu/wiki/User-guide:-CD-based-games#q-i-have-an-ecm-or-ape-file))   to get a .bin.ecm to just .bin.   I get up to the open terminal part  and drag and drop the game folder into Terminal then type what the  website tells me to type. Terminal then says:  
```
Last login: Thu Feb  9 15:43:31 on ttys000
Owners-MBP-2:~ Jaywolf$ /Users/owner/Desktop/LSD\ -\ Dream\ Emulator\ \(Japan\)\ \[SLPS-01556\] ./unecm "Track 01.bin.ecm" "LSD - Dream Emulator (Japan) [SLPS-01556].bin"
-bash: /Users/owner/Desktop/LSD - Dream Emulator (Japan) [SLPS-01556]: is a directory
Owners-MBP-2:~ Jaywolf$ /Users/owner/Desktop/LSD\ -\ Dream\ Emulator\ \(Japan\)\ \[SLPS-01556\]/unecm ./unecm "Track 01.bin.ecm" "LSD - Dream Emulator (Japan) [SLPS-01556].bin"
UNECM - Decoder for Error Code Modeler format v1.0
Copyright (C) 2002 Neill Corlett

usage: /Users/owner/Desktop/LSD - Dream Emulator (Japan) [SLPS-01556]/unecm ecmfile [outputfile]
Owners-MBP-2:~ Jaywolf$ "
```

I have no idea how to use terminal at all. I'm trying to get the game: LSD -Dream Emulator to work on Openemu. Any help appreciated.

I drag and drop the Game folder into teminal and then copy and paste: ./unecm "Track 01.bin.ecm" "LSD - Dream Emulator (Japan) [SLPS-01556].bin"  into terminal. it then says:

```
Last login: Thu Feb  9 16:05:48 on ttys000
Owners-MBP-2:~ Jaywolf$ /Users/owner/Desktop/LSD\ -\ Dream\ Emulator\ \(Japan\)\ \[SLPS-01556\] ./unecm "Track 01.bin.ecm" "LSD - Dream Emulator (Japan) [SLPS-01556].bin"
-bash: /Users/owner/Desktop/LSD - Dream Emulator (Japan) [SLPS-01556]: is a directory
Owners-MBP-2:~ Jaywolf$ 
```


so I drag and drop the Unecm terminal file thing into terminal. It then adds: 

```
/Users/owner/Desktop/LSD\ -\ Dream\ Emulator\ \(Japan\)\ \[SLPS-01556\]/unecm 
```

so I copy and paste:  ./unecm "Track 01.bin.ecm" "LSD - Dream Emulator (Japan) [SLPS-01556].bin"  into terminal. It then adds: 

```
UNECM - Decoder for Error Code Modeler format v1.0
Copyright (C) 2002 Neill Corlett

usage: /Users/owner/Desktop/LSD - Dream Emulator (Japan) [SLPS-01556]/unecm ecmfile [outputfile]
Owners-MBP-2:~ Jaywolf$ 

```
No idea what to do next. Or if I'm even doing it right.
The file I'm trying to convert is: Track 01.bin.ecm

Any Help very appreciated! I seriously only wanna play this game because of a creepypasta I read about it lol. I'd buy it for my PS2 (since it plays ps1 games) but I'm sure Dad wouldn't let me buy a game with the name "LSD"  XD

Thanx in advance.

---

### Post by wildmanne39 on 2017-02-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by adec2 on 2017-02-24
Was there a batch file with this? If so you can just open a terminal (with wine installed) and type "wine <path to your batch file.bat"

---

### Post by jaywolf on 2017-02-24
> **adec2 said:**
> Was there a batch file with this? If so you can just open a terminal (with wine installed) and type "wine <path to your batch file.bat"

Nope. Inside the LSD Dream emulator folder is as follows:
a .cue file
a .bin.ecm file
a .7z file

---

### Post by adec2 on 2017-06-02
sudo apt install ecm
then type ecm-uncompress <path to .bin.ecm file>

---

