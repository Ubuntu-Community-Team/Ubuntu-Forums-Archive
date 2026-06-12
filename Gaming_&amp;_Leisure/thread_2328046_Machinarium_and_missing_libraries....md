---
title: "Machinarium and missing libraries..."
date: 2016-06-16
forum: Gaming &amp; Leisure
---

### Post by CVGH on 2016-06-16
Hi!

I'm trying to figure out how to install the missing packages.


```
ister@jupitermining:~/GOG Games/Machinarium/game$ ldd Machinarium    
     linux-gate.so.1 =>  (0xf77af000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf769c000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf767c000)
    libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf7544000)
    libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf752c000)
    libXt.so.6 => /usr/lib/i386-linux-gnu/libXt.so.6 (0xf74cc000)
    libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf742c000)
    libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf73ec000)
    libgtk-x11-2.0.so.0 => /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0 (0xf6f7c000)
    libgdk-x11-2.0.so.0 => /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0 (0xf6ecc000)
    libatk-1.0.so.0 => /usr/lib/i386-linux-gnu/libatk-1.0.so.0 (0xf6ea4000)
    libgdk_pixbuf-2.0.so.0 => /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0 (0xf6e7c000)
    libpangocairo-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0 (0xf6e6c000)
    libpango-1.0.so.0 => /usr/lib/i386-linux-gnu/libpango-1.0.so.0 (0xf6e1c000)
    libcairo.so.2 => /usr/lib/i386-linux-gnu/libcairo.so.2 (0xf6cf4000)
    libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf6c9c000)
    libgmodule-2.0.so.0 => /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0 (0xf6c94000)
    libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf6c8c000)
    libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf6b7c000)
    libnss3.so => not found
    libsmime3.so => not found
    libssl3.so => not found
    libplds4.so => not found
    libplc4.so => not found
    libnspr4.so => not found
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf6b34000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf6b14000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6964000)
    libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf6954000)
    /lib/ld-linux.so.2 (0x5661b000)
    libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf692c000)
    libSM.so.6 => /usr/lib/i386-linux-gnu/libSM.so.6 (0xf691c000)
    libICE.so.6 => /usr/lib/i386-linux-gnu/libICE.so.6 (0xf68fc000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf68dc000)
    libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf68b4000)
    libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf6884000)
    libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf687c000)
    libgio-2.0.so.0 => /usr/lib/i386-linux-gnu/libgio-2.0.so.0 (0xf66f4000)
    libpangoft2-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0 (0xf66dc000)
    libXinerama.so.1 => /usr/lib/i386-linux-gnu/libXinerama.so.1 (0xf66d4000)
    libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xf66c4000)
    libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xf66b4000)
    libXcursor.so.1 => /usr/lib/i386-linux-gnu/libXcursor.so.1 (0xf66a4000)
    libXcomposite.so.1 => /usr/lib/i386-linux-gnu/libXcomposite.so.1 (0xf669c000)
    libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf6694000)
    libthai.so.0 => /usr/lib/i386-linux-gnu/libthai.so.0 (0xf6684000)
    libpixman-1.so.0 => /usr/lib/i386-linux-gnu/libpixman-1.so.0 (0xf65d4000)
    libxcb-shm.so.0 => /usr/lib/i386-linux-gnu/libxcb-shm.so.0 (0xf65cc000)
    libxcb-render.so.0 => /usr/lib/i386-linux-gnu/libxcb-render.so.0 (0xf65bc000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf65ac000)
    libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf65a4000)
    libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf6564000)
    libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf655c000)
    libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf6554000)
    libuuid.so.1 => /lib/i386-linux-gnu/libuuid.so.1 (0xf654c000)
    libselinux.so.1 => /lib/i386-linux-gnu/libselinux.so.1 (0xf6524000)
    libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf650c000)
    libharfbuzz.so.0 => /usr/lib/i386-linux-gnu/libharfbuzz.so.0 (0xf64b4000)
    libdatrie.so.1 => /usr/lib/i386-linux-gnu/libdatrie.so.1 (0xf64a4000)
    libgraphite2.so.3 => /usr/lib/i386-linux-gnu/libgraphite2.so.3 (0xf647c000)



```

When I try to install them I get this:

```
root@jupitermining:~# apt-get install libnspr4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnspr4 is already the newest version.
libnspr4 set to manually installed.



```

So the libraries are installed but Machinarium can't find them?

I did a support request to GOG but haven't got a reply...

Thanks for reading!

---

### Post by steeldriver on 2016-06-16
Is this a 32-bit system or a 64-bit system to which you've added 32-bit library packages?

---

### Post by CVGH on 2016-06-17
64bit

---

### Post by steeldriver on 2016-06-17
In that case, the apt-get command is telling you that the native (i.e. 64-bit) libnspr4 package is installed - however, your application needs the equivalent 32-bit library package, which (since multiarch is apparently already enabled on your system) you should be able to install using

```

sudo apt-get install libnspr4:i386

```

but please DO check the list of proposed packages to be removed/installed before pressing 'Y' in case there are any conflicts

Likewise for the other missing libraries.

---

### Post by Dennis N on 2016-06-17
On the 64 bit machine, for example, **libnspr4** is the 64-bit library; you need to install **libnspr4:i386** to get the needed 32-bit library for Machinarium. I used Synaptic package manager to install these, since it has an architecture selector button as a filter. See the attached screenshot:

---

### Post by CVGH on 2016-06-18
Thanks for the tips, Synaptic made is easy to fix the 32 bit libraries!

```
lister@jupitermining:~/GOG Games/Machinarium$ \./start.shRunning Machinarium
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(Machinarium:10268): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module"
./start.sh: line 16: 10268 Segmentation fault      (core dumped) "$(pwd)/$BIN_NAME"



```

Any ideas?

Thanks!!

---

### Post by Dennis N on 2016-06-18
@CVGH;

You and I have so far gone down the same path trying to get Machinarium working and basically ended up in the same place. I recently tried to get it running on Xubuntu 16.04. In addition to all the 32-bit libraries we both added, I added the theme engine package as well which is **gtk2-engines-murrine:i386**. That will eliminate that particular warning. 

But the big problem now is this, and I see you get it too - segmentation fault:

```
dmn@Sydney:~/games/Machinarium$ ./Machinarium
Segmentation fault (core dumped)

```

Not good, as this message is basically a program crash, and I don't know how to fix that. But, I DO have Machinarium running, just not on 64-bit Xubuntu 16.04. There are two workarounds I have discovered:

1) Install the 32-bit version of the operating system. I have a computer here with 32-bit Xubuntu 12.04 and Machinarium installed easily and runs normally on that system. I installed it on there several years ago. I'd expect 32-bit 14.04 or 16.04 would work as well.  

2) I recently found that Machinarium runs fine on 64-bit Manjaro Linux XFCE which I have as a dual boot installation on this same computer (alongside the Xubuntu 16.04). I did not need to add a single extra library to the system. All the needed 32-bit libraries were already included with this OS.

Neither of these options may be acceptable to you, since you would need to install a different OS. Just to add, I also tried Machinarium on 64-bit Xubuntu 15.04 maybe a year ago and exactly the same thing happened on starting the program - segmentation fault.

---

### Post by Dennis N on 2016-06-19
Just did another test: Machinarium runs fine on the current Linux Mint 17.3 Rosa (64-bit). Linux Mint includes the needed 32-bit libraries by default, and nothing needed to be added.

---

### Post by oldrocker99 on 2016-06-20
Please mark this thread as [SOLVED].

---

### Post by CVGH on 2016-06-20
Hey Dennis,

So I tried to install some of the other missing libraries and I noticed one of the things that would be removed
was "ubuntu desktop" so I stopped. So basically, this game cannot be run in Ubuntu 14.04.....

So determining that a program cannot be run in Ubuntu means the thread is "solved"?

---

### Post by Dennis N on 2016-06-20
> So determining that a program cannot be run in Ubuntu means the thread is "solved"?
This is your thread, so I believe it is your call when it is marked solved. Maybe he thought you had a solution.

The same 64-bit Xubuntu 15.04 and 16.04 OSes that would not run Machinarium will run other 32-bit game programs that I have in my collection, so it's only that one program. Don't know what it is about it. But as I said, I do have it running on 64-bit Linux Mint MATE 17.2 (updated to 17.3) so I do have a way to play that game. Manjaro worked too. It does stand up to repeat play.

I was planning to test it on Xubuntu 14.04 32-bit (I have a 32-bit laptop), but haven't got around to it yet. I expect Machinarium will work there. It does on Xubuntu 12.04. I think installing a 32-bit Ubuntu-family OS (are you willing to dual boot?) may be a solution. You could run your 32-bit software on it. And no need to install any libraries. 

How to list all 32-bit libraries you have installed:

```
dpkg-query -l *:i386
```

I was planning to post back on a test of Xubuntu 14.04 and 16.04 32-bit.

---

### Post by Dennis N on 2016-06-20
I got the game to run on Xubuntu 16.04, 64-bit OS.

This was on the gog.com website for Machinarium:

> Requires the following packages to be installed: libc6:i386 libasound2:i386 libasound2-data:i386 libasound2-plugins:i386 libgtk2.0-0:i386 libcurl3:i386 libnss3:i386 libxt6:i386 and dependencies.
Notice: this game comes with a 32-bit binary only 


I checked over my package installs, and **libcurl3:i386** was not yet installed, so I did that and the game now runs. However, the sound on Xubuntu 16.04 has a little annoying static in it*, while it doesn't on Linux Mint MATE (same computer) and my other Machinarium installs. 

Also, I do not see a package **libasound2-data:i386** in the repositories, but libasound2-data is already installed. Maybe it is for both architectures? Yes it is, since it's architecture is shown under "all" in Synaptic Package manager.

*some checking shows this problem with 16.04 is just on this one computer.

---

### Post by Dennis N on 2016-06-21
CVGH,

I used Xubuntu 14.04 64-bit in this final test, to document the process all together in one place. I began with no 32-bit packages on this system, and first enabled the 32-bit architecture on the OS. Then I installed the 32-bit packages listed below based on information gathered from gog.com and humblebundle.com:
```
All packages installed to Xubuntu 14.04 (dependencies automatically installed are not shown) to meet the requirements of Machinarium:

lib32z1
libgtk2.0-0:i386
libidn11:i386
libglu1-mesa:i386
libxmu6:i386
libpangox-1.0-0:i386
libpangoxft-1.0-0:i386
libasound2:i386
libasound2-plugins:i386
libcurl3:i386
libnss3:i386

optional (to kill some warnings if you start game from terminal):
gtk2-engines-murrine:i386
gtk2-engines-pixbuf:i386

```

After installation, the game ran normally, with no annoying static sound this time as I got in my install on Xubuntu 16.04 mentioned in previous post on the same computer (for others, that problem may not occur).

I hope this helps get yours working!

---

### Post by CVGH on 2016-06-21
Thank You Dennis!!!

Could not find the GTK engines but game works great!!

I need to look closer at the GOG site next time....

Now I will mark it solved!!

Brian

---

### Post by Dennis N on 2016-06-21
> Could not find the GTK engines but game works great!!
Oops..
My mistake. Should be **gtk2-engines-murrine:i386** and **gtk2-engines-pixbuf:i386** I fixed the post above.

One other tip: the game starts in full screen by default, and sometimes, the cursor becomes a bit uncontrolable - probably because it is a flash game. I found that playing it in window mode fixes the cursor problem. 

Enjoy your game!

---

### Post by oldrocker99 on 2016-06-21
My apologies for asking the OP to mark as [SOLVED] prematurely, and I'm glad it finally got solved.

---

