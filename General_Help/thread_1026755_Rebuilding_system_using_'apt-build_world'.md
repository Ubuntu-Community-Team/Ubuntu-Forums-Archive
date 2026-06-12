---
title: "Rebuilding system using 'apt-build world'"
date: 2008-12-31
forum: General Help
---

### Post by JeremyTheGeek on 2008-12-31
Hey everyone. Yesterday I decided to try and optimize my system for my specific architecture using 'apt-build world' using instructions from 

[http://polishlinux.org/linux/debian/apt-build-optimize-debian/](http://polishlinux.org/linux/debian/apt-build-optimize-debian/)

Now every few hours or so it dies when it comes into contact with a package that it can't find the source to. At this point I need to remove the specific package from /etc/apt/apt-build.list and restart the process. Now my question is this.

Does apt-build world start from the beginning and recompile everything or does it skip back to where it left off?

If it starts at the beginning is there an easy way for me to find any package that don't have its source available and automatically remove it from the list? I've been compiling for 30+ hours using the above method and ive only reached gcc (which is where it chocked because it can't find source)

Please help me out here. I am very tired :/
-=Germ=-

---

### Post by dcstar on 2008-12-31
> **JeremyTheGeek said:**
> Hey everyone. Yesterday I decided to try and optimize my system for my specific architecture using 'apt-build world' using instructions from 

[http://polishlinux.org/linux/debian/apt-build-optimize-debian/](http://polishlinux.org/linux/debian/apt-build-optimize-debian/)
.........

Why do you think doing that will "optimize my system for my specific architecture"?

---

### Post by JeremyTheGeek on 2009-01-01
> **dcstar said:**
> Why do you think doing that will "optimize my system for my specific architecture"?

No idea really. I was just bored and had a few spare hours on my hands so I thought id try something out. BAD IDEA.

Still compiling XD

---

### Post by dcstar on 2009-01-01
> **JeremyTheGeek said:**
> No idea really. I was just bored and had a few spare hours on my hands so I thought id try something out. BAD IDEA.


All it will do is compile the exact same .deb packages that are already in the repositories, it is a hang-over from the days where everybody basically had to compile their own packages from source and sometimes a new compiler version would give you a performance boost if you recompiled everything.

As you can see now, it is a total waste of time and resources these days.

---

### Post by JeremyTheGeek on 2009-01-01
So. If I just Ctrl-C it will there be any adverse side effects?

---

