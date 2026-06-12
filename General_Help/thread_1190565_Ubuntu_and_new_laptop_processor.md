---
title: "Ubuntu and new laptop processor"
date: 2009-06-18
forum: General Help
---

### Post by d42 on 2009-06-18
I'm considering getting a Dell Inspiron 15n [(from here)]("http://configure.us.dell.com/dellstore/config.aspx?cs=19&dgvcode=ss&c=US&l=EN&vw=list&oc=dncwzl1&dgc=CJ&cid=7420&lid=0&acd=10550055-1727683-")- It's cheep, does everything I need, and comes pre-installed with ubuntu, hopefully meaning the hardware will be easily compatible with most linux.

For this laptop I have the option of getting a Intel Core 2 Duo. Will this processor "just work" out of the box, or will I have to use a certain Kernel or suchlike? (I'm going to wipe the ubuntu they give me, install my own, and try out a few different distros)  

Plus, sense I don't know much about hardware, would it increase speed more to upgrade from the Pentium Dual Core to the Core 2 Duo, or keep the Pentium and get an extra gb of RAM?

Thanks in advance:D

---

### Post by Hund on 2009-06-18
Every processors works fine. I would go for more RAM, I'm guessing your not going to use it to play any games or any other performance demanding tasks anyway. :)

---

### Post by d42 on 2009-06-18
Ok, thanks. I guess I also meant to ask- will programs in ubuntu be able to take advantage of a duel core system? I've been reading that in windows many programs can't use more than one core, unless you manually set it.

---

### Post by sdennie on 2009-06-18
Most, if not all, distros have support for 8 or more cores.  Most applications on linux are not multithreaded (at least not in a performance orientated way) but, I would still probably go for the Core 2 Duo processor.  It's trivial to upgrade the RAM in the laptop and you can do it later but, in general, the only way to upgrade the CPU is to buy a new laptop.

---

### Post by 3rdalbum on 2009-06-18
Go for the Core 2 Duo, you won't regret it. All processors work on Ubuntu, no trouble there.

Ubuntu has no trouble using multiple CPU cores. It is, however, a fact of life that programs will not be able to use multiple cores unless they are specially written for this. Such programs that are not re-written, will work on one of your cores.

One tactic for getting multi-core use out of single-threaded programs, is to run two instances of the program simultaneously. If you are encoding videos to DivX, you can run two instances of the encoder working on different files (the DivX encoder is single-threaded). However, if you're encoding videos to h.264, the h.264 encoder is multi-threaded, so you just have to set that option. Most other programs that can use multiple threads, will automatically just use them.

---

