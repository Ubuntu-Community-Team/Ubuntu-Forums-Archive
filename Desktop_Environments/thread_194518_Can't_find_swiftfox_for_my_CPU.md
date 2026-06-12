---
title: "Can't find swiftfox for my CPU"
date: 2006-06-11
forum: Desktop Environments
---

### Post by joplass on 2006-06-11
I have been trying to install swiftfox with automatix on my notebook but I keep getting "there is not swiftfox for your CPU".
Any idea?

---

### Post by art on 2006-06-11
What CPU do you have? Swiftfox is compiled for several architectures, see here:
[http://getswiftfox.com/releases.htm](http://getswiftfox.com/releases.htm)

---

### Post by joplass on 2006-06-11
I have a Pentium4.  I was able to install it on my desktop which is also a P4.

---

### Post by arnieboy on 2006-06-11
can u paste the results of the following commands:
```
cat /proc/cpuinfo | egrep "cpu family" | egrep "15"
cat /proc/cpuinfo | egrep Intel
```

---

### Post by joplass on 2006-06-14
[QUOTE=arnieboy]can u paste the results of the following commands:
```
cat /proc/cpuinfo | egrep "cpu family" | egrep "15"
cat /proc/cpuinfo | egrep Intel
```[/QUOTE]

job@job-ubuntu:~$ cat /proc/cpuinfo | egrep "cpu family" | egrep "15"
cpu family      : 15
job@job-ubuntu:~$ cat /proc/cpuinfo | egrep Intel
vendor_id       : GenuineIntel
model name      : Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
job@job-ubuntu:~$

Thanks

---

### Post by pecanov on 2006-06-15
Seems like the Pentium M build will suit you.

---

### Post by FredB on 2006-06-15
Sorry to be a little annoying, but is there any win in speed ? Because, building using -mpcu=name of cpu is not really an optimizer for speed ;)

---

### Post by Stirling on 2006-06-15
[QUOTE=FredB]Sorry to be a little annoying, but is there any win in speed ? Because, building using -mpcu=name of cpu is not really an optimizer for speed ;)[/QUOTE]
At risk of taking this thread further off-topic, Swiftfox is compiled with -march=cpu not -mcpu=cpu.  -march implies -mcpu but will generate code that can't be run on older processors.

---

### Post by FredB on 2006-06-15
[QUOTE=Stirling]At risk of taking this thread further off-topic, Swiftfox is compiled with -march=cpu not -mcpu=cpu.  -march implies -mcpu but will generate code that can't be run on older processors.[/QUOTE]

Of course. It was a mistake while typing. And the only win of speed is related to using -O3 instead of -O2.

I am using an homemade trunk build. I build it using "--enable-optimize=-O3 -pipe -w -march=pentium4".

And I used the rendering test page from [scragz.com]("http://www.scragz.com/")

With a P4 2.6 ghz + 1 Gb + Ubuntu 6.06 I came from **9.51** (using -Os) to** 6.52** (using -O3). It is slower than Firefox official 1.5.0.4 build (which got something like 4.something), because of using cairo based interface, called Thebes.

---

### Post by joplass on 2006-06-16
uh how do I install this pentium m swiftfox.  a guide somewhere?
thanks

---

