---
title: "Steam errors for Portal, Portal2, and Shadow of Mordor"
date: 2017-07-08
forum: Gaming &amp; Leisure
---

### Post by taimuda on 2017-07-08
So I'm on Ubuntu 16.04 and the three games in the title don't work with the following details;

Portal comes up with an error when I launch it saying "Could not find required OpenGL entry point 'glColorMaskIndexedEXT'! Either your video card is unsupported, or your OpenGL driver needs to be updated"

Portal 2 says that it is running but doesn't launch, syncs, then doesn't come up. 

Shadow of Mordor is the same as Portal 2.

---

### Post by efflandt on 2017-07-08
What graphics card/chip do you have and what drivers are you using (default or proprietary and version)? If you do not know look for sections about VGA (and possibly 3D if a hybrid dual graphics laptop) in the output of [blindly carefully enter your user password when sudo asks for it (nothing echoed)]:```
sudo lspci -v | less
```(q quits less)

Run **steam** from a terminal window (Ctrl+Alt+T) and see what errors show when you attempt to launch those games. If running 64-bit Ubuntu, you may need to add some 32-bit (i386) libs if using Intel graphics. Nvidia cards/chips work best with nvidia driver packages (Additional Drivers), but if you need newer drivers you can add graphics-drivers ppa per [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) and **Additional Drivers** should show newer drivers (currently up to nvidia-381). But an old card may need one of the older drivers. I am not familiar with AMD graphics.

Check out the sticky at the top of the **Steam for Linux** forum  [http://steamcommunity.com/app/221410/discussions/](http://steamcommunity.com/app/221410/discussions/) about some old libs  that steam includes, and other section(s) related to your graphics.

---

### Post by taimuda on 2017-07-09
Video card; Radeon X1300/X1550 Series 

I've tried getting the newest OpenGL drivers, and I have them. It still doesn't seem to want to work. It says the radeon, or proprietary drivers are in use.

Ubuntu is 64-bit.

Booting Steam from terminal results;

Portal
Code:
```

This system supports the OpenGL extension GL_EXT_framebuffer_object.
This system supports the OpenGL extension GL_EXT_framebuffer_blit.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
This system DOES NOT support the OpenGL extension GL_APPLE_fence.
This system DOES NOT support the OpenGL extension GL_NV_fence.
This system supports the OpenGL extension GL_ARB_sync.
This system DOES NOT support the OpenGL extension GL_EXT_draw_buffers2.

```


Portal2
```

absolutely nothing comes in the terminal

```

Shadow of Mordor

Just says there is a crash report in my crash report directory, but not the reason for the crash. I looked it up, but I don't seem to have a program to view the problem in the crash report itself. If it helps the crash report file is a &#8220;Network Packet Capture&#8221; file.

---

### Post by efflandt on 2017-07-10
Crash dump (.dmp) files from steam are in /tmp/dumps/ (not sure if specific games put them elsewhere). Not sure why dump files are identified as "Network Packet Capture" other than maybe being through a unix socket from X. If you install **ghex** which is a gui that displays both hexadecimal and ascii content of those files, open one with that, and scroll all the way to the end of the file, it says in ascii the reason for the dump. In my case the only .dmp files show at the end **Assert( Assertion Failed: BFileExists( /home/efflandt/.steam/steamapps/OpenVR/bin/linux64/vrpathreg ) failed ): vr/vrmanager.cpp:190**, but I do not have any virtual reality hardware, so that is not an issue.

X1300/X1500 graphics is quite old legacy graphics from ATI before that was bought by AMD. It will not work with proprietary AMD drivers. It should work fine with default Radeon drivers, but not sure if you need to add any missing 32-bit (i386) libs.

I do have an old PC with ATI X1300 graphics, but it is the first single core Athlon64 3200+ (2.0 GHz) missing some newer CPU flags. It still has WinXP and both 32 and 64-bit Ubuntu 10.04 on its 200 GB drive, but is slow and minecraft (OpenGL) wold not run on it, so I would not think of trying steam on it. It can run 64-bit 16.04 (installed to 16 GB SD card for my tablet PC).

I also have an Intel dual core 1.66 GHz laptop from 2007 with X1300 mobile graphics which could run minecraft in Linux (much better than similar laptop w/old Intel graphics). I used that laptop to install 64-bit 16.04.2 to an old 80 GB Intel SSD and installed steam to it, but do not want to clutter that SSD with steam games, so just need to figure out what from steam to put on external drive to test that.

Did you install steam using Ubuntu package either Software Center or using "sudo apt install steam" in a termimal (apt or apt-get are same 16.04 or newer)? Steam used to (or maybe still does) include some old lib files and those may interfere if using the .deb file downloaded from Steam website. Usually that interferes with steam itself running, but in one case someone had no trouble with Portal, but had trouble with Portal2 until he renamed one of those old libs under steam with .bak extension. Ubuntu steam package uses a launcher that automatically deletes those old steam lib files. So if you used the .deb file from Steam website, you might try```
sudo apt remove steam
sudo apt update
sudo apt install steam
```Steam itself and some games are 32-bit, so when I installed steam using "sudo apt install steam" on the 16.04.2 on the SSD of that laptop it also installed:```
The following additional packages will be installed:
  gcc-5-base:i386 gcc-6-base:i386 libbsd0:i386 libc6:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libgcc1:i386 libgcrypt20:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libgpg-error0:i386 libllvm3.8:i386 libpciaccess0:i386
  libstdc++6:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxxf86vm1:i386 zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386 rng-tools:i386
The following NEW packages will be installed:
  gcc-5-base:i386 gcc-6-base:i386 libbsd0:i386 libc6:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi6:i386 libgcc1:i386 libgcrypt20:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libgpg-error0:i386 libllvm3.8:i386 libpciaccess0:i386
  libstdc++6:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386
  libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxxf86vm1:i386 steam:i386 zlib1g:i386
0 upgraded, 43 newly installed, 0 to remove and 19 not upgraded.
Need to get 21.8 MB of archives.
After this operation, 189 MB of additional disk space will be used.
```

---

