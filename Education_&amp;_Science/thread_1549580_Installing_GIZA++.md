---
title: "Installing GIZA++"
date: 2010-08-10
forum: Education &amp; Science
---

### Post by nakul777 on 2010-08-10
-->GIZA++ is a statistical M.T. software. i have dell inspiron 1540 machine with 10.04  LTS updated from internet. when i try running the make file i get following errors.Please tell what should be done of it. 


&#65279;-->nakul@nakul-laptop:~/GIZA++/GIZA++-v2$ make >>output.txt 
In file included from Parameter.h:28, 
                 from Parameter.cc:23: 
Pointer.h:27:20: error: stream.h: No such file or directory 
Parameter.cc:24:21: error: fstream.h: No such file or directory 
In file included from Parameter.h:26, 
                 from Parameter.cc:23: 
mystl.h: In member function ‘bool leda_h_array<A, B>::defined(const A&) const’: 
mystl.h:183: error: there are no arguments to ‘end’ that depend on a template parameter, so a declaration of ‘end’ must be available 
mystl.h:183: note: (if you use ‘-fpermissive’, G++ will accept your code, but allowing the use of an undeclared name is deprecated) 
mystl.h: In member function ‘const B& leda_h_array<A, B>operator[](const A&) const’: 
mystl.h:187: error: there are no arguments to ‘end’ that depend on a template parameter, so a declaration of ‘end’ must be available 
mystl.h: In member function ‘B& leda_h_array<A, B>operator[](const A&)’: 
mystl.h:195: error: there are no arguments to ‘end’ that depend on a template parameter, so a declaration of ‘end’ must be available 
mystl.h:199: error: there are no arguments to ‘end’ that depend on a template parameter, so a declaration of ‘end’ must be available 
In file included from Parameter.h:28, 
                 from Parameter.cc:23: 
Pointer.h: At global scope: 
Pointer.h:41: warning: type qualifiers ignored on function return type 
Pointer.h:62: warning: type qualifiers ignored on function return type 
Pointer.h: In member function ‘const DELP<T>& DELP<T>operator=(DELP<T>&)’: 
Pointer.h:138: error: ‘p’ was not declared in this scope 
Pointer.h: In destructor ‘DELP<T>::~DELP()’: 
Pointer.h:144: error: ‘p’ was not declared in this scope 
Pointer.h: In member function ‘void DELP<T>::set(T*)’: 
Pointer.h:149: error: ‘p’ was not declared in this scope 
In file included from Parameter.cc:23: 
Parameter.h: In function ‘unsigned int mConvert(const std::string&, unsigned int&)’: 
Parameter.h:35: error: ‘strcasecmp’ was not declared in this scope 
In file included from Parameter.cc:23: 
Parameter.h:36: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h: In function ‘int mConvert(const std::string&, int&)’: 
Parameter.h:40: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h:41: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h: In function ‘bool mConvert(const std::string&, bool&)’: 
Parameter.h:48: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h:49: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h: In function ‘short int mConvert(const std::string&, short int&)’: 
Parameter.h:53: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h:54: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h: In function ‘short unsigned int mConvert(const std::string&, short unsigned int&)’: 
Parameter.h:58: error: ‘strcasecmp’ was not declared in this scope 
Parameter.h:59: error: ‘strcasecmp’ was not declared in this scope 
Parameter.cc: In function ‘bool writeParameters(stdofstream&, const ParSet&, int)’: 
Parameter.cc:48: warning: ignoring return value of ‘char* getcwd(char*, size_t)’, declared with attribute warn_unused_result 
make: *** [optimized/Parameter.o] Error 1 

README file contents are as follows (showing only the relevant part of it):-

Part II: How To Compile GIZA++

In order to compile GIZA++ you may need:
- recent version of the GNU compiler (2.95 or higher)
- recent version of assembler and linker which do not have restrictions
  with respect to the length of symbol names

There is a make file in the src directory that will take care of the
compilation. The most important targets are:

GIZA++: generates an optimized version 

GIZA++.dbg: generates the debug version 

depend: generates the "dependencies" file (make this whenever you add
source or header files to the package.

========================================================================
Part III: How To run GIZA++

It's simple:

GIZA++ [config-file] [options]

All options which expect a parameter could also be used in the
parameter file. For example the command line options

    GIZA++ -S S.vcb -T T.vcb -C ST.snt

corresponds to the config file:

    S: S.vcb
    T: T.vcb
    C: ST.snt

If you call GIZA++ without a parameter you get a list of all the
options. The option names form GIZA are normally still valid. The
default values of the parameters typically are optimized with respect
to the corpora I use and typically give good results. It is
nevertheless important that these parameters are always optimized for
every new task.

---

### Post by wafadz on 2011-05-17
[SIZE=2][B]Dear All

I am installing Giza++, now i reached the 3 step which includes running the 'make' under giza-pp folder
I have some troubles with the make file 
[COLOR=DarkGreen]
warda@Satellite-C650D:~/Giza/giza-pp$ make
make -C GIZA++-v2
make[1]: Entering directory `/home/warda/Giza/giza-pp/GIZA++-v2'
g++   -Wall -W -Wno-deprecated -O3 -DNDEBUG -DWORDINDEX_WITH_4_BYTE   -c Parameter.cpp -o optimized/Parameter.o
In file included from Parameter.h:28:0,
                 from Parameter.cpp:23:
Pointer.h:27:20: fatal error: stream.h: No such file or directory
compilation terminated.
make[1]: *** [optimized/Parameter.o] Error 1[/COLOR]

Can you help me please
[/B][/SIZE]

---

### Post by PC_load_letter on 2011-05-17
I have no experience with GIZA++ but reading through the error message, the compiler is looking for a file (stream.h) but can't find it. This is a header file and it should be included with the source, or it should be part of the system. 

A quick googling :D reveals that all the .h files have been deprecated from the newer versions of GCC, here is the relevant thread: 
[http://ubuntuforums.org/showthread.php?t=1188714](http://ubuntuforums.org/showthread.php?t=1188714)

Please report back if you manage to fix it.


**EDIT:** Here is another thread, with a possible fix: 
[http://ubuntuforums.org/showthread.php?t=1180125#2](http://ubuntuforums.org/showthread.php?t=1180125#2)

---

### Post by muneson on 2012-01-09
A more forward-looking solution is to get a version of Giza >= 1.0.3,
which does compile with newer g++.

[http://code.google.com/p/giza-pp/downloads/list](http://code.google.com/p/giza-pp/downloads/list)

---

