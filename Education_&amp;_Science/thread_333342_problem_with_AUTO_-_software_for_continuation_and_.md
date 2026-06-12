---
title: "problem with AUTO - software for continuation and bifurcation"
date: 2007-01-07
forum: Education &amp; Science
---

### Post by tkjacobsen on 2007-01-07
Does anyone know how to get AUTO 2000 to work under ubuntu?

When i run the test described in the manual
cd test/
make > TEST

i get the following error:
```

pp2.c:1:22: error: auto_f2c.h: No such file or directory
pp2.c:9: error: expected ‘)’ before ‘ndim’
pp2.c:23: error: expected ‘)’ before ‘ndim’
pp2.c:38: error: expected ‘)’ before ‘ndim’
pp2.c:45: error: expected ‘)’ before ‘ndim’
pp2.c:53: error: expected ‘)’ before ‘ndim’
pp2.c:60: error: expected ‘)’ before ‘ndim’
make[1]: *** [pp2.o] Error 1
exp.c:1:22: error: auto_f2c.h: No such file or directory
exp.c:9: error: expected ‘)’ before ‘ndim’
exp.c:21: error: expected ‘)’ before ‘ndim’
exp.c:31: error: expected ‘)’ before ‘ndim’
exp.c:41: error: expected ‘)’ before ‘ndim’
exp.c:49: error: expected ‘)’ before ‘ndim’
exp.c:56: error: expected ‘)’ before ‘ndim’
make[1]: *** [exp.o] Error 1
int.c:1:22: error: auto_f2c.h: No such file or directory
int.c:9: error: expected ‘)’ before ‘ndim’
int.c:46: error: expected ‘)’ before ‘ndim’
int.c:60: error: expected ‘)’ before ‘ndim’
int.c:92: error: expected ‘)’ before ‘ndim’
int.c:123: error: expected ‘)’ before ‘ndim’
int.c:131: error: expected ‘)’ before ‘ndim’
make[1]: *** [int.o] Error 1
dd2.c:1:22: error: auto_f2c.h: No such file or directory
dd2.c:9: error: expected ‘)’ before ‘ndim’
dd2.c:44: error: expected ‘)’ before ‘ndim’
dd2.c:58: error: expected ‘)’ before ‘ndim’
dd2.c:66: error: expected ‘)’ before ‘ndim’
dd2.c:75: error: expected ‘)’ before ‘ndim’
dd2.c:83: error: expected ‘)’ before ‘ndim’
make[1]: *** [dd2.o] Error 1
opt.c:1:22: error: auto_f2c.h: No such file or directory
opt.c:9: error: expected ‘)’ before ‘ndim’
opt.c:49: error: expected ‘)’ before ‘ndim’
opt.c:70: error: expected ‘)’ before ‘ndim’
opt.c:103: error: expected ‘)’ before ‘ndim’
opt.c:111: error: expected ‘)’ before ‘ndim’
opt.c:120: error: expected ‘)’ before ‘ndim’
make[1]: *** [opt.o] Error 1
lin.c:1:22: error: auto_f2c.h: No such file or directory
lin.c:9: error: expected ‘)’ before ‘ndim’
lin.c:23: error: expected ‘)’ before ‘ndim’
lin.c:37: error: expected ‘)’ before ‘ndim’
lin.c:48: error: expected ‘)’ before ‘ndim’
lin.c:59: error: expected ‘)’ before ‘ndim’
lin.c:67: error: expected ‘)’ before ‘ndim’
make[1]: *** [lin.o] Error 1
bvp.c:1:22: error: auto_f2c.h: No such file or directory
bvp.c:9: error: expected ‘)’ before ‘ndim’
bvp.c:25: error: expected ‘)’ before ‘ndim’
bvp.c:35: error: expected ‘)’ before ‘ndim’
bvp.c:45: error: expected ‘)’ before ‘ndim’
bvp.c:53: error: expected ‘)’ before ‘ndim’
bvp.c:60: error: expected ‘)’ before ‘ndim’
make[1]: *** [bvp.o] Error 1
pp3.c:1:22: error: auto_f2c.h: No such file or directory
pp3.c:9: error: expected ‘)’ before ‘ndim’
pp3.c:22: error: expected ‘)’ before ‘ndim’
pp3.c:40: error: expected ‘)’ before ‘ndim’
pp3.c:48: error: expected ‘)’ before ‘ndim’
pp3.c:57: error: expected ‘)’ before ‘ndim’
pp3.c:65: error: expected ‘)’ before ‘ndim’
make[1]: *** [pp3.o] Error 1
wav.c:1:22: error: auto_f2c.h: No such file or directory
wav.c:9: error: expected ‘)’ before ‘ndim’
wav.c:22: error: expected ‘)’ before ‘ndim’
wav.c:44: error: expected ‘)’ before ‘ndim’
wav.c:52: error: expected ‘)’ before ‘ndim’
wav.c:61: error: expected ‘)’ before ‘ndim’
wav.c:69: error: expected ‘)’ before ‘ndim’
make[1]: *** [wav.o] Error 1
plp.c:1:22: error: auto_f2c.h: No such file or directory
plp.c:9: error: expected ‘)’ before ‘ndim’
plp.c:71: error: expected ‘)’ before ‘ndim’
plp.c:87: error: expected ‘)’ before ‘ndim’
plp.c:95: error: expected ‘)’ before ‘ndim’
plp.c:104: error: expected ‘)’ before ‘ndim’
plp.c:112: error: expected ‘)’ before ‘ndim’
make[1]: *** [plp.o] Error 1

```

The file TEST is as follows:
```

make[1]: Entering directory `/home/mash/src/auto/2000/demos/pp2'
Cleaning pp2 ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o pp2.o pp2.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/pp2'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/pp2'
Cleaning pp2 ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/pp2'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/exp'
Cleaning exp ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o exp.o exp.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/exp'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/exp'
Cleaning exp ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/exp'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/int'
Cleaning int ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o int.o int.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/int'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/int'
Cleaning int ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/int'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/dd2'
Cleaning dd2 ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o dd2.o dd2.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/dd2'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/dd2'
Cleaning dd2 ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/dd2'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/opt'
Cleaning opt ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o opt.o opt.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/opt'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/opt'
Cleaning opt ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/opt'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/lin'
Cleaning lin ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o lin.o lin.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/lin'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/lin'
Cleaning lin ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/lin'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/bvp'
Cleaning bvp ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o bvp.o bvp.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/bvp'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/bvp'
Cleaning bvp ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/bvp'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/pp3'
Cleaning pp3 ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o pp3.o pp3.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/pp3'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/pp3'
Cleaning pp3 ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/pp3'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/wav'
Cleaning wav ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o wav.o wav.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/wav'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/wav'
Cleaning wav ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/wav'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/plp'
Cleaning plp ...
Cleaning ... done
gcc -pthread -DPTHREADS -O -I/include    -c -o plp.o plp.c
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/plp'
make[1]: Entering directory `/home/mash/src/auto/2000/demos/plp'
Cleaning plp ...
Cleaning ... done
make[1]: Leaving directory `/home/mash/src/auto/2000/demos/plp'

```

---

### Post by emancusi on 2007-05-03
Hi! a couple of years later I have the same proble whit AUTO 2000. Did You solve your problem? May you help me? Please may you contact me at email [email]mancusi@unina.it[/email].
Best,
erasmo

---

### Post by WW on 2007-05-03
This works for me:

After running **./configure** and **make** in the auto/2000 directory, edit the file auto/2000/cmds/auto.env.sh so that the environment variable AUTO_DIR is the auto/2000 directory.  (By default, it is set to $HOME/auto/2000.  If you have extracted the tar file in your home directory, it will not be necessary to edit this file.)  Then, assuming you are in the auto/2000 directory, give the command
```

$ source cmds/auto.env.sh

```
Next, add the "current directory" to your path:
```

$ export PATH=$PATH:.

```
(It is normally recommended that you do not do this, but it appears that some of the AUTO tools expect it.)

Now this should work:
```

$ cd test
$ make > TEST

```

---

### Post by emancusi on 2007-05-04
THX very much. NOW AUTO 2000 works. 
Best

---

