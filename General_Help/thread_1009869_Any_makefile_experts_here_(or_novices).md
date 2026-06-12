---
title: "Any makefile experts here? (or novices)"
date: 2008-12-13
forum: General Help
---

### Post by Fuwisu on 2008-12-13
Ok this is the problem:

I've got a working directory with 

Directory1 (contains class1.cpp and class1.h)
Directory2 (contains class2.cpp and class2.h)
Directory3 (contains class3.cpp and class3.h)
Makefile 

Say class1.h includes class2.h and class2.h includes class3.h
(to keep it easy). Now my makefile is the following:

CC=g++

CXXFLAGS=-Wall

LDFLAGS=

SOURCES=Plaats/Plaats.cpp Adres/Adres.cpp StandIncl/StandIncl.cpp Reservatie/Reservatie.cpp Optreden/Optreden.cpp Concertzaal/Concertzaal.cpp Klant/Klant.cpp Systeem/Systeem.cpp Main/Main.cpp

OBJECTS=$(SOURCES:.cpp=.o)

BIN=elk

all: $(OBJECTS)
	$(CC)	$(OBJECTS) $(LDFLAGS) -o $(BIN)

.cpp .o:
	$(CC)	$(CXXFLAGS) -c $<

depend:
	makedepend	-- $(CXXFLAGS)  --  $(SOURCES)

.PHONY:
clean:
	rm -f *.o
	rm -f *.d
	rm -f $(BIN)

------------------------------------------------------------

As you see, I've got 10 directories. Now my problem is that it doesn't want to make because it can't find the included header file (for example: class1.h: cannot find class2.h) because, of course, class2.h isn't in the same directory as class1.h.
I've already tried #include "Directory2/Class2.h", #include "Class2.h" in the header files and "SOURCES=Plaats/Plaats.cpp" and "SOURCES=Plaats.cpp" in the makefile, yet it doesn't work.
Can anyone give me a better makefile OR say what the solution is to this problem?

Many thanks in advance.

---

### Post by Fuwisu on 2008-12-13
bumpedeebump

---

### Post by Fuwisu on 2008-12-13
Ok I noticed it has something to do with the -I flags, I tried putting -I.. and -I/ behind it, still no results.

---

### Post by Keith Hedger on 2008-12-13
try ```
-I/path/to/directory1 -I/path/to/directory2 -I/path/to/directory3
```

you should be able to use relative paths

---

### Post by Fuwisu on 2008-12-13
It checks the map of the header file, the relative path is then /go 1 map up/, but I don't know how to formulate that.

---

### Post by Keith Hedger on 2008-12-13
```
./folder  - "folder" in current directory
../folder - "folder" at same level as current dir
../../folder - "folder" in directory above current dir
```

---

### Post by Fuwisu on 2008-12-13
So what should be changed in my makefile? Cause it doesn't seem to work.

---

### Post by Fuwisu on 2008-12-13
Problem fixed, thanks.

---

