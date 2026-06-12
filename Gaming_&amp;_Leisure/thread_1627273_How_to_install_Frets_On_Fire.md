---
title: "How to install Frets On Fire?"
date: 2010-11-21
forum: Gaming &amp; Leisure
---

### Post by Alexander_ on 2010-11-21
Hi! How can i install frets on fire? Can anybody help me?

---

### Post by cchhrriiss121212 on 2010-11-21
Open software center and search for it, then click install.

---

### Post by WienerWuerstel on 2010-11-21
```
sudo apt-get install fretsonfire
```

---

### Post by Alexander_ on 2010-11-22
> **cchhrriiss121212 said:**
> Open software center and search for it, then click install.


Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

---

### Post by Alexander_ on 2010-11-22
> **WienerWuerstel said:**
> ```
sudo apt-get install fretsonfire
```

dosn't work too ):

---

### Post by cchhrriiss121212 on 2010-11-22
Are you shown which packages are the problem? Try opening synaptic and clicking on "reload", "mark all upgrades", then "apply".

---

### Post by Alexander_ on 2010-11-22
> **cchhrriiss121212 said:**
> Are you shown which packages are the problem? Try opening synaptic and clicking on "reload", "mark all upgrades", then "apply".
it needs ''libgl1-mesa-dev''and this needs libgl1-mesa-glx (=7.7.1-1ubuntu2)
i don't know where i can find libgl1-mesa-glx (=7.7.1-1ubuntu2)

---

### Post by cchhrriiss121212 on 2010-11-22
What version of Ubuntu is this? I have 7.9 installed by default on 10.10. And did you try running the updates as shown in post 6?

---

### Post by themusicalduck on 2010-11-22
Try running ```
sudo apt-get install libgl1-mesa-dev
``` and see what it says.

If it fails then try ```
sudo apt-get install libgl1-mesa-glx
``` and try again.

Then try installing Frets on Fire.

---

### Post by Alexander_ on 2010-11-23
> **cchhrriiss121212 said:**
> What version of Ubuntu is this? I have 7.9 installed by default on 10.10. And did you try running the updates as shown in post 6?
i have 10.04
and i don't want to install everything 
which upgrades i have to install ?

---

### Post by cchhrriiss121212 on 2010-11-23
> **Alexander_ said:**
> i don't want to install everything
Running updates will not install everything, it will keep your system current and allow you to install things like fretsonfire. If you have a slow connection then just update the problem packages manually with synaptic or the method themusicalduck posted.

---

### Post by Alexander_ on 2010-11-24
> **cchhrriiss121212 said:**
> Running updates will not install everything, it will keep your system current and allow you to install things like fretsonfire. If you have a slow connection then just update the problem packages manually with synaptic or the method themusicalduck posted.

"reload", "mark all upgrades" and "apply" i install this and it same thing :(
when i try to install libgl1-mesa-dev it needs libgl1-mesa-glx (= 7.7.1-1ubuntu2)
then i install libgl1-mesa-glx and then i try again to install libgl1-mesa-dev and it wants libgl1-mesa-glx (= 7.7.1-1ubuntu2) again

---

### Post by Alexander_ on 2010-12-11
is there anyway i can install frets on fire?

---

### Post by RoflHaxBbq on 2010-12-12
Hmm...

I believe that sudo apt-get usually installs all dependencies.

Try putting this into terminal.

```
sudo apt-get update
```

then

```
sudo apt-get install fretsonfire
```

---

### Post by Alexander_ on 2011-01-15
the same think :(

---

