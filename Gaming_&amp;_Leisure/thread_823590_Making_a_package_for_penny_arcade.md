---
title: "Making a package for penny arcade"
date: 2008-06-09
forum: Gaming &amp; Leisure
---

### Post by lunarcloud on 2008-06-09
Hey, I'm planning on making a package for penny arcade: on the rain slick precipice of darkness episode one.

So I understand I need to make a mini linux structure (y'know like pennyarcade/usr/bin/games/ ) and that stuff... but how do I make it show up in the menu after install?

Where are these .desktop files for the menu items located?

---

### Post by Polygon on 2008-06-09
piracy is bad.

however, to create gnome menu entries, maybe this post will help you out.

[http://ubuntuforums.org/showthread.php?t=75606](http://ubuntuforums.org/showthread.php?t=75606)

---

### Post by dfreer on 2008-06-10
If your asking where to place the .desktop file so that it shows in the gnome-menu, it's /usr/share/applications/

I'm sure your creating your .deb for ease of future reinstallations, just make sure that you don't pirate the software in the process. It's a cheap download, and they are among the few that actually release their program for linux 32-bit and 64-bit.

---

### Post by lunarcloud on 2008-07-09
I'm going to take the files straight from the tar, The demo IS the full version, You download it and then activate it.
 I will not include my activation key. 

> **Polygon said:**
> piracy is bad.
I don't pirate games, they are the one form of proprietary software I support. (And on that same road pirating software hurts open source).
I never said I was pirating. Assuming is bad too. lol.

                                                  
> **dfreer said:**
> If your asking where to place the .desktop file so that it shows in the gnome-menu, it's /usr/share/applications/

I assume the folder for the gnome menu entries are the same as the KDE ones? because I haven't used gnome for 2 years. Happy KDE 4.1 (beta) user.

> **dfreer said:**
> they are among the few that actually release their program for linux 32-bit and 64-bit.

Really? It supports 64-bit? I just ran it and assumed I used getlibs or something. Thats nice of them. That's why it worked swimmingly.

---

### Post by dfreer on 2008-07-10
> **zarquad said:**
> I assume the folder for the gnome menu entries are the same as the KDE ones? because I haven't used gnome for 2 years. Happy KDE 4.1 (beta) user.

When I made my ZSNES/pSX packages back before KDE 4, they would show up in both. I doubt they changed it but you never know.

> **zarquad said:**
> Really? It supports 64-bit? I just ran it and assumed I used getlibs or something. Thats nice of them. That's why it worked swimmingly.

Not sure on how Penny Arcade releases their games, you could very well be running the 32-bit version for all I know. Generally, either they will release both a 32-bit and 64-bit version, or they will throw both in there and have some sort of script to install the right one.

One way to check would be to run ldd on the binary; not only will this tell you if it's using 32-bit or 64-bit libs, it'll let you know what it depends on so you can make a proper control file.

---

### Post by acoustibop on 2008-07-10
Don't forget that On the Rain-Slick Precipice of Darkness is started with a script that enables a couple of libs that come with the game.  So, since you can't use ldd with the script, only with the executive, it will always report those two as unsatisfied requirements. ;)

---

### Post by lunarcloud on 2008-07-24
Alright, so I'm nearly there. Thanks for all the help.

When I use ldd, it gives me a list, some of these are in their folder, some are 32 bit libs... is there a way to find out which package each of these libs are from?

```
linux-gate.so.1 =>  (0xffffe000)                                        
        libfmodex.so => not found                                               
        libfmodevent.so => not found                                            
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7e40000)              
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7d9c000)                        
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf7d96000)                
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7ca3000)                
        libm.so.6 => /lib32/libm.so.6 (0xf7c7e000)                              
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7c72000)                  
        libc.so.6 => /lib32/libc.so.6 (0xf7b23000)                              
        libdl.so.2 => /lib32/libdl.so.2 (0xf7b1f000)                            
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7b07000)                  
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7a20000)                      
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf795d000)                
        libdirectfb-1.0.so.0 => /usr/lib32/libdirectfb-1.0.so.0 (0xf78f9000)    
        libfusion-1.0.so.0 => /usr/lib32/libfusion-1.0.so.0 (0xf78f1000)        
        libdirect-1.0.so.0 => /usr/lib32/libdirect-1.0.so.0 (0xf78de000)        
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf6dc9000)                
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6dc7000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6db8000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6db0000)
        /lib/ld-linux.so.2 (0xf7ef4000)
        libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf6dae000)
        libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6d96000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6d93000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6d8d000)

```

---

### Post by dfreer on 2008-07-24
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Use the "Search the Contents of Packages" Section, just paste the library name in like this:
[http://packages.ubuntu.com/search?searchon=contents&keywords=libSDL-1.2.so.0&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=libSDL-1.2.so.0&mode=exactfilename&suite=hardy&arch=any)
You can see that **libSDL-1.2.so.0** is part of the libsdl1.2debian-* packages for 32-bit and 64-bit, and the 32-bit library is provided for 64-bit users in the package ia32-libs.

Furthermore, this site is very useful if you need to know what version of each library is in each release (for example if you wanted to create a .deb for dapper users), or you can use [http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) if you are releasing for Debian users (useful to run a debian system to ensure compatibility, I noticed my ZSNES binaries compiled in Ubuntu sometimes would not run on Debian and I had to recompile them).

---

### Post by Funk Phenomena on 2008-08-04
Fwiw, I had to copy the files from linuxlibs to /usr/lib32 to get it to work in Ubuntu 64.

---

