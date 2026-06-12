---
title: "zsnes in Hardy Heron"
date: 2008-09-20
forum: Gaming &amp; Leisure
---

### Post by Rabiah on 2008-09-20
I've been trying to install this, but cant figure out how, I tried sudo apt-get and through add/remove but it doesn't seem to work.

---

### Post by Meow27 on 2008-09-21
cant you just get it from synaptic?

(just fyi the saves are in /home/username/.zsnes)

if that fails, try snes9x.

if that fails, try using zsnes (windows) in Wine

if that fails i cant help you anymore :(

---

### Post by mcallenSchmee on 2008-09-21
Do you not know how to install programs in general? Or are you getting errors? Are you asking how to install it? (Your post isn't very clear what your problem is or what you want)

Typing this into the terminal will install zsnes
```
sudo apt-get install zsnes 
```

---

### Post by eragon100 on 2008-09-21
Get it from here, the one in add/remove doesn't give any sound in hardy:

[http://board.zsnes.com/phpBB2/viewtopic.php?p=168959](http://board.zsnes.com/phpBB2/viewtopic.php?p=168959)

(and, no, you don't have to worry about the libraries)

Just download and extract the folder for your processor, than run the program from there (it's the blue icon called zsnes)

---

### Post by Holonet on 2008-09-21
If you are using 64-bit, there isn't a package available.  It can be done as shown in this thread:

[http://ubuntuforums.org/showthread.php?t=771290](http://ubuntuforums.org/showthread.php?t=771290)

If you have 32-bit, make sure you have the necessary repositories activated (I'm not sure which one zsnes is in), and the methods already mentioned should work.

---

