---
title: "Compiling Matlab mex files in feisty"
date: 2007-04-04
forum: Education &amp; Science
---

### Post by sam81 on 2007-04-04
Hello, has anyone had any luck compiling mex files in feisty?

I'm using Matlab 7.1.0.21 (R14) Service Pack 3 (student version), and I'm trying to compile a mex file for sound playback. I have a mexopts.sh file in the directory where I'm compiling, and have set the compiler version to gcc-4.1 there
```
CC = gcc-4.1
```
The compilation goes fine with
```
mex -v playsnd.c
```
however when I try to use the binary I get the following error:
```
EDU>> a=wavread('interval1.wav');
EDU>> playsnd(a, 44100, 16)
??? Invalid MEX-file '/home/sam/playsnd/playsnd.mexglx': /usr/local/matlab71_sv/bin/glnx86/../../sys/os/glnx86/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6).
```

gcc 4.2 is not in the repos as far as I know, but for some reason one of its library files is required :confused: . A google search came up with the following thread, [http://ubuntuforums.org/showthread.php?t=270605]("http://ubuntuforums.org/showthread.php?t=270605") which suggests that the problem is not matlab specific. The solutions proposed in that thread didn't work for me, and I'm a bit confused :(  by all the linking and C library version stuff (you guess I have no experience in C programming).

If anyone has any suggestions it would be very much appreciated!

btw. the file compiles and works well in edgy with the same matlab version.

---

### Post by ashipika on 2007-04-24
Hello...

I had the same problem in Feisty.. But following the advice found here ([http://mexcdf.sourceforge.net/faq.html](http://mexcdf.sourceforge.net/faq.html)) i did the following:
# cd $MATLAB
# cd sys/os/glnx86
# mkdir old
# mv libstdc++.* libg2c.* libgcc_s* old
thereby forcing matlab to uses systems libraries.. After restarting Matlab compiling "just worked" :) 

I have MEX back!! YAHOOOO!

Cheers,
    Ales

---

### Post by sam81 on 2007-04-26
Thanks, I eventually got the sound playback working right using a mex file compiled in edgy with gcc3.3, I'll try out your solution when I have time anyhow, it might turn out useful if I have to compile any other mex. Though I dearly hope I won't have to compile any mex file, each time it's like going through hell uh...

---

### Post by shellyoung on 2007-06-13
Thanks ashipika
it works for me very well!

---

