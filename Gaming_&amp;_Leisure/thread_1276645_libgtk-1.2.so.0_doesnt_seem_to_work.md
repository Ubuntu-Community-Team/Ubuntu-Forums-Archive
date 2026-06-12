---
title: "libgtk-1.2.so.0 doesnt seem to work"
date: 2009-09-27
forum: Gaming &amp; Leisure
---

### Post by dragosal on 2009-09-27
i know this has been posted over and over but  all i find are old posts and i am sorry if the answer is staring me in the face but i am brand new to linux after years on windows but ```
:/usr/local/games/epsxe$ ./epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```
this is all i get and i know i have the file, i downloaded it twice and it says it is installed. i have heard alot of good about linux and want an OS that can play my emuators and maybe some windows games without dragging down my computing power like windows does. i am running ubuntu 9.04  if that helps >.> also i know my grammer sucks but i have been up several extra hours trying to figure it out myself before asking for help

---

### Post by Perfect Storm on 2009-09-27
Are you running 64-bit?

Also give me the output of;
```
ldd /usr/local/games/epsxe/epsxe
```

---

### Post by dragosal on 2009-09-27
```
:~$ ldd /usr/local/games/epsxe/epsxe
    linux-gate.so.1 =>  (0xf7f79000)
    libncurses.so.5 => /lib32/libncurses.so.5 (0xf7f2f000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf7f2b000)
    libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7ed7000)
    libz.so.1 => /usr/lib32/libz.so.1 (0xf7ec1000)
    libgtk-1.2.so.0 => not found
    libgdk-1.2.so.0 => not found
    libgmodule-1.2.so.0 => not found
    libglib-1.2.so.0 => not found
    libXi.so.6 => /usr/lib32/libXi.so.6 (0xf7eb6000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7ea6000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7db7000)
    libm.so.6 => /lib32/libm.so.6 (0xf7d91000)
    libc.so.6 => /lib32/libc.so.6 (0xf7c2d000)
    /lib/ld-linux.so.2 (0xf7f7a000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7c24000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7c20000)
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7c06000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7bee000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf7be8000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7be3000)

```

and i am using 64 bit

---

### Post by dragosal on 2009-09-27
i downloaded and installed a file titled libgtk1.2_1.2.10-18.1build2_amd64.deb which i believed was supposed to contain the three files that list says is missing but apparently that wasn't the case or something

---

### Post by DoktorSeven on 2009-09-27
> **dragosal said:**
> i downloaded and installed a file titled libgtk1.2_1.2.10-18.1build2_amd64.deb which i believed was supposed to contain the three files that list says is missing but apparently that wasn't the case or something

ePSXe is a 32bit executable, so it will need a 32-bit version of GTK 1.2, the -amd64 .deb package won't work.  I'm not certain where to get it though if your 32-bit library packages don't include it.

---

### Post by Perfect Storm on 2009-09-27
You need to use this; [http://ubuntuforums.org/showpost.php?p=2849759&postcount=1](http://ubuntuforums.org/showpost.php?p=2849759&postcount=1)

```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
getlibs /usr/local/games/epsxe/epsxe
```


See if it works. If not please post back with 
```
ldd /usr/local/games/epsxe/epsxe
```

---

### Post by raj7095 on 2009-10-30
I had the same problem. Apparently, you have to install it using the source code from gtk.org.

---

### Post by Supersonic Doom on 2010-12-04
I was having the same problem on my amd64 maverick, ldd output gave

    linux-gate.so.1 =>  (0xf77b6000)
    libncurses.so.5 => /lib32/libncurses.so.5 (0xf775d000)
    libdl.so.2 => /lib32/libdl.so.2 (0xf7759000)
    libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7705000)
    libz.so.1 => /usr/lib32/libz.so.1 (0xf76f0000)
    libgtk-1.2.so.0 => /usr/lib32/libgtk-1.2.so.0 (0xf75a9000)
    libgdk-1.2.so.0 => /usr/lib32/libgdk-1.2.so.0 (0xf7570000)
    libgmodule-1.2.so.0 => not found
    libglib-1.2.so.0 => not found
    libXi.so.6 => /usr/lib32/libXi.so.6 (0xf7561000)
    libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7551000)
    libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7434000)
    libm.so.6 => /lib32/libm.so.6 (0xf740e000)
    libc.so.6 => /lib32/libc.so.6 (0xf72b3000)
    /lib/ld-linux.so.2 (0xf77b7000)
    libSM.so.6 => /usr/lib32/libSM.so.6 (0xf72aa000)
    libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7291000)
    libgmodule-1.2.so.0 => not found
    libglib-1.2.so.0 => not found
    libgmodule-1.2.so.0 => not found
    libglib-1.2.so.0 => not found
    libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7276000)
    libuuid.so.1 => /lib32/libuuid.so.1 (0xf7271000)
    libXau.so.6 => /usr/lib32/libXau.so.6 (0xf726d000)
    libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf7266000)

so then... now what?

edit:
looked up missing package
[http://packages.ubuntu.com/dapper/i386/libglib1.2/download](http://packages.ubuntu.com/dapper/i386/libglib1.2/download)
unpacked into /usr/lib32

now epsxe opens, but shows 

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

---

