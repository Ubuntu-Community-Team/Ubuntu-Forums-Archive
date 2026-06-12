---
title: "neXt RC Simulator for Linux"
date: 2013-12-31
forum: Gaming &amp; Leisure
---

### Post by rnsd on 2013-12-31
Greetings! Hi I'm new here but not to Ubuntu. Im looking for some help running a program in linux. Its titled neXt RC Simulator. The version I want to run is for Linux of course but it is also available for Windows and Mac as well.

I wanted to try the demo first but cant get anywhere with it. Can someone take a minute to download the small program and see if the demo will run and what it takes to get it to run?

If no one can do that maybe at least point me in the right direction.
Thanks
 
First, here is a demo video of the software so you can see how nice it actually is. 
[http://www.youtube.com/watch?v=8GhUwz016hU](http://www.youtube.com/watch?v=8GhUwz016hU)
Here is the down load link. It looks like a very nice RC simulator and its not nearly  as expensive as the most popular 2 Phoenix 4.0 and Real Flight 7.0 and I'd love to have something that works in linux.
I have Phoenix on my Win XP partition already.
[http://www.cgm-online.com/rc-heli-simulator/_download.html](http://www.cgm-online.com/rc-heli-simulator/_download.html)

---

### Post by dannyboy79 on 2014-01-01
after downloading the linux zip file and extracting it. there doesn't appear to be any installer script or anything to install into linux. Maybe you could run it in WINE but I definitely don't see anything for linux so I have no idea why they say there game works in linux

---

### Post by R33D3M33R on 2014-01-01
Works for me, just run neXt.x86 for 32-bit system and neXt.x86_64 for 64-bit system. If the game doesn't start, do:

```
ldd neXt.x86
```

(or neXt.x86_64) and it will show you which files are missing.

---

### Post by MikeCyber on 2014-01-01
Downloading. I've Realflight, don't remember what version, with the controller. Now that would be neat to have that controller working...but I heavily doubt...I also have a Spektrum DX6i, any ideas on how to 
use that?

---

### Post by efflandt on 2014-01-02
I tried it out in 64-bit 12.04 and it seems to work fine. The only issue I had was, how do you get Archive Manager to preserve directories? It extracted all files to my Downloads directory with no subdirectories, so even when I created a dir to extract it in, it would not run because it could not find its neXt_Data dir. So I used unzip and then everything was in the proper directories and worked. Since I haven't used an RC sim lately and would have to find my USB controller, I tried it with Logitech F710 gamepad, and that worked (for 2 minutes only in the demo).

This is another RC heli sim that I have used in Linux before, but it has been a couple of years: [http://www.heli-x.net/](http://www.heli-x.net/)

---

### Post by rnsd on 2014-01-03
> **MikeCyber said:**
> Downloading. I've Realflight, don't remember what version, with the controller. Now that would be neat to have that controller working...but I heavily doubt...I also have a Spektrum DX6i, any ideas on how to 
use that?

Here is a list of compatible controllers at the bottom of the page. Realflight is in the list that works.
[http://www.rc-aerobatics.eu/cgm-rc-heli-simulator_e.html](http://www.rc-aerobatics.eu/cgm-rc-heli-simulator_e.html)

---

### Post by rnsd on 2014-01-03
> **R33D3M33R said:**
> Works for me, just run neXt.x86 for 32-bit system and neXt.x86_64 for 64-bit system. If the game doesn't start, do:

```
ldd neXt.x86
```

(or neXt.x86_64) and it will show you which files are missing.

Thanks for all the replies folks. Do you have to run that command as root?

 When I run it in the terminal non root I get the command not found song and dance.

 This is the results of ldd neXt.x86_64


guest1@guest1-desktop:~/downloads/nextlinux$ ldd neXt.x86_64
    linux-vdso.so.1 =>  (0x00007fff831ff000)
    libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00007f1bc151d000)
    libGL.so.1 => /usr/lib/mesa/libGL.so.1 (0x00007f1bc129c000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f1bc0f65000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f1bc0d53000)
    libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f1bc0b49000)
    libdl.so.2 => /lib/libdl.so.2 (0x00007f1bc0944000)
    libpthread.so.0 => /lib/libpthread.so.0 (0x00007f1bc0727000)
    librt.so.1 => /lib/librt.so.1 (0x00007f1bc051f000)
    libm.so.6 => /lib/libm.so.6 (0x00007f1bc029b000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f1bc0084000)
    libc.so.6 => /lib/libc.so.6 (0x00007f1bbfcfd000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f1bc17ab000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f1bbf9e8000)
    libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0x00007f1bbf7e2000)
    libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f1bbf5df000)
    libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f1bbf3d8000)
    libdrm.so.2 => /lib/libdrm.so.2 (0x00007f1bbf1cd000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f1bbefb1000)
    libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f1bbeda6000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f1bbeba2000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f1bbe99b000)
:~/downloads/nextlinux$

---

### Post by rnsd on 2014-01-03
> **efflandt said:**
> I tried it out in 64-bit 12.04 and it seems to work fine. The only issue I had was, how do you get Archive Manager to preserve directories? It extracted all files to my Downloads directory with no subdirectories, so even when I created a dir to extract it in, it would not run because it could not find its neXt_Data dir. So I used unzip and then everything was in the proper directories and worked. Since I haven't used an RC sim lately and would have to find my USB controller, I tried it with Logitech F710 gamepad, and that worked (for 2 minutes only in the demo).

This is another RC heli sim that I have used in Linux before, but it has been a couple of years: [http://www.heli-x.net/](http://www.heli-x.net/)

You can restart it and use it another 2 minutes. You just have to keep repeating that unless you want to pay and register.

So yours just worked with no problems?

---

### Post by efflandt on 2014-01-03
> **rnsd said:**
> So yours just worked with no problems?

Yes, but of course if the binary is not in your $PATH you cd to the "Linux x86+64bit" dir and then: **./neXt.x86_64** runs it (in 64-bit 12.04 on PC in my sig).

What graphics are you using? I know when I was doing some graphics benchmarks on a new laptop with 64-bit 13.10 and combo Intel HD 4600/Nvidia GTX 765M graphics, not all of the benchmarks would run with the Intel video, but they did with nvidia.

---

### Post by MikeCyber on 2014-01-04
> **rnsd said:**
> Here is a list of compatible controllers. Realflight is in the list that works.
Where, what list?

Did you do? 
chmod +x ne*64

---

### Post by monkeybrain20122 on 2014-01-04
Just unzip the file and click neXt.x86_64 (64 bit) or neXt.x86(32 bit) to start. No installation required.

---

### Post by monkeybrain20122 on 2014-01-04
> **efflandt said:**
> The only issue I had was, how do you get Archive Manager to preserve directories? It extracted all files to my Downloads directory with no subdirectories

Do you use Lubuntu? This appears to be a feature/bug of pcmanfm (unzipped zipped file contents get scattered all over the places). I have no such issue with Nautilus even using the same file roller. Not sure if a bug has been filed.
[http://ubuntuforums.org/showthread.php?t=2196967](http://ubuntuforums.org/showthread.php?t=2196967)

---

### Post by monkeybrain20122 on 2014-01-04
> **rnsd said:**
> Thanks for all the replies folks. Do you have to run that command as root?

 When I run it in the terminal non root I get the command not found song and dance.

 This is the results of ldd neXt.x86_64


guest1@guest1-desktop:~/downloads/nextlinux$ ldd neXt.x86_64
    linux-vdso.so.1 =>  (0x00007fff831ff000)
    libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00007f1bc151d000)
    libGL.so.1 => /usr/lib/mesa/libGL.so.1 (0x00007f1bc129c000)
    libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f1bc0f65000)
    libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f1bc0d53000)
    libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f1bc0b49000)
    libdl.so.2 => /lib/libdl.so.2 (0x00007f1bc0944000)
    libpthread.so.0 => /lib/libpthread.so.0 (0x00007f1bc0727000)
    librt.so.1 => /lib/librt.so.1 (0x00007f1bc051f000)
    libm.so.6 => /lib/libm.so.6 (0x00007f1bc029b000)
    libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f1bc0084000)
    libc.so.6 => /lib/libc.so.6 (0x00007f1bbfcfd000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f1bc17ab000)
    libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f1bbf9e8000)
    libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0x00007f1bbf7e2000)
    libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f1bbf5df000)
    libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f1bbf3d8000)
    libdrm.so.2 => /lib/libdrm.so.2 (0x00007f1bbf1cd000)
    libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f1bbefb1000)
    libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f1bbeda6000)
    libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f1bbeba2000)
    libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f1bbe99b000)
:~/downloads/nextlinux$
No don't need root and don't need to use the terminal at all. Just right click it (make sure it is allowed to be executed as program, again right click > Properties > Permission) Why are you guys making things so complicated? :)

---

### Post by rnsd on 2014-01-04
I put the link in the other post like it should have been. 

No I haven't done any chmod commands.

---

### Post by rnsd on 2014-01-04
> **monkeybrain20122 said:**
> No don't need root and don't need to use the terminal at all. Just right click it (make sure it is allowed to be executed as program, again right click > Properties > Permission) Why are you guys making things so complicated? :)

 It simply is not working for me it does nothing when I click it or run it in the terminal.

---

### Post by rnsd on 2014-01-04
> **efflandt said:**
> Yes, but of course if the binary is not in your $PATH you cd to the "Linux x86+64bit" dir and then: **./neXt.x86_64** runs it (in 64-bit 12.04 on PC in my sig).

What graphics are you using? I know when I was doing some graphics benchmarks on a new laptop with 64-bit 13.10 and combo Intel HD 4600/Nvidia GTX 765M graphics, not all of the benchmarks would run with the Intel video, but they did with nvidia.


My graphics card is the Intel Corporation 82915G/GV/910GL Integrated Graphics Controller

---

### Post by MikeCyber on 2014-01-04
I don't think that's powerful enough. I have a Asus GTX 770...
Do
./n*64
in a terminal and paste the output.

---

### Post by rnsd on 2014-01-04
> **MikeCyber said:**
> I don't think that's powerful enough. I have a Asus GTX 770...
Do
./n*64
in a terminal and paste the output.

Here is the results of that

/downloads/neXt64$ ./n*64
Set current directory to /home/guest1/downloads/neXt64
Found path: /home/guest1/downloads/neXt64/neXt.x86_64
Mono path[0] = '/home/guest1/downloads/neXt64/neXt_Data/Managed'
Mono path[1] = '/home/guest1/downloads/neXt64/neXt_Data/Mono'
Mono config path = '/home/guest1/downloads/neXt64/neXt_Data/Mono/etc'
Aborted
guest1@guest1-desktop:~/downloads/neXt64$

---

### Post by mips on 2014-01-04
> **MikeCyber said:**
> I don't think that's powerful enough. I have a Asus GTX 770...


Nope it's fine, I just tested it on my old laptop with the same GPU and it runs ok, get the odd message about a skipped frame now and again but it runs ok.

I can launch the app by clicking on it in thunar or doing ./neXt.x86 from a terminal.

@[[COLOR=#000000]rnsd[/COLOR]]("http://ubuntuforums.org/member.php?u=1895026")

Do you have mesa installed and opengl working correctly?

---

### Post by rnsd on 2014-01-04
> **mips said:**
> Nope it's fine, I just tested it on my old laptop with the same GPU and it runs ok, get the odd message about a skipped frame now and again but it runs ok.

I can launch the app by clicking on it in thunar or doing ./neXt.x86 from a terminal.

@[[COLOR=#000000]rnsd[/COLOR]]("http://ubuntuforums.org/member.php?u=1895026")

Do you have mesa installed and opengl working correctly?

I'm not sure about mesa and opengl. How do I check?

my Intel G910 vid card works OK with Phoenix on windows although it wont' do the new 2D landscapes in Phoenix it does run Phoenix with things set to low though. And runs Heli-X in Ubuntu 10.04.

---

### Post by monkeybrain20122 on 2014-01-04
> **rnsd said:**
> I'm not sure about mesa and opengl. How do I check?

.

in the terminal 

```
sudo apt-get install mesa-utils
glxinfo | grep OpenGL

```

---

### Post by rnsd on 2014-01-04
> **monkeybrain20122 said:**
> in the terminal 

```
sudo apt-get install mesa-utils
glxinfo | grep OpenGL

```


 Its says mesa was already installed and the glxinfo command yielded no results.

---

### Post by rnsd on 2014-01-04
With the readelf -d command I found the needed library's but how do I get them. Maybe I already have them but the program can't find them?

guest1@guest1-desktop:~/downloads/neXtlinux/Linux64$ readelf -d neXt.x86_64

Dynamic section at offset 0x1180740 contains 32 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libGLU.so.1]
 0x0000000000000001 (NEEDED)             Shared library: [libGL.so.1]
 0x0000000000000001 (NEEDED)             Shared library: [libX11.so.6]
 0x0000000000000001 (NEEDED)             Shared library: [libXext.so.6]
 0x0000000000000001 (NEEDED)             Shared library: [libXcursor.so.1]
 0x0000000000000001 (NEEDED)             Shared library: [libdl.so.2]
 0x0000000000000001 (NEEDED)             Shared library: [libpthread.so.0]
 0x0000000000000001 (NEEDED)             Shared library: [librt.so.1]
 0x0000000000000001 (NEEDED)             Shared library: [libm.so.6]
 0x0000000000000001 (NEEDED)             Shared library: [libgcc_s.so.1]
 0x0000000000000001 (NEEDED)             Shared library: [libc.so.6]
 0x0000000000000001 (NEEDED)             Shared library: [ld-linux-x86-64.so.2]
 0x000000000000000c (INIT)               0x449b50
 0x000000000000000d (FINI)               0x128e948
 0x0000000000000004 (HASH)               0x4002d0
 0x000000006ffffef5 (GNU_HASH)           0x405a60
 0x0000000000000005 (STRTAB)             0x420748
 0x0000000000000006 (SYMTAB)             0x40ba90
 0x000000000000000a (STRSZ)              137785 (bytes)
 0x000000000000000b (SYMENT)             24 (bytes)
 0x0000000000000015 (DEBUG)              0x0
 0x0000000000000003 (PLTGOT)             0x1781fe8
 0x0000000000000002 (PLTRELSZ)           11544 (bytes)
 0x0000000000000014 (PLTREL)             RELA
 0x0000000000000017 (JMPREL)             0x446e38
 0x0000000000000007 (RELA)               0x443eb0
 0x0000000000000008 (RELASZ)             12168 (bytes)
 0x0000000000000009 (RELAENT)            24 (bytes)
 0x000000006ffffffe (VERNEED)            0x443d40
 0x000000006fffffff (VERNEEDNUM)         7
 0x000000006ffffff0 (VERSYM)             0x442182
 0x0000000000000000 (NULL)               0x0

---

### Post by monkeybrain20122 on 2014-01-04
I think most of these should already be installed. But anyway, you can install them using synaptic. For examples, search libglu and it returns something like libglu-mesa, search libx11 returns libx11-6, libxext returns libxext6 etc Just mark those for installation and then install them.

If you don't have synaptic, install it with
sudo apt-get install synaptic

Edited: wait a minute, something is not right. From the output of ldd of your previous post those libs are already installed.

---

### Post by rnsd on 2014-01-05
I found a few of them in synaptic but was going to have to unload all the compiz-fusion plugins, adacity, gnoeme desktop and a few other things so I didnt get it.

---

### Post by monkeybrain20122 on 2014-01-05
> **rnsd said:**
> I found a few of them in synaptic but was going to have to unload all the compiz-fusion plugins, adacity, gnoeme desktop and a few other things so I didnt get it.

That is crazy. What release of Ubuntu? How did you install it?

---

### Post by rnsd on 2014-01-07
> **monkeybrain20122 said:**
> That is crazy. What release of Ubuntu? How did you install it?

Im running Ubuntu 10.04 with all updates. Installed it from CD 2 or 3 years ago. My first Ubuntu was 8.10 been loving it ever since with the exception of programs not running occasionally. I guess If I were a Linux Guru I could fix it .

---

### Post by monkeybrain20122 on 2014-01-07
> **rnsd said:**
> Im running Ubuntu 10.04 with all updates. Installed it from CD 2 or 3 years ago. My first Ubuntu was 8.10 been loving it ever since with the exception of programs not running occasionally. I guess If I were a Linux Guru I could fix it .

Well that is most likely the source of your problems 10.04 has been dead since last April and even if it hasn't expired all of its libraries are very old. Please backup your data a do a fresh install of a currently supported Ubuntu release. 12.04 is the LTS, 13.10 is the latest, you can forget about 13.04(end of life in 2 weeks) and 12.10(end of life April)

---

### Post by MikeCyber on 2014-01-09
I use Nvidia but I guess for Intel it's best to use the very latest...check Phoronix.

---

### Post by mips on 2014-01-09
> **rnsd said:**
> Im running Ubuntu 10.04 with all updates.

Wish you had mentioned that earlier.

---

### Post by rnsd on 2014-01-13
I upgraded the lap top to 11.04 and despised the new desktop that came stock with it, never did find the terminal. I put 10.04 back on it and never have even bothered getting it for my Deskop PC.

I'll upgrade it If I can keep my desktop just like it is now otherwise I'll just use windows to play neXt.

Thanks

---

### Post by MikeCyber on 2014-01-14
Just type Term in where you search your apps. It's installed by default. I'd go with 13.10, backup your home directory and paste it back afterwards. Very, very basic so good luck for you.

---

### Post by rnsd on 2014-01-17
> **MikeCyber said:**
> Just type Term in where you search your apps. It's installed by default. I'd go with 13.10, backup your home directory and paste it back afterwards. Very, very basic so good luck for you.

If I can keep Gnome desktop I'll upgrade. Thanks

---

### Post by MikeCyber on 2014-01-18
Yes. Personally I only do:
ls -la
cp -rfp .thunderbird /Media/whereever/disk/
to keep my emails but you can copy the whole home folder if you like.

---

