---
title: "DosBox start-up problem: libfusion-1.0.so.0"
date: 2009-07-01
forum: Gaming &amp; Leisure
---

### Post by OobNosferatu on 2009-07-01
So I was able to start dosbox to play all my favorite oldies two months ago. In the meantime I installed plenty of softwares, including updating my video driver and a ton of other updates.

Now it doesn't work. Here's the command:

```

sudo dosbox
```

or even

```
dosbox
```

and the output is always:
```
dosbox: error while loading shared libraries: libfusion-1.0.so.0: cannot open shared object file: No such file or directory
```

I tried re-installing, removing then re-install, etc etc etc. Nothing worked. I looked up libfusion-1.0.so.0 and the information I get is extremely useless. 

I looked in usr/lib and found a "libfusion.so" link which is broken... and I tried looking it up in synaptic but found nothing there either.

I'm on Intrepid, 64 bit.

Has anyone else run into this problem before?

---

### Post by dfreer on 2009-07-01
[http://packages.ubuntu.com/search?searchon=contents&keywords=libfusion-1.0.so.0&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libfusion-1.0.so.0&mode=exactfilename&suite=intrepid&arch=any)

The ia32-libs package provides the 32-bit version of the same library, only needed if you are trying to run a 32-bit binary of dosbox. I'd check if libdirectfb-1.0-0 is installed correctly on your system, it may be the symbolic link just needs to be fixed.

---

### Post by OobNosferatu on 2009-07-02
zomg! libdirectfb was it! I went to synaptics and re-installed it, others listed and the binary file as well... perfect! 

Thanks man.

Btw, just for my information, what is this thing and what does it do?

---

### Post by dfreer on 2009-07-03
> DirectFB is a graphics library which was designed with embedded systems in mind. It offers maximum hardware accelerated performance at a minimum of resource usage and overhead.

Don't really know the specifics, but it's basically an API for programs (like games and video players) to draw output to the screen. In the future, whenever bash/ld reports that you are missing a library, check out packages.ubuntu.com. It helps a lot!

---

