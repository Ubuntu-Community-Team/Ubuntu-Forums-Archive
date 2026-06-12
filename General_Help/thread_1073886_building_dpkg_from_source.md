---
title: "building dpkg from source"
date: 2009-02-18
forum: General Help
---

### Post by jdelgado on 2009-02-18
Hello,

mine is a long story:

I wanted to install GRASS GIS 6.4 from the binaries, which means that I had to make some symbolic links from libgdal.so.1 to libgdal1.5.0.so.1 and so on. In the end it is necessary to run ldconfig, right?

When I run ldconfig, I get a very big mess, the beginning of it being:

```
jdelgado@jdelgado-laptop:~$ ldconfig
/sbin/ldconfig.real: 	&#65533;e is not a known library type
/sbin/ldconfig.real: &#65533;&#65533;&#65533;@*k&#65533;Q-&#65533;&#65533;V&#1141;&#65533;&#65533;&#65533;P&#65533;&#65533;&#65533;N\|&#65533;
                                              &#65533;&#65533;&#65533;&#65533;m&#65533;(&#65533;&#65533;&#65533;&#65533;c&#65533;:&#65533;&#65533;82&#65533;i&#65533;0K=K&#65533;E&#65533;`&#65533;&#65533;&#65533;&#380;&#65533;b&#65533;&#65533;&#65533;&#65533;/n&#65533;&#65533;( &#65533;Lm&#65533;L_&#65533;&#65533;&#65533;&#65533;t&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;&#65533;
                                 Z?V&#65533;&#65533;]&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;5I&#65533;&#65533;&#65533;&#65533;)-4&#65533;T&#65533;&#65533;b&#65533;O4x&#1665;&#65533;qu&#1502;
```

After I run ldconfig, my prompt (like the beginning of each line on my shell) is not written in normal characters, but in very strange ones, like this:

```
&#9496;&#9229;&#9226;&#9484;±&#9618;&#9229;&#9146;@&#9496;&#9229;&#9226;&#9484;±&#9618;&#9229;&#9146;-&#9484;&#9618;&#9147;&#9500;&#9146;&#9147;:·$ 
```

I can actually keep typing and make commands, but I simply cannot understand anything. I have normally to close the terminal and open it again.

The problem is after I started with these operations I could never open synaptic again or do any kind of apt-get: I always get the following (which was already discussed in other threads, and believe me, I have tried them all):

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I do exactly that, dpkg --configure -a, and the result is the same as when I do ldconfig (the weird characters).

This is why I want to install dpkg from source, which I did. But I got the following error:

```
jdelgado@jdelgado-laptop:~/Desktop/dpkg-1.14.12ubuntu4$ make
make  all-recursive
make[1]: Entering directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4'
Making all in intl
make[2]: Entering directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4/intl'
Making all in getopt
make[2]: Entering directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4/getopt'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4/getopt'
Making all in lib
make[2]: Entering directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4/lib'
: trigdeferred.l
gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -I../intl -DCONFIGDIR=\"/usr/local/etc/dpkg\" -DCOPYINGFILE=\"/usr/local/share/common-licenses/GPL-2\"    -g -O2 -MT trigdeferred.o -MD -MP -MF .deps/trigdeferred.Tpo -c -o trigdeferred.o trigdeferred.c
gcc: trigdeferred.c: No such file or directory
gcc: no input files
make[2]: *** [trigdeferred.o] Error 1
make[2]: Leaving directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jdelgado/Desktop/dpkg-1.14.12ubuntu4'
make: *** [all] Error 2
```

I don't know exactly what the problem is, if it is trigdeferred.c that is missing or something else (anyway I don't have a clue of what trigdeferred.c is...).

I decided to ignore the error and move forward, which brought me to run 'dpkg --configure -a' again. This time, there are no more weird characters but only a error message:

```
dpkg: failed to open package info file `/usr/local/var/dpkg/status' for reading: No such file or directory
```

I simply 'touch status' on the right directory. Then:

```
dpkg: failed to open package info file `/usr/local/var/dpkg/available' for reading: No such file or directory
```

and I just 'touch available' on the same directory.

In the end, I run 'dpkg --configure -a' and nothing happens. And I still can not run synaptic or any apt-get or run ldconfig, which is very critical for me.

Hope you made it to the end of the message :)

Thanks for your help

jose miguel

---

### Post by snova on 2009-02-18
> **jdelgado said:**
> ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I do exactly that, dpkg --configure -a, and the result is the same as when I do ldconfig (the weird characters).

Well, I can't explain the weird characters, but that command must be run with sudo (as it is an administrative command):

```
sudo dpkg --configure -a
```

---

### Post by jdelgado on 2009-02-19
Well, I used sudo as a matter of fact.

Summarizing my long threadL

[LIST]
[*]I need to know what is going on with ldconfig and in which way it is related to dpkg
[*]I need to build dpkg from source, as apt-get does not work anymore
[/LIST]

thanks for your help!

j

---

### Post by snova on 2009-02-19
> **jdelgado said:**
> Well, I used sudo as a matter of fact.

Sorry. I've misread things before. :)

> I need to know what is going on with ldconfig and in which way it is related to dpkg

I'm honestly not sure what ldconfig does...

> I need to build dpkg from source, as apt-get does not work anymore

I certainly hope not! dpkg is a very core system component, I'm not even sure it's possible to replace it (well, without breaking a lot of things).

Anyway, this can be fixed- and I have doubts that reinstalling dpkg would help anything anyway. The trouble is, I'm not sure *how*...

Well, I'm about out of ideas. I do know that trying to install another dpkg won't help, though.

```

sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a

```

See if it does anything...

Also, what happens if you just try to run the program? I'm not sure what ldconfig does, but I'm also not sure whether it's necessary.

---

### Post by Yellow Pasque on 2009-02-19
I have to agree that installing dpkg from source is not the solution here (you'd be hacking away at the branches instead of the root of the problem). 
> which means that I had to make some symbolic links from libgdal.so.1 to libgdal1.5.0.so.1
My guess is that this is where things went wrong. Try removing any links you manually created in /usr/lib.

---

### Post by jdelgado on 2009-02-20
Temujin,

I agree with you. The good news is that after removing the links the ldconfig works again. The problem is that while building the new version of dpkg I screwed it and now it does not work when I run apt-get update:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
``` 

I run dpkg... and nothing happens. I run again apt-get and I get the same.

 I will now boot from CD and try to repair or install any missing packages.

Thanks for the good hint.

j.

---

### Post by jdelgado on 2009-02-20
snova:

Thanks for your help. I think ldconfig is used sort of to actualize symbolic links that you create yourself. However, I am not sure about it... Anyway, it works again, but not any apt-get... It is not critical though, I still can install intrepid again or so :)

greetz

j.

---

