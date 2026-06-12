---
title: "cedega instal"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Akya on 2005-12-14
when i try to install cedega it gives me this problem can any one help me?


gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/home/jeff/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/home/jeff/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by RAOF on 2005-12-14
I seem to recall this is a problem with their code.  It doesn't compile under gcc-4, which is what you'll have installed if you got "build-essential".

A solution would be to install the "gcc-3.4" package, and then run:
```
export CC=gcc-3.4
./WineCVS.sh

```
That should make cedega install using gcc-3.4, which doesn't mind so much that the cedega code is not quite standard :)

---

### Post by Akya on 2005-12-14
nope that didnt work export cc=gcc-3.4 doesnt do anything on my comp for some reason, like i enter it and it just doesnt do anything and then it goes to the next line

---

### Post by RAOF on 2005-12-14
The export line isn't meant to produce any output.  To check that it has worked, you can run "echo $CC", and it should say "gcc-3.4".  This is also **after** you have installed the gcc-3.4 package.  To do that, try "sudo apt-get install gcc-3.4"

---

### Post by Akya on 2005-12-14
that still didnt fix it :(

---

### Post by RAOF on 2005-12-14
Ok.  Running this:
```
export CC=gcc-3.4
$CC --version

```
should produce something that isn't an error.  If it does, you've got gcc-3.4 installed correctly.

Now, we want to get cedega working.  Lets just start from the beginning:
```
export CC=gcc-3.4
rm -r ~/.WineCVS
./WineCVS.sh

```
and try installing cedega again, from the beginning.

Incidentally, if you're trying to do this on an AMD64 system, don't bother.  It doesn't work.

---

### Post by NXArmada on 2005-12-14
I use Cedega and I have had no problems with it at all.

Check with Transgaming support see if they can help you with the problem.  They tend to be very helpful.

---

