---
title: "FCE Ultra Performance Issues"
date: 2007-05-22
forum: Gaming &amp; Leisure
---

### Post by nythacker on 2007-05-22
I have a dual-boot (Windows/Ubuntu) PC and I have some performance problems with the FCEU emulator v0.98.12. After compiling the FCEU emulator from source and running it on Ubuntu, I experience extremely slow performance as compared to the Windows binary of the same version which runs perfectly speedy on my Windows 2000 partition.

Has anyone experienced this problem before?

So how come the compiled version of FCEU on Ubuntu Linux runs 1000x slower than the Windows version? Test it out yourself...

FYI. I have an Athlon "Thunderbird" 1.2 Ghz processor and 768MB RAM.

---

### Post by DoktorSeven on 2007-05-22
When you compiled it from source, did you use the --with-opengl configure option? (./configure --with-opengl)

Doing it without that will use software drawing of the emulator window, which is slower; Windows will do so by default using DirectDraw, which is why it's faster.

(An aside if you're not aware: you'll need working 3d / direct rendering in Linux (terminal-> **glxinfo | grep direct** should return direct rendering: Yes).  If it doesn't, search for how to enable this with your card.)

---

### Post by nythacker on 2007-05-23
> **DoktorSeven said:**
> When you compiled it from source, did you use the --with-opengl configure option? (./configure --with-opengl)

No, I haven't tried compiling FCEU with that option yet. I will try it and see how it goes. Thanks very much for the advice.

I did some further research though regarding my FCEU problem and found out that compiling FCEU with newer versions of the GCC compiler on AMD Athlon processors produces poor executables. I dunno why this is the case. Here's the link for your reference:

**[COLOR="Blue"][http://fceultra.sourceforge.net/faq.php]("http://fceultra.sourceforge.net/faq.php")[/COLOR]**

With this in mind, has anybody figured out what CPU-specific optimization flags are used to compile FCEU with AMD Athlon processors?

Any help would be greatly appreciated.

Thanks!

---

### Post by DoktorSeven on 2007-05-23
```

export CFLAGS="-O2 -march=athlon-xp -pipe"
export CXXFLAGS="-O2 -march=athlon-xp -pipe"
./configure --with-opengl

```

If that gives you problems try replacing "athlon-xp" with just "athlon".

---

### Post by nythacker on 2007-05-23
> **DoktorSeven said:**
> ```

export CFLAGS="-O2 -march=athlon-xp -pipe"
export CXXFLAGS="-O2 -march=athlon-xp -pipe"
./configure --with-opengl

```

If that gives you problems try replacing "athlon-xp" with just "athlon".

DoktorSeven,

Thanks very much for trying to help me out here. I did some research on optimizing GCC, took your advice, and modified your suggestion to the following taking in consideration that I have an AMD Athlon "Thunderbird" 1.2 Ghz processor:

```

export CFLAGS="-O2 -march=athlon-tbird -pipe"
export CXXFLAGS="-O2 -march=athlon-tbird -pipe"
./configure --with-opengl

```

Tried out the new FCEU executable and the performance was better but a bit choppy (like skipping a few frames here and there) and in no way as good as the Windows binary of the same version which run smoothly and at full speed on my less than stellar 1Ghz laptop running Windows 2000.

---

### Post by DoktorSeven on 2007-05-23
I'm running fceu on an old P4 1.5GHz proc and have never noticed any choppiness/frame skipping at all.  Do you have 3d enabled for your videocard which helps the OpenGL rendering (as noted in my first reply above), or if you do, do you have 3d desktop effects on (those should be disabled to play games)?

---

### Post by nythacker on 2007-05-24
> **DoktorSeven said:**
> I'm running fceu on an old P4 1.5GHz proc and have never noticed any choppiness/frame skipping at all.  Do you have 3d enabled for your videocard which helps the OpenGL rendering (as noted in my first reply above), or if you do, do you have 3d desktop effects on (those should be disabled to play games)?

Yes, I currently have an old 64MB ATI Radeon 7200 video card and 3D is enabled as I use Beryl without any problems at all. When I play games, I always turn off Beryl as I've read a lot of posts of it giving performance problems on games.

BTW, I'm currently running the Windows binary of FCEU v0.98.12 on Wine without any problems and it performs just as fast and as smooth as it would in Windows. This would be my last resort though if nothing on earth can fix the performance problems that I have mentioned running the native version of FCEU v0.98.12 on Ubuntu.

---

