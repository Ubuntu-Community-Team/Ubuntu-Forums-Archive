---
title: "How to get ZSNES on 9.04"
date: 2009-11-02
forum: Gaming &amp; Leisure
---

### Post by npierce1 on 2009-11-02
This probably seems like a noob question, and it might be, I am an Ubuntu noob but I have tried every suggestion I have seen. Thus, I post for help.

I have tried this in terminal:

```
sudo apt-get install zsnes
```and get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate
```Everywhere I look tells me to look in Synaptic Package Manager (which lists only a gameboy advance emulator) or try that command in terminal, which does not do anything. 

Any suggestions for what to try next? Thanks.

---

### Post by selfier on 2009-11-02
zsnes is only available on 32bit machines, if you are using a 64bit then you are out of luck, unless someone found a way to install the it with all the 32bit libs.

---

### Post by Grishka on 2009-11-03
I've put a 64-bit ZSNES package [here](https://launchpad.net/~thir/+archive/ppa/+files/zsnes_1.510-2.2ubuntu2~ppa1_amd64.deb). it was made for Jaunty, but should work in Karmic as well. to prevent it from segfaulting, it has to be run for the first time with ```
zsnes -ad sdl
```

---

### Post by adzik on 2009-11-04
Thanks for posting the link Grishka.
Works great on 64bit!

---

### Post by afkun on 2010-03-05
Thanks for posting the help on here. I had the exact same problem, but that package saved it. Now, if only I can get the sounds to work!

---

