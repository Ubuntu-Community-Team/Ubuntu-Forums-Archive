---
title: "wine 0.9.15 error"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by ELD on 2006-06-13
I keep getting this error when going to the audio tab in winecfg

> 
Creating link /home/liam/.kde/socket-ubuntu.
can't create mcop directory


Any ideas?

---

### Post by frying_fish on 2006-06-13
Crazy, I get the exact same error.  There was a fix a while back about changing some libraries, but that shouldn't be causing that issue, especially now that I got passed the issue of the libraries, if you find a solution please let me know.

---

### Post by DoktorSeven on 2006-06-13
I had a similar error:
```
$ winecfg
Link points to "/tmp/ksocket-stephen"
can't create mcop directory

```
Doing a **mkdir /tmp/ksocket-stephen** (stephen = my username) solved it.

---

### Post by ELD on 2006-06-14
[QUOTE=DoktorSeven]I had a similar error:
```
$ winecfg
Link points to "/tmp/ksocket-stephen"
can't create mcop directory

```
Doing a **mkdir /tmp/ksocket-stephen** (stephen = my username) solved it.[/QUOTE]

I will try something like that and let you know.

What i don't get is the .kde, since im on gnome...

---

### Post by gi2k15 on 2006-06-20
[QUOTE=DoktorSeven]I had a similar error:
```
$ winecfg
Link points to "/tmp/ksocket-stephen"
can't create mcop directory

```
Doing a **mkdir /tmp/ksocket-stephen** (stephen = my username) solved it.[/QUOTE]
This solved the problem here too.

---

### Post by lleonard on 2006-06-20
[QUOTE=DoktorSeven]I had a similar error:
```
$ winecfg
Link points to "/tmp/ksocket-stephen"
can't create mcop directory

```
Doing a **mkdir /tmp/ksocket-stephen** (stephen = my username) solved it.[/QUOTE]

I've fixed that error before using that technique too.  

I've also seen a solution for GNOME users posted elsewhere (probably here on ubuntuforums.org) that suggests running kcontrol and turning off the sound system.  Sound will still work in GNOME.  I tried it with success.

---

### Post by ELD on 2006-06-21
Just a note:

"mkdir /home/liam/.kde/socket-ubuntu"

Doing that in terminal fixes it, there was no socket-ubuntu directory so it wouldn't work, works fine now :)

---

### Post by sewpafly on 2006-06-30
I ran ksocket (and disabled sound) after I got this error and then another one complaining about not being able to create a link (Creating link /home/xxxxx/.kde/socket-ubuntu). and that fixed that problem.

---

### Post by DaveNF2G on 2006-07-26
The mkdir option didn't work for me.  Here is what I get:

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

I installed JACK using the Synaptic manager but still get the error above.

---

### Post by telperion on 2006-08-17
for me:
mkdir /tmp/ksocket-YOURSERNAME

winecfg
audio--> esd (ESS)

now work 
with esd mixer in gnome sound preferences

---

### Post by jamespi on 2006-08-20
i had the same error in GAIM. it turned out i needed a directory .kde/socket-hal9000

which is the hostname of my computer. so maybe it was working for you people used ubuntu or your username because they were the same as your hostname.

---

### Post by cccc on 2006-10-15
under dapper drake I'm still geting this error:```

# winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

jack and jack-tools are installed

---

### Post by cccc on 2006-10-15
after installing:```

libjack0.100.0-0 - JACK Audio Connection Kit (libraries)
libjack0.100.0-dev - JACK Audio Connection Kit (development files)
libjackasyn-dev - Development files for libjackasyn
libjackasyn0 - The Asynchrounous JACK Library
```
the error of libjack is gone.

---

