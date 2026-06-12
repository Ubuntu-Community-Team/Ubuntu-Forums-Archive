---
title: "error with liblua.so and stepmania"
date: 2005-12-10
forum: Gaming &amp; Leisure
---

### Post by arcanistherogue on 2005-12-10
So, I want to play stepmania.  I had played this on windows before and loved it.  If you don't know, this is a DDR clone for many different platforms including Linux and OS X.  

So, I got a .tar.gz file of all the binaries, and as root put these in /usr/local/games/stepmania, then I ran the "stepmania" executable.

I got the following error:

```
john@kubuntu:/usr/local/games/stepmania/StepMania-3.9-rc3$ ./stepmania
./stepmania: error while loading shared libraries: liblua.so: cannot open shared object file: No such file or directory

```

So, I went into kynaptic and installed all the lua packages I could find, including liblua-50.so

I run it again, and get the same error.

How do I get this working?

Thanks alot.

---

### Post by Perfect Storm on 2005-12-10
Just ran it pefect in the home directory. 
It could be you need to make a run script for it.

---

### Post by arcanistherogue on 2005-12-10
how would I go about doing that?

also, what version and where did you get it?  I got 3.9 from softpedia.

---

### Post by Harleen on 2005-12-10
Do you have that missing file (probably a hard link) on your hard disk? It has to be located either in /usr/lib or /usr/local/lib.

If you do, run "sudo ldconfig". (updates library informations)
If not, create a link with that name pointing to the appropriate file:

cd /usr/lib
sudo ln -s liblua-50.so liblua.so
sudo ldconfig

Maybe the arguments to the ln command have to be switched. I always mess that up... But it will complain, if they are in the wrong order.

---

### Post by arcanistherogue on 2005-12-10
Ok, I downloaded from stepmania.com and now I get the following errors when I run that one instead:

```
john@kubuntu:/usr/local/games/stepmania/StepMania-3.9$ ./stepmania
StepMania 3.9
Log starting 2005-12-10 20:36:52
Loading window: gtk
OS: Linux ver 020612
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.3.5
Threads library: NPTL 2.3.5
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).
ALSA Driver: 0: NVidia CK8S [CK8S], device 0: Intel ICH [NVidia CK8S], 0/1 subdevices avail
ALSA Driver: 0: NVidia CK8S [CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958], 1/1 subdevices avail
Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
Mixing 0.000000 ahead in 0 Mix() calls
Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy
Language: english
Theme: default
Error: Couldn't find a sound driver that works

```

...A bit more help please? :p

---

### Post by Harleen on 2005-12-10
Just follow the advices in one of the countless "No sound in..."-threads. ;)

This one may work for you:
artsdsp -m ./stepmania

---

### Post by arcanistherogue on 2005-12-10
K, I'll try that when I'm done with configuring karamba <_<

---

### Post by arcanistherogue on 2005-12-10
eh, I got an error saying that artsdsp only works for binaries? :X

---

