---
title: "&quot;make install&quot; export , problem in FLENS compiling"
date: 2009-11-26
forum: Desktop Environments
---

### Post by mohabic on 2009-11-26
[COLOR=#000000][FONT=arial]Dear All:
        In ubuntu/linux, now i could install all dependencies, 'make' the FLENS file and here is the o/p of terminal.
[SIZE=3]moha@ubuntu:~$ cd /home/moha/FLENS-2009-06-12
moha@ubuntu:~/FLENS-2009-06-12$ make

   FLENS_HOME=/home/moha/FLENS-2009-06-12


processing dir flens:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/flens'
g++ -shared -Wall -Wextra -Werror -g -O0 -fPIC -o [libflens.so]("http://libflens.so/") .obj/*.o -llapack -latlas -lblas
cp libflens.so /home/moha/FLENS-2009-06-12
make[1]: Leaving directory `/home/moha/FLENS-2009-06-12/flens'

processing dir tutorials:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/tutorials'
make[1]: Nothing to be done for `all'.
make[1]:  Leaving directory `/home/moha/FLENS-2009-06-12/tutorials'

processing dir examples:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/examples'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/moha/FLENS-2009-06-12/examples'

processing dir tests:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/tests'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/moha/FLENS-2009-06-12/tests'
----------------------------------------------------------------------------------------------------------------------

Now the problem is I can't execute these:-
1- export LD_LIBRARY= /home/moha/FLENS-2009-06-12/:$LD_LIBRARY

the terminal o/p is :-
bash: export: `/home/moha/FLENS-2009-06-12/:': not a valid identifier

2-make install
terminal o/p is:-
Makefile.common:19: /config: No such file or directory
make: *** No rule to make target  `/config'.  Stop.

Thanks on advane
[/SIZE][/FONT][/COLOR]

---

### Post by lloyd_b on 2009-11-27
> **mohabic said:**
> [COLOR=#000000][FONT=arial]Dear All:
        In ubuntu/linux, now i could install all dependencies, 'make' the FLENS file and here is the o/p of terminal.
[SIZE=3]moha@ubuntu:~$ cd /home/moha/FLENS-2009-06-12
moha@ubuntu:~/FLENS-2009-06-12$ make

   FLENS_HOME=/home/moha/FLENS-2009-06-12


processing dir flens:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/flens'
g++ -shared -Wall -Wextra -Werror -g -O0 -fPIC -o [libflens.so]("http://libflens.so/") .obj/*.o -llapack -latlas -lblas
cp libflens.so /home/moha/FLENS-2009-06-12
make[1]: Leaving directory `/home/moha/FLENS-2009-06-12/flens'

processing dir tutorials:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/tutorials'
make[1]: Nothing to be done for `all'.
make[1]:  Leaving directory `/home/moha/FLENS-2009-06-12/tutorials'

processing dir examples:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/examples'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/moha/FLENS-2009-06-12/examples'

processing dir tests:

make[1]: Entering directory `/home/moha/FLENS-2009-06-12/tests'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/moha/FLENS-2009-06-12/tests'
----------------------------------------------------------------------------------------------------------------------

Now the problem is I can't execute these:-
1- export LD_LIBRARY= /home/moha/FLENS-2009-06-12/:$LD_LIBRARY

the terminal o/p is :-
bash: export: `/home/moha/FLENS-2009-06-12/:': not a valid identifier

2-make install
terminal o/p is:-
Makefile.common:19: /config: No such file or directory
make: *** No rule to make target  `/config'.  Stop.

Thanks on advane
[/SIZE][/FONT][/COLOR]

Assuming you cut-n-pasted that "export..." line, your problem is that you have a space after the equals sign - bash doesn't like that!

Lloyd B.

---

