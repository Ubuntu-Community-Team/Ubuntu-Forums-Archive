---
title: "Make command not working"
date: 2009-05-20
forum: General Help
---

### Post by mtdinesh on 2009-05-20
Hi all
I am completely new to ubuntu. as some of my programs work only in linux, i made an UBUNTU 9.04 live cd...and the system works perfectly

But when i tried to install the programs, when I type the MAKE command it returns "Make command not found"..Then one of my friend suggested to run the command

**[COLOR=Red]sudo apt-get install build-essential[/COLOR]**

after that when i ran MAKE the result was like this

[I]rm -f *.o germline test/generated.match test/generated.log test/generated.err
g++ -O3 -I include -c GERMLINE_0001.cpp
In file included from InputManager.h:6,
                 from GERMLINE.h:6,
                 from GERMLINE_0001.cpp:1:
BasicDefinitions.h:27: error: ‘ofstream’ does not name a type
GERMLINE_0001.cpp: In function ‘int main(int, char**)’:
GERMLINE_0001.cpp:20: error: ‘strlen’ was not declared in this scope
GERMLINE_0001.cpp:20: error: ‘strncmp’ was not declared in this scope
make: *** [GERMLINE_0001.o] Error 1[/I]

then by browsing the internet I used the following options also...

[B][COLOR=Red]sudo apt-get install openssl

sudo apt-get install kernel-source[/COLOR][/B]

But the MAKE comand is not working..

Please help..

Thanks in advance

dinesh

---

### Post by kmaster228 on 2009-05-20
OK first of all what exactly did you type into the terminal, the command to make a folder is mkdir, im not sure about the make command, what exactly do you want to make?

---

### Post by Jonnox on 2009-05-20
before you try to install, you should use:

```
sudo apt-get update
```

But if you are running from a LiveCD then when you reboot then you will lose all the programs you installed.

But after that is said, it appears what you have is a syntatical probelm with your code. If *g++* encounters a problem, then the make will show an error.

> from GERMLINE.h:6,
from GERMLINE_0001.cpp:1:
BasicDefinitions.h:27: error: ‘ofstream’ does not name a type
GERMLINE_0001.cpp: In function ‘int main(int, char**)’:
GERMLINE_0001.cpp:20: error: ‘strlen’ was not declared in this scope
GERMLINE_0001.cpp:20: error: ‘strncmp’ was not declared in this scope
make: *** [GERMLINE_0001.o] Error 1


It appears you might have forgotten an ```
#include
```

---

### Post by Bender2k14 on 2009-05-20
What does your makefile look like?

---

### Post by mtdinesh on 2009-05-20
I opened the file "Makefile"....it looks like this....
But within the directory there is no file with name "Make"

CC=g++
OPT=-O3 -I include
SRCS=GERMLINE_0001.cpp GERMLINE.cpp Share.cpp Chromosome.cpp ChromosomePair.cpp HMIndividualsExtractor.cpp MarkerSet.cpp Individual.cpp Individuals.cpp InputManager.cpp MatchFactory.cpp MatchesBuilder.cpp NucleotideMap.cpp PEDIndividualsExtractor.cpp Match.cpp PolymorphicIndividualsExtractor.cpp SNP.cpp SNPPositionMap.cpp SNPs.cpp
OBJS=GERMLINE_0001.o GERMLINE.o Chromosome.o Share.o ChromosomePair.o HMIndividualsExtractor.o MarkerSet.o Individual.o Individuals.o InputManager.o MatchFactory.o MatchesBuilder.o NucleotideMap.o PEDIndividualsExtractor.o Match.o PolymorphicIndividualsExtractor.o SNP.o SNPPositionMap.o SNPs.o
MAIN=germline

all: clean germline test_case

germline: $(OBJS)
    $(CC) $(OPT) -o $(MAIN) $(OBJS)

$(OBJS): $(SRCS)
    $(CC) $(OPT) -c $*.cpp
clean:
    -rm -f *.o $(MAIN) test/generated.match test/generated.log test/generated.err
test_case:
    -@./$(MAIN) -bits 50 -min_m 1 -err_hom 2 -err_het 0 < test/test.run 2> test/generated.err | echo "Running Test Case"
    diff -q -s test/expected.match test/generated.match

---

### Post by mtdinesh on 2009-05-20
> **kmaster228 said:**
> OK first of all what exactly did you type into the terminal, the command to make a folder is mkdir, im not sure about the make command, what exactly do you want to make?

I wanted to compile a program called GERMLINE using the command MAKE...
this is what i followed...

*From the command line, extract germline with tar xzvf germline-X-X-X.zip, enter the extracted directory, and compile germline with make. *

---

### Post by StuartN on 2009-05-20
> **mtdinesh said:**
> I wanted to compile a program called GERMLINE using the command MAKE...

Yes, it looks like a _#include <string.h>_ or similar is missing from your main source.

---

