---
title: "Help With OpenMortal Please"
date: 2008-08-28
forum: Gaming &amp; Leisure
---

### Post by bipolaric on 2008-08-28
hi people, Linux Noob here, I have just downloaded openmortal-0.7.tar.bz2

but I haven't a clue what to do with this package, is there anyone that can give me a step-by-step guide as to how to install this game.

Any help would be gratefully appreciated - Thanks Mark :)

---

### Post by dudeofthedead on 2008-08-28
```
tar xjvf openmortal-0.7.tar.bz2
cd openmortal-0.7
./configure
make
su # for Ubuntu that would be 'sudo make install'
make install
exit
make clean

```

You may need to apt-get/aptitude a couple of dependecies in the process.

---

### Post by bipolaric on 2008-08-28
hi i tried the first line in the terminal, and I got this.......
$ tar xjvf openmortal-0.7.tar.bz2
tar: openmortal-0.7.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
What does this mean ? this is alien to me :(

---

### Post by dudeofthedead on 2008-08-28
cd to the right directory first!  I'm assuming it's sitting on your Desktop, so try this.

```
cd ~/Desktop
```

then the rest of the shell script...

---

### Post by Xcursion666 on 2010-12-07
i converted the rpm package using alien then i installed it on my laptop and when i run the game in terminal i get this error 
robert@laptop:~$ openmortal
openmortal: error while loading shared libraries: libperl.so: cannot open shared object file: No such file or directory
it worked fine on my desktop though
](*,)

---

### Post by Perfect Storm on 2010-12-07
Necromancing. Thread closed.

---

