---
title: "make error"
date: 2010-03-05
forum: Education &amp; Science
---

### Post by masoodstar on 2010-03-05
Dear friends

I encountered an error during lbflow package installation (a scientific one).

The sequence of operations is here with error:

>>./configure --disable-gts
>>sudo make

[SIZE=2][B][sudo] password for amp: 
make  all-recursive
make[1]: Entering directory `/home/amp/lbflow-1.1'
Making all in src
make[2]: Entering directory `/home/amp/lbflow-1.1/src'
source='lbflow.cpp' object='lbflow-lbflow.o' libtool=no \
    DEPDIR=.deps depmode=none /bin/bash ../depcomp \
    g++ -DHAVE_CONFIG_H -I. -I. -I..         -c -o lbflow-lbflow.o `test -f 'lbflow.cpp' || echo './'`lbflow.cpp
../depcomp: line 432: exec: g++: not found
make[2]: *** [lbflow-lbflow.o] Error 127
make[2]: Leaving directory `/home/amp/lbflow-1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/amp/lbflow-1.1'
make: *** [all] Error 2
[/B][/SIZE]
Do you have any idea to troubleshoot this problem?

Thanks

---

### Post by spinoza666 on 2010-03-05
Well I'm certainly no expert on installing from source, but I noticed that it says 'g++ not found' in your error message. Do you you have the necessary compiler installed? I believe it's the g++ or gcc package. Install/reinstall them both and see if it works?

---

### Post by s.fox on 2010-03-05
Hello,

Can you confirm that the g++ package is installed?   I  believe it is called gcc-c++ in synaptic package manager.

-Silver Fox

---

### Post by masoodstar on 2010-03-05
Thank you all

But I've installed g++-gcc on my machine manually; and my problem already exists.

Is there any failure with my installation that I get this error.

Please tell me another useful solution.

---

### Post by DzmitryG on 2010-03-08
Post there:
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

---

