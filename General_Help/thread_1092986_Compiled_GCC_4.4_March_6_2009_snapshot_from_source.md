---
title: "Compiled GCC 4.4 March 6 2009 snapshot from source and messed my whole system up"
date: 2009-03-11
forum: General Help
---

### Post by Neo_The_User on 2009-03-11
This is a double post of [http://ubuntuforums.org/showthread.php?t=1091997](http://ubuntuforums.org/showthread.php?t=1091997) but since this topic is busier, I wanted to post it in here. Mods and admins, please delete [http://ubuntuforums.org/showthread.php?t=1091997](http://ubuntuforums.org/showthread.php?t=1091997) and if this is in violation of the rules for double posting and or making duplicate threads, feel free to give me a warning as I understand this is most likely wrong.

**[SIZE="5"]_I AM DESPERATE!_[/SIZE]**

Hi. I compiled GCC 4.4 from source and it was i686 optimized, X86, 32-bit architecture and I ran ./configure --prefix=/usr, make, sudo make install, no errors. It all worked wonderfully. After I reboot, HAL, Dbus, and networking don't work. I run sudo Xorg -configure to not use HAL, keyboard and mouse work. Networking still doesn't. I spend about 10 minutes trying to fix it and I decide to do a fresh install. Why did GCC 4.4 break my system? How can I prevent it from happening? How can I have GCC 4.4 and all its sub applications compiled from source and not have problems?

My goal of doing all this: To compile a kernel with GCC 4.4 and G++ 4.4

For those who want to help (Linux beginners do not try this)

```

cd && mkdir devel && cd devel && wget http://gcc.releasenotes.org/snapshots/LATEST-4.4/gcc-4.4-20090306.tar.bz2 && tar xjf gcc-4.4* && cd gcc* && sudo apt-get build-dep libstdc++5 libstdc++6 gcc g++ && ./configure --prefix=/usr && make && sudo make install

```

Read that code line carefully so you know what you're about to do! IF IN DOUBT, DON'T DO THAT COMMAND! BY THE WAY, IT WILL TAKE OVER 7 HOURS DEPENDING ON CPU CLOCK SPEED!

---

### Post by dcstar on 2009-03-11
> **Neo_The_User said:**
> 
.........
1) **Why did GCC 4.4 break my system?**

2) **How can I prevent it from happening?**

3) **How can I have GCC 4.4 and all its sub applications compiled from source and not have problems?**

My goal of doing all this: To compile a kernel with GCC 4.4 and G++ 4.4

For those who want to help (Linux beginners do not try this)

```

cd && mkdir devel && cd devel && wget http://gcc.releasenotes.org/snapshots/LATEST-4.4/gcc-4.4-20090306.tar.bz2 && tar xjf gcc-4.4* && cd gcc* && sudo apt-get build-dep libstdc++5 libstdc++6 gcc g++ && ./configure --prefix=/usr && make && sudo make install

```


1) Probably Because YOU installed software outside the dpkg system and then tried to use that same system to somehow figure out what you did.

2) Stop doing things you don't understand.

3) Wait until someone creates a .deb package (with all dependencies worked out) and makes it available for the Ubuntu version you are running.

---

### Post by Neo_The_User on 2009-03-11
well gcc 4.4 aint in the ubuntu repos and when it is, it wont be i686 optimized. btw i develop for dri.freedesktop.org and i need gcc 4.4 now for development purposes.

---

### Post by thtrgremlin on 2009-03-11
I was reading a guide recently about KDE development, ant it says ALWAYS build core components in a virtual machine because they have a strong likelyhood of breaking your system otherwise. Personally, I would use a chroot environment inside the virtual one for at least testing purposes.

GCC is a very important core part of the system in many ways. One of the whole issues with a Linux distribution is that everything is tested such that certain versions of stuff work together correctly. Updating individual programs sometimes will make that program break, so when it is something like GCC or the kernel, everything that can depend on that....  **** rolls downhill to put it simply.

Just as a suggestion, Gentoo is much more well designed to be tinkered with at that level and not crack, not to mention Gentoo unstable is Sweeny Todd / Dexter bleeding edge for having the very latest versions of things. It is not for the faint of heart, but it may give you more the kind of environment to play in you are looking for.

No offence to Ubuntu, and would be interested to hear people disagree with me, but Ubuntu is just too bulky (relatively) to just go in and just recompile and update gcc or the kernel. imho.

Also, you didn't just run that like you posted it, did you? you did run those each one at a time, right?

---

### Post by Neo_The_User on 2009-03-11
> **thtrgremlin said:**
> 
Also, you didn't just run that like you posted it, did you? you did run those each one at a time, right?

I didn't run it as posted. your explanation cleared it up for me on why. thank you.

---

### Post by MaxIBoy on 2009-03-11
If you're performing a complex series of steps, use the "&&" feature. That will stop the operation at the first step that goes wrong. In other words, 
This will screw things up:
```
cp /etcv/apt/preferences /etc/apt/preferences.bak; dangerous_command /etc/apt/preferences
```Because this person typed "etc" wrong in the cp command, and now /etc/apt/preferences doesn't have a backup file.

Whereas this:
```
cp /etcv/apt/preferences /etc/apt/preferences.bak && dangerous_command /etc/apt/preferences
```Won't screw things up, because the "cp" command will fail and stop you from messing with the preferences file without doing a backup.


Simplified example, same concept.


Also, yeah, messing with GCC is a major no-no. Most libraries that are imported by other applications act wierd unless compiled with a compatible version of GCC. So if program A was compiled with GCC 4.x and it uses libvorbis for sound, and libvorbis was compiled with GCC 3.x, you're asking for trouble. Leave this stuff up to the repository maintainers.

---

### Post by Neo_The_User on 2009-03-11
I didn't use the && feature for the last time. Would it not break my system if I compile GCC 4.3.3 from source?

---

### Post by heindsight on 2009-03-11
If you really need to build the latest gcc from source, install it in /usr/local rather than /usr. That way it won't interfere with anything else and if you need to use the version you compiled rather than the default ubuntu gcc then you can call it by it's full path...

---

### Post by Neo_The_User on 2009-03-11
> **heindsight said:**
> If you really need to build the latest gcc from source, install it in /usr/local rather than /usr. That way it won't interfere with anything else and if you need to use the version you compiled rather than the default ubuntu gcc then you can call it by it's full path...

How can I call it by its full path only for compiling a kernel? I'm so happy I FINALLY came across somebody who knows what they are talking about. Thanks.

---

### Post by heindsight on 2009-03-11
> **Neo_The_User said:**
> How can I call it by its full path only for compiling a kernel? I'm so happy I FINALLY came across somebody who knows what they are talking about. Thanks.

Actually a lot of people around here know what they're talking about.

If you want to change the C compiler used to compile *anything* edit the makefile and change the value of the CC variable.
EDIT:
Or just set the CC environment variable to the compiler you want to use when you run make:
```
CC=/usr/local/bin/gcc make
```

---

### Post by Neo_The_User on 2009-03-11
And I set the CC variable to /usr/local? or /usr/local/gcc4.4-i686 or whatever?

---

### Post by heindsight on 2009-03-11
> **Neo_The_User said:**
> And I set the CC variable to /usr/local? or /usr/local/gcc4.4-i686 or whatever?

It might help if you read the make documentation. Install make-doc:
```
sudo apt-get make-doc
```
and do
```
info make
```

In there the CC variable is described as follows:
> `CC'
     Program for compiling C programs; default `cc'.

thus, the CC variable should either give the full path to the C compiler (if it's not in the PATH or if some other program of the same name can be found earlier in the PATH), or just the program name (if it's in the PATH and nothing else in the PATH will 'override' it)

---

### Post by Neo_The_User on 2009-03-11
Ah so I actually link it to the gcc 4.4 binary I see.

---

