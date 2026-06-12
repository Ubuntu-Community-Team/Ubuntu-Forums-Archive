---
title: "Trying to install free command and conqure"
date: 2006-12-12
forum: Gaming &amp; Leisure
---

### Post by penguinchrissy on 2006-12-12
when I try to run the make file I get this error I have no clue what it means 

make[1]: Entering directory `/home/dj/freecnc++/src'
g++ -Wall -Werror -g  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -std=c++98 -Wconversion -W -Wno-unused -c game/dispatcher.cpp -o game/dispatcher.o -I./include  -I./include/lua
./include/structure.h:268: error: ISO C++ forbids declaration of ‘BuildingAnimEvent’ with no type
./include/structure.h:268: error: expected ‘;’ before ‘*’ token
make[1]: *** [game/dispatcher.o] Error 1
make[1]: Leaving directory `/home/dj/freecnc++/src'
make: *** [default] Error 2

any ideas?

---

### Post by Nerdriot on 2008-02-12
I'm having the exact same issue. I've done everything I know to do, really...

Completely lost.

Anyone have any ideas? Please and thank you. :)

---

### Post by compiledkernel on 2008-02-12
Best guess, its a problem with the source. Would take some modification to correct that. The project seems fairly dead, have either of you considered 

[FreeRa]("http://gaming.gwos.org/doku.php/games:alphabetical:f:freera")
or
[BosWars]("http://gaming.gwos.org/doku.php/games:alphabetical:b:boswars")

---

### Post by PoHandle on 2008-07-12
I have figured out a solution that worked on my machine.  I had the same exact error when attempting to compile FreeCnC from source.  By adding a line into one of the source files, I was able to get the game running (No sound in opening video, and no SHPviewer tool).

I extracted freecnc-20041219-source.tgz to my home folder:
```
tar -xvf ~/freecnc-20041219-source.tgz
```

I'm using the .MIX files from the free demo.  I put them all in the ~/freecnc++/data/mix directory.

Then I created a backup of the problematic source file and edited it:
```
cp ~/freecnc++/src/include/structure.h ~/freecnc++/src/include/structure.h.backup
gedit ~/freecnc++/src/include/structure.h
```

At line 162, you will have to add:
```
class BuildingAnimEvent;
```
so structure.h has been changed from this:
```
...
    // matches the unit's type value specified in units.ini
    std::vector<Uint8> passengerAllow;
    // matches the unit's type name.
    std::vector<UnitType*> specificTypeAllow;
};

class BAttackAnimEvent;

class Structure : public UnitOrStructure
{
public:
    friend class BuildingAnimEvent;
    friend class BAttackAnimEvent;
...
```
to this:
```
...
    // matches the unit's type value specified in units.ini
    std::vector<Uint8> passengerAllow;
    // matches the unit's type name.
    std::vector<UnitType*> specificTypeAllow;
};

class BAttackAnimEvent;
class BuildingAnimEvent;
class Structure : public UnitOrStructure
{
public:
    friend class BuildingAnimEvent;
    friend class BAttackAnimEvent;
...
```

Save and exit gedit.  Now go to the freecnc++ directory and compile:
```
cd ~/freecnc++
make
```

After it goes through the build process (you'll get errors about the SHPviewer tool) you will be able to play FreeCnC with:
```
~/freecnc++/freecnc
```

I know it's not the best fix, but it gets the job done.  Hope this helps.

---

