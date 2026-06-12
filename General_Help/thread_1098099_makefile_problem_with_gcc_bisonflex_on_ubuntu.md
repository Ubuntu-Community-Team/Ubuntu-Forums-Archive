---
title: "makefile problem with gcc bison/flex on ubuntu"
date: 2009-03-16
forum: General Help
---

### Post by Garvey on 2009-03-16
I presently have a compiler to write with Flex and Bison.
I have a lex.l file, and a parse.y in which there are no conflicts.
I also have a symtable.h included.

I have a makefile as follows...
============================================================
project: parse.tab.o lex.yy.o
	echo ---> compiling and linking project program
	cc -DYYDEBUG=1 -o project parse.tab.o lex.yy.o -ly -ll -lm    

lex.yy.o:   lex.yy.c parse.tab.h # the dependencies of lex.yy.o the lexer object
	echo ---> determining dependency for lex.yy.o

lex.yy.o parse.tab.o: symtable.h #just declares that symtable.h is a dependency to both
	echo ---> determining symtable.h dependency for lex.yy.o parse.tab.o

parse.tab.c parse.tab.h:  parse.y	# THE PARSE C AND H FILES MADE...  OK to here
	echo --->  making parse.tab.c and parse.tab.h
	bison -d parse.y

lex.yy.c : lex.l 			# THE LEX C FILE MADE
	echo ---> making lexfile
	flex lex.l

============================================================
When I run it, I get the following output.  The line numbers don't actually correspond. Could you advise as to how the makefile should be written to not have any error?
============================================================
joe@BlueAcer:/usr/local/project/chk$ make
makefile:9: warning: overriding commands for target `lex.yy.o'
makefile:6: warning: ignoring old commands for target `lex.yy.o'
echo ---> determining symtable.h dependency for lex.yy.o parse.tab.o
echo ---> making lexfile
flex lex.l
echo --->  making parse.tab.c and parse.tab.h
bison -d parse.y
echo ---> determining symtable.h dependency for lex.yy.o parse.tab.o
echo ---> compiling and linking project program
cc -DYYDEBUG=1 -o project parse.tab.o lex.yy.o -ly -ll -lm    
cc: parse.tab.o: No such file or directory
cc: lex.yy.o: No such file or directory
make: *** [&#65279;project] Error 1
joe@BlueAcer:/usr/local/project/chk$ 
============================================================

---

### Post by snova on 2009-03-16
> **Garvey said:**
> I presently have a compiler to write with Flex and Bison.
I have a lex.l file, and a parse.y in which there are no conflicts.
I also have a symtable.h included.

I have a makefile as follows...

```

project: parse.tab.o lex.yy.o
	echo ---> compiling and linking project program
	cc -DYYDEBUG=1 -o project parse.tab.o lex.yy.o -ly -ll -lm    

lex.yy.o:   lex.yy.c parse.tab.h # the dependencies of lex.yy.o the lexer object
	echo ---> determining dependency for lex.yy.o

lex.yy.o parse.tab.o: symtable.h #just declares that symtable.h is a dependency to both
	echo ---> determining symtable.h dependency for lex.yy.o parse.tab.o

parse.tab.c parse.tab.h:  parse.y	# THE PARSE C AND H FILES MADE...  OK to here
	echo --->  making parse.tab.c and parse.tab.h
	bison -d parse.y

lex.yy.c : lex.l 			# THE LEX C FILE MADE
	echo ---> making lexfile
	flex lex.l

```

When I run it, I get the following output.  The line numbers don't actually correspond. Could you advise as to how the makefile should be written to not have any error?

```

joe@BlueAcer:/usr/local/project/chk$ make
makefile:9: warning: overriding commands for target `lex.yy.o'
makefile:6: warning: ignoring old commands for target `lex.yy.o'
echo ---> determining symtable.h dependency for lex.yy.o parse.tab.o
echo ---> making lexfile
flex lex.l
echo --->  making parse.tab.c and parse.tab.h
bison -d parse.y
echo ---> determining symtable.h dependency for lex.yy.o parse.tab.o
echo ---> compiling and linking project program
cc -DYYDEBUG=1 -o project parse.tab.o lex.yy.o -ly -ll -lm    
cc: parse.tab.o: No such file or directory
cc: lex.yy.o: No such file or directory
make: *** [&#65279;project] Error 1
joe@BlueAcer:/usr/local/project/chk$ 

```

First of all, use [noparse]```
[/noparse] tags to preserve the indentation, its quite helpful.

Secondly, take a look at its output. It never compiles lex.yy.c or parse.tab.c, it only generates the sources.

This is because of the following rule:

[CODE]
lex.yy.o parse.tab.o: symtable.h #just declares that symtable.h is a dependency to both
	echo ---> determining symtable.h dependency for lex.yy.o parse.tab.o

```

As not only does it set the dependency chain, it also overrides make's default handling of .c files.

You could either write the compilation command here yourself, or remove the echo command.

---

