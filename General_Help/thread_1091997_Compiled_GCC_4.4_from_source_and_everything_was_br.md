---
title: "Compiled GCC 4.4 from source and everything was broken"
date: 2009-03-09
forum: General Help
---

### Post by Neo_The_User on 2009-03-09
**[SIZE="4"]_EDIT! SOLVED! BAD HARD DRIVE!_[/SIZE]**

Hi. I compiled GCC 4.4 from source and it was i686 optimized, X86, 32-bit architecture and I ran ./configure --prefix=/usr, make, sudo make install, no errors. It all worked wonderfully. After I reboot, HAL, Dbus, and networking don't work. I run sudo Xorg -configure to not use HAL, keyboard and mouse work. Networking still doesn't. I spend about 10 minutes trying to fix it and I decide to do a fresh install. Why did GCC 4.4 break my system? How can I prevent it from happening? How can I have GCC 4.4 and all its sub applications compiled from source and not have problems?

My goal of doing all this: To compile a kernel with GCC 4.4 and G++ 4.4

For those who want to help (Linux beginners do not try this)

```

cd && mkdir devel && cd devel && wget http://gcc.releasenotes.org/snapshots/LATEST-4.4/gcc-4.4-20090306.tar.bz2 && tar xjf gcc-4.4* && cd gcc* && sudo apt-get build-dep libstdc++5 libstdc++6 gcc g++ && ./configure --prefix=/usr && make && sudo make install

```

Read that code line carefully so you know what you're about to do! IF IN DOUBT, DON'T DO THAT COMMAND! BY THE WAY, IT WILL TAKE OVER 7 HOURS DEPENDING ON CPU CLOCK SPEED!

---

### Post by InfinityCircuit on 2009-03-09
Or just:

```
aptitude install gcc-snapshot
```

---

### Post by Neo_The_User on 2009-03-09
> **InfinityCircuit said:**
> Or just:

```
aptitude install gcc-snapshot
```

That's older than 4.3. It's 4.2. sudo apt-get install gcc-4.3 is newer than that even.

---

### Post by Neo_The_User on 2009-03-10
bump. please help. has anybody compiled ANY version of gcc from source and their system worked afterwards?

Problem: gcc 4.4 breaks my system.

What I want to accomplish: compile a kernel under 700K using gcc 4.4 and then continue doing mesa and libdrm development with gcc 4.4.

---

### Post by Neo_The_User on 2009-03-10
nobody compiles gcc eh? bump bump bump!! Ugh ok nobody wants to help me out eh? I help others and don't get back much. Well that sure sucks. I'll be compiling and trying to debug this problem myself on my other machines. If anybody feels like giving me a little tip of advice, suggestion, or an explanation on why gcc broke my system, feel free to post! Nobody is stopping you!

---

### Post by Culexian on 2009-03-17
I've compiled gcc from source a few times now. You say everything was broken, in what way?

---

### Post by Neo_The_User on 2009-03-17
networking didn't work, display screens were completely blanked, everything you could imagine, right after ubuntu finishes starting up. i still want gcc 4.4 but i'm not compiling it until i find out what happened.

---

### Post by Culexian on 2009-03-18
Did you run 'sudo ldconfig' after installing?

If you ran 'make -k check' after the build, were there many errors?(That's a command that will take quite a while too)

If there were just a few, that's normal.

---

### Post by Neo_The_User on 2009-03-18
OK I was wrong this whole time. My hard drive got corrupted which is why my system broke. I compiled the gcc suite to /usr again and it works wonderfully. Just coincidence that I was compiling gcc 4.4 right before my entire system broke. But yeah... wrong diagnostic.

---

### Post by Culexian on 2009-03-23
Glad that you got it sorted out. How's the performance of 4.4? I noticed a large jump in performance from 4.3.2 to 4.3.3.

---

### Post by Neo_The_User on 2009-03-23
> **Culexian said:**
> Glad that you got it sorted out. How's the performance of 4.4? I noticed a large jump in performance from 4.3.2 to 4.3.3.

Well I compiled about 6 kernels using GCC 4.4, Xfce 4.6 stable from source, and some other things and its really good. I also do lots of tweaking for the Makefiles. Please visit this page for more info:

[http://neo-technical.wikispaces.com/gcc+4.4+ubuntu](http://neo-technical.wikispaces.com/gcc+4.4+ubuntu)

Near the bottom you should see where to put the optimization flags for it. 

Best regards.

---

