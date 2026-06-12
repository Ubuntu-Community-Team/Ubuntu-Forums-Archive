---
title: "Howto install X-plane 8.4 DVD set and 8.5 beta net installer"
date: 2006-09-10
forum: Gaming &amp; Leisure
---

### Post by fubadubrub on 2006-09-10
**I was having a bit of trouble installing X-plane and I solved it for me. Here's how.**
> Download the DVD installer and extract it: [http://dev.x-plane.com/installer/1.13/](http://dev.x-plane.com/installer/1.13/)
```
chmod +x Installer-i586
```




> Then based on the set of info here [http://www.happypenguin.org/show?X-Plane](http://www.happypenguin.org/show?X-Plane)
do this:
```
sudo umount /dev/dvd
```
```
sudo mkdir -p /mnt/dvd
```
```
sudo mount -t udf /dev/dvd /mnt/dvd
```
> **Note that the DVD must be mounted as UDF for the installer to run.**




> **Note that you start out with the DVD that says X-Plane V8 on it**.
```
./Installer-i586
```
**Just install all 7 DVD this way but do start with the first one though.**




> **See this posting for instructions on how to install the Loki libs and yes you will need them so do check out this posting.  Simply download Loki libs and extract:**
[http://ubuntuforums.org/showthread.php?t=180759](http://ubuntuforums.org/showthread.php?t=180759)




> To run the game:
```
cd your/path/here/X-Plane\ 8.40
```
```
LD_PRELOAD=/your/path/here/Loki_Compat/libopenal-0.0.so ./X-Plane-i586
```




> **To update X-Plane simple download the net installer and extract it and chmod it and run as you have already been shown how**.

Have Fun!

---

### Post by corstar on 2006-10-20
Edit. It totaly screwed the whole thing. I have no scenery at all now. Xplane SUCKS

---

### Post by hikaricore on 2006-10-20
> **corstar said:**
> Edit. It totaly screwed the whole thing. I have no scenery at all now. Xplane SUCKS

That's right express your feelings by lashing out at a piece of software and someone for trying to help everyone with info to install it...

---

### Post by wehttam67 on 2006-10-24
I get the following error after *sudo mount -t udf /dev/dvd /mnt/dvd*

mount: block device /dev/dvd is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/dvd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

any tips?

Cheers

---

### Post by corstar on 2006-11-12
After a bit of messing around, I found the procedure to work.

This is the order for the commands.

sudo umount /dev/dvd

sudo mkdir -p /mnt/dvd

sudo mount -t udf /dev/dvd /mnt/dvd

LD_PRELOAD=/usr/lib/libalut.so.0 ./X-Plane-i586  ( I need to use this, the game doesn't run otherwise, it might be cool for others)

---

### Post by Saubazi on 2006-11-22
I did the install deed but after I try to launch nogo ](*,) 

$ LD_PRELOAD=/usr/lib32/libalut.so.0 ./X-Plane-i586
X-System Error:
I can not find a 3-D accelerator card that can handle OpenGL that has correctly installed drivers.

I will still let you run the simulator, but the frame rate will NOT allow for a good simulation.

For you to fly realistically, you must use X-Plane version Classic, or get a 3-D accelerator card that can handle OpenGL.

See [www.X-Plane.com](www.X-Plane.com) for a list of the currently-compatible 3-D video cards.

Sorry.
*** glibc detected *** ./X-Plane-i586: free(): invalid pointer: 0x0dd05cb8 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf7ba447d]
/lib32/libc.so.6(__libc_free+0x84)[0xf7ba4604]
./X-Plane-i586(_ZdlPv+0x1c)[0x85421d0]
/home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so(_ZN9__gnu_cxx13new_allocatorISsE10deallocateEPSsj+0x1d)[0xe9884c3b]
/home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so(_ZNSt12_Vector_baseISsSaISsEE13_M_deallocateEPSsj+0x31)[0xe98849ab]
/home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so(_ZNSt12_Vector_baseISsSaISsEED2Ev+0x3b)[0xe9887129]
/home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so(_ZNSt6vectorISsSaISsEED1Ev+0x56)[0xe9886e5e]
/home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so(_Z22XPLMFindAndLoadPluginsPKc+0x4f4)[0xe9885ac8]
/home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so(XPLMInitializePlugins+0xd1)[0xe9885169]
./X-Plane-i586[0x81d2ee4]
./X-Plane-i586[0x8118dbb]
./X-Plane-i586[0x8057223]
./X-Plane-i586[0x8057f14]
/lib32/libc.so.6(__libc_start_main+0xdc)[0xf7b528cc]
./X-Plane-i586[0x804df01]
======= Memory map: ========
08048000-0860a000 r-xp 00000000 08:04 10643942                           /home/jykke/X-Plane 8.40/X-Plane-i586
0860a000-0861a000 rw-p 005c1000 08:04 10643942                           /home/jykke/X-Plane 8.40/X-Plane-i586
0861a000-0de17000 rw-p 0861a000 00:00 0                                  [heap]
e9600000-e9621000 rw-p e9600000 00:00 0 
e9621000-e9700000 ---p e9621000 00:00 0 
e97bf000-e97cb000 r-xp 00000000 08:04 10643751                           /home/jykke/X-Plane 8.40/Resources/plugins/PluginAdminLin.xpl
e97cb000-e97cd000 rw-p 0000b000 08:04 10643751                           /home/jykke/X-Plane 8.40/Resources/plugins/PluginAdminLin.xpl
e97cd000-e9843000 r-xp 00000000 08:04 10643753                           /home/jykke/X-Plane 8.40/Resources/plugins/XPWidgets.so
e9843000-e984c000 rw-p 00076000 08:04 10643753                           /home/jykke/X-Plane 8.40/Resources/plugins/XPWidgets.so
e984c000-e9853000 rw-p e984c000 00:00 0 
e9853000-e98a0000 r-xp 00000000 08:04 10643752                           /home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so
e98a0000-e98ab000 rw-p 0004c000 08:04 10643752                           /home/jykke/X-Plane 8.40/Resources/plugins/XPLM.so
e98ab000-e9db1000 rw-p e98ab000 00:00 0 
e9db1000-e9db2000 ---p e9db1000 00:00 0 
e9db2000-ea5b2000 rwxp e9db2000 00:00 0 
ea5b2000-ea6b2000 rw-s 0010f000 00:0d 11111                              /dev/dri/card0
ea6b2000-ea6c0000 rw-p ebcce000 00:00 0 
ea6c0000-eaac0000 rw-s 0010e000 00:0d 11111                              /dev/dri/card0
eaac0000-eabc0000 rw-s 00000000 00:12 65450                              /dev/shm/ATISHM00
eabc0000-eb0f2000 rw-p eabc0000 00:00 0 
eb0fb000-eb120000 rw-p eb0fb000 00:00 0 
eb120000-eb620000 rw-s 0000a000 00:0d 11111                              /dev/dri/card0
eb620000-ebb20000 rw-s 00009000 00:0d 11111                              /dev/dri/card0
ebb20000-ebc85000 rw-p ebb20000 00:00 0 
ebc8b000-ebccb000 rw-p ebc8b000 00:00 0 
ebccb000-ebcce000 rw-s 0010d000 00:0d 11111                              /dev/dri/card0
ebcd3000-ebd14000 rw-p ebcd3000 00:00 0 
ebd14000-ebe54000 rw-s 0010a000 00:0d 11111                              /dev/dri/card0
ebe54000-ebe55000 rw-p ebe54000 00:00 0 
ebe55000-ec495000 rw-s 00007000 00:0d 11111                              /dev/dri/card0
ec495000-ec595000 rw-s 00006000 00:0d 11111                              /dev/dri/card0
ec595000-f4595000 rw-s 00003000 00:0d 11111                              /dev/dri/card0
f4595000-f4645000 r-xp 00000000 08:03 15223001                           /usr/lib32/libstdc++.so.5.0.7
f4645000-f464a000 rw-p 000af000 08:03 15223001                           /usr/lib32/libstdc++.so.5.0.7
f464a000-f464f000 rw-p f464a000 00:00 0 
f464f000-f4e37000 r-xp 00000000 08:03 524464                             /usr/lib32/dri/fglrx_dri.so
f4e37000-f4e80000 rw-p 007e8000 08:03 524464                             /usr/lib32/dri/fglrx_dri.so
f4e80000-f4f0a000 rw-p f4e80000 00:00 0 
f4f0a000-f4f0b000 ---p f4f0a000 00:00 0 
f4f0b000-f570b000 rwxp f4f0b000 00:00 0 
f570b000-f77ab000 rw-p f570b000 00:00 0 
f77ab000-f77af000 r-xp 00000000 08:03 15225550                           /usr/lib32/libogg.so.0
f77af000-f77b0000 rw-p 00003000 08:03 15225550                           /usr/lib32/libogg.so.0
f77b0000-f77b7000 r-xp 00000000 08:03 2932819                            /lib32/librt-2.4.so
f77b7000-f77b9000 rw-p 00006000 08:03 2932819                            /lib32/librt-2.4.so
f77b9000-f77ba000 rw-p f77b9000 00:00 0 
f77ba000-f77f4000 r-xp 00000000 08:03 15221890                           /usr/lib32/libsmpeg-0.4.so.0
f77f4000-f77f6000 rw-p 00039000 08:03 15221890                           /usr/lib32/libsmpeg-0.4.so.0
f77f6000-f7812000 rw-p f77f6000 00:00 0 
f7812000-f7819000 r-xp 00000000 08:03 15221887                           /usr/lib32/libvorbisfile.so.3
f7819000-f781a000 rw-p 00006000 08:03 15221887                           /usr/lib32/libvorbisfile.so.3
f781a000-f7833000 r-xp 00000000 08:03 15225549                           /usr/lib32/libvorbis.so.0
f7833000-f7842000 rw-p 00019000 08:03 15225549                           /usr/lib32/libvorbis.so.0
f7842000-f78a0000 r-xp 00000000 08:03 15221349                           /usr/lib32/libSDL-1.2.so.0.7.2
f78a0000-f78a2000 rw-p 0005d000 08:03 15221349                           /usr/lib32/libSDL-1.2.so.0.7.2
f78a2000-f78ca000 rw-p f78a2000 00:00 0 
f78ca000-f78e8000 r-xp 00000000 08:03 15223130                           /usr/lib32/libaudiofile.so.0
f78e8000-f78ea000 rw-p 0001e000 08:03 15223130                           /usr/lib32/libaudiofile.so.0
f78ea000-f78eb000 rw-p f78ea000 00:00 0 
f78eb000-f78f4000 r-xp 00000000 08:03 15223123                           /usr/lib32/libesd.so.0
f78f4000-f78f5000 rw-p 00008000 08:03 15223123                           /usr/lib32/libesd.so.0
f78f5000-f7986000 r-xp 00000000 08:03 15222262                           /usr/lib32/libglib-2.0.so.0.1200.4
f7986000-f7987000 rw-p 00091000 08:03 15222262                           /usr/lib32/libglib-2.0.so.0.1200.4
f7987000-f798b000 r-xp 00000000 08:03 15222496                           /usr/lib32/libgthread-2.0.so.0.1200.4
f798b000-f798c000 rw-p 00003000 08:03 15222496                           /usr/lib32/libgthread-2.0.so.0.1200.4
f798c000-f798f000 r-xp 00000000 08:03 15222369                           /usr/lib32/libgmodule-2.0.so.0.1200.4
f798f000-f7990000 rw-p 00002000 08:03 15222369                           /usr/lib32/libgmodule-2.0.so.0.1200.4
f7990000-f7995000 r-xp 00000000 08:03 15222804                           /usr/lib32/libartsc.so.0
f7995000-f7996000 rw-p 00004000 08:03 15222804                           /usr/lib32/libartsc.so.0
f7996000-f7a50000 r-xp 00000000 08:03 15222265                           /usr/lib32/libasound.so.2.0.0
f7a50000-f7a55000 rw-p 000b9000 08:03 15222265                           /usr/lib32/libasound.so.2.0.0
f7a55000-f7a59000 r-xp 00000000 08:03 15223096                           /usr/lib32/libXdmcp.so.6.0.0
f7a59000-f7a5a000 rw-p 00003000 08:03 15223096                           /usr/lib32/libXdmcp.so.6.0.0
f7a5a000-f7a5b000 rw-p f7a5a000 00:00 0 
f7a5b000-f7a5d000 r-xp 00000000 08:03 15223094                           /usr/lib32/libXau.so.6.0.0
f7a5d000-f7a5e000 rw-p 00001000 08:03 15223094                           /usr/lib32/libXau.so.6.0.0
f7a5e000-f7b32000 r-xp 00000000 08:03 15221470                           /usr/lib32/libstdc++.so.6.0.8
f7b32000-f7b35000 r--p 000d4000 08:03 15221470                           /usr/lib32/libstdc++.so.6.0.8
f7b35000-f7b37000 rw-p 000d7000 08:03 15221470                           /usr/lib32/libstdc++.so.6.0.8
f7b37000-f7b3d000 rw-p f7b37000 00:00 0 
f7b3d000-f7c6a000 r-xp 00000000 08:03 2932800                            /lib32/libc-2.4.so
f7c6a000-f7c6c000 r--p 0012c000 08:03 2932800                            /lib32/libc-2.4.so
f7c6c000-f7c6e000 rw-p 0012e000 08:03 2932800                            /lib32/libc-2.4.so
f7c6e000-f7c71000 rw-p f7c6e000 00:00 0 
f7c71000-f7c7b000 r-xp 00000000 08:03 15220951                           /usr/lib32/libgcc_s.so.1
f7c7b000-f7c7c000 rw-p 00009000 08:03 15220951                           /usr/lib32/libgcc_s.so.1
f7c7c000-f7ca0000 r-xp 00000000 08:03 2932804                            /lib32/libm-2.4.so
f7ca0000-f7ca2000 rw-p 00023000 08:03 2932804                            /lib32/libm-2.4.so
f7ca2000-f7ca3000 rw-p f7ca2000 00:00 0 
f7ca3000-f7ca5000 r-xp 00000000 08:03 2932803                            /lib32/libdl-2.4.so
f7ca5000-f7ca7000 rw-p 00001000 08:03 2932803                            /lib32/libdl-2.4.so
f7ca7000-f7cb6000 r-xp 00000000 08:03 2932817                            /lib32/libpthread-2.4.so
f7cb6000-f7cb8000 rw-p 0000f000 08:03 2932817                            /lib32/libpthread-2.4.so
f7cb8000-f7cba000 rw-p f7cb8000 00:00 0 
f7cba000-f7d04000 r-xp 00000000 08:03 15221145                           /usr/lib32/libopenal.so.0
f7d04000-f7d05000 rw-p 0004a000 08:03 15221145                           /usr/lib32/libopenal.so.0
f7d05000-f7d5a000 rw-p f7d05000 00:00 0 
f7d5a000-f7e20000 r-xp 00000000 08:03 15223093                           /usr/lib32/libX11.so.6.2.0
f7e20000-f7e23000 rw-p 000c5000 08:03 15223093                           /usr/lib32/libX11.so.6.2.0
f7e23000-f7e2f000 r-xp 00000000 08:03 15223097                           /usr/lib32/libXext.so.6.4.0
f7e2f000-f7e30000 rw-p 0000c000 08:03 15223097                           /usr/lib32/libXext.so.6.4.0
f7e30000-f7ea9000 r-xp 00000000 08:03 15222497                           /usr/lib32/libGLU.so.1.3.060501
f7ea9000-f7eaa000 rw-p 00079000 08:03 15222497                           /usr/lib32/libGLU.so.1.3.060501
f7eaa000-f7eab000 rw-p f7eaa000 00:00 0 
f7eab000-f7f43000 r-xp 00000000 08:03 15225398                           /usr/lib32/libGL.so.1.2
f7f43000-f7f48000 rw-p 00098000 08:03 15225398                           /usr/lib32/libGL.so.1.2
f7f48000-f7f4b000 rw-p f7f48000 00:00 0 
f7f4d000-f7f50000 rw-p f7f4d000 00:00 0 
f7f50000-f7f51000 rw-s 00005000 00:0d 11111                              /dev/dri/card0
f7f51000-f7f61000 rw-s 00004000 00:0d 11111                              /dev/dri/card0
f7f61000-f7f63000 rw-s 00002000 00:0d 11111                              /dev/dri/card0
f7f63000-f7f67000 r-xp 00000000 08:03 15225571                           /usr/lib32/libalut.so.0
f7f67000-f7f6a000 rw-p 00003000 08:03 15225571                           /usr/lib32/libalut.so.0
f7f6a000-f7f6c000 rw-p f7f6a000 00:00 0 
f7f6c000-f7f87000 r-xp 00000000 08:03 2932779                            /lib32/ld-2.4.so
f7f87000-f7f89000 rw-p 0001b000 08:03 2932779                            /lib32/ld-2.4.so
ffeb2000-ffedb000 rwxp ffeb2000 00:00 0                                  [stack]
ffedb000-ffedc000 rw-p ffedb000 00:00 0 
ffffe000-fffff000 r-xp ffffe000 00:00 0 
Aborted (core dumped)


I am getting a bit confused by this missing OpenGL bit. I am running the stuff under 64bit Edgy...

---

### Post by Saubazi on 2006-11-24
I made some progress...
If I start with MALLOC_CHECK=1 ./X-Plane-i586 the loader does not crash immediately. However, it is still complaining about missing 3D card and additionally to this I get plenty of:
fglX11AllocateManagedSurface: __FGLTexMgrAllocMem failed!!

After about 20% of loading the loader just hangs up there.

None of this LD_PRELOAD stuff helped me a bit.

Is there an issue with ATI here?
Mine is running quite ok on other occasions but here I have this drama.

Anyway graphics should be ok:
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by Saubazi on 2006-11-26
BUMP - I am really having hard time finding help for this one...

---

### Post by juanvm on 2007-02-28
:lolflag: 
No go here..................
-------------------------------------------------------------------------------------------------------------
root@juan-desktop:/home/juan# chmod +x X-Plane-DVD-Install
root@juan-desktop:/home/juan# sudo umount /dev/dvd
root@juan-desktop:/home/juan# sudo mkdir -p /mnt/dvd
root@juan-desktop:/home/juan# sudo mount -t udf /dev/dvd /mnt/dvd
root@juan-desktop:/home/juan# ./X-Plane-DVD-Install
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Segmentation fault
root@juan-desktop:/home/juan#
------------------------------------------------------------------------------------------------------------

Any idea?????????????

---

### Post by juanvm on 2007-03-01
> **juanvm said:**
> :lolflag: 
No go here..................
-------------------------------------------------------------------------------------------------------------
root@juan-desktop:/home/juan# chmod +x X-Plane-DVD-Install
root@juan-desktop:/home/juan# sudo umount /dev/dvd
root@juan-desktop:/home/juan# sudo mkdir -p /mnt/dvd
root@juan-desktop:/home/juan# sudo mount -t udf /dev/dvd /mnt/dvd
root@juan-desktop:/home/juan# ./X-Plane-DVD-Install
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Segmentation fault
root@juan-desktop:/home/juan#
------------------------------------------------------------------------------------------------------------

Any idea?????????????

Solved.....

Downloaded X-Plane-Net-Install
Placed x-Plane 8.4 dvd in driver

root@juan-desktop:/home/juan# chmod +x X-Plane-Net-Install
root@juan-desktop:/home/juan# sudo umount /dev/dvd
root@juan-desktop:/home/juan# sudo mkdir -p /mnt/dvd
root@juan-desktop:/home/juan# sudo mount -t udf /dev/dvd /mnt/dvd
root@juan-desktop:/home/juan# 

Opened Home folder
Left click X-Plane-Net-Install icon
X-plane was installed
Now when I start x-plane it will just flash the opening screen for half a second and it will close.....................

Again.... Any idea.....................:lolflag:

---

### Post by juanvm on 2007-03-27
> **juanvm said:**
> Solved.....

Downloaded X-Plane-Net-Install
Placed x-Plane 8.4 dvd in driver

root@juan-desktop:/home/juan# chmod +x X-Plane-Net-Install
root@juan-desktop:/home/juan# sudo umount /dev/dvd
root@juan-desktop:/home/juan# sudo mkdir -p /mnt/dvd
root@juan-desktop:/home/juan# sudo mount -t udf /dev/dvd /mnt/dvd
root@juan-desktop:/home/juan# 

Opened Home folder
Left click X-Plane-Net-Install icon
X-plane was installed
Now when I start x-plane it will just flash the opening screen for half a second and it will close.....................

Again.... Any idea.....................:lolflag:

------------------------------------------------------------------------------------------------------------------------------
Finally................. is running...........

Updated to X-Plane 8.60

at the console: (from Joshua Wise)

$export MALLOC_CHECK_=1              (note the underscore line after CHECK__)
$./X-Plane-i586

It was installed in latest ver of Kubuntu with all the latest patches, CH Yoke and Pro pedals works, the hat switch on the yoke do not work. I also installed in Opensuse but the CH pro pedals do not work.....................
:guitar: :lolflag:

---

### Post by mattp52 on 2007-06-04
Anyone managed to get X-Plane installed fresh on Feisty? I just get "Unable to Install"  "No such file or directory" when executing it off the command line (execution bit is set and X-plane (v8.20) DVD is mounted as per instructions earlier in this thread....

---

### Post by Fubie on 2007-07-06
Ok, I'm trying to mount my DVD drive as a udf but it keeps telling me that the unmount command is not found.

Any help would be appreciated!

---

### Post by rhornsby on 2007-07-14
> **Fubie said:**
> Ok, I'm trying to mount my DVD drive as a udf but it keeps telling me that the unmount command is not found.


Drop the first "N" from your command.  You want "umount" not "u**n**mount"  :)

I found this thread because I downloaded the X-Plane demo installer, but I must be a real doofus because I can't make it run:

rhornsby@redshoes:~/bin$ gunzip X-Plane-Net-Install.gz 
rhornsby@redshoes:~/bin$ chmod 755 X-Plane-Net-Install 
rhornsby@redshoes:~/bin$ ./X-Plane-Net-Install 
bash: ./X-Plane-Net-Install: No such file or directory
rhornsby@redshoes:~/bin$ ls -l
total 11816
-rwxr-xr-x 1 rhornsby rhornsby 12079408 2007-01-06 13:24 X-Plane-Net-Install

EDIT:

Trying to run this on Feisty, kernel 2.6.20-16 (x64).

Turns out that the installer appears to have been compiled against a different set of libraries than what I have available.  I got past the problem (above) with not being able to run the file (would be really nice if the system would say "can't find linked library...") by installing the package libc6-i386.

Unfortunately now it is actually complaining about libraries I apparently don't have.

root@redshoes:/home/rhornsby/bin# ./X-Plane-Net-Install 
./X-Plane-Net-Install: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

Have to work on this, or maybe try installing a 32-bit system?

---

### Post by Abandon on 2008-02-02
I received the 8 DVD set of X-Plane 8.60 this week. I had some trouble because of poor documentation. But i figured it out. It is not so difficult.

First: don' t use the installer from their homepage. Instead use the one just below were it' s written as:
[B]
SERVERS FOR OLDER VERSIONS OF X-PLANE THAN VERSION 8[/B]:

I used the [http://www.boostair.com/download/x-plane-v8-lin/](http://www.boostair.com/download/x-plane-v8-lin/) link and downloaded the dvd installer. Place it in you' re homedir, make sure its executable and give it a spin with the game dvd in you're drive. Don' t start with a scenerydisc, use the gameplay disc.

When you are presented with a directory tree, choose "cancel"  and default installation will take place in you' re homedir. After that you do the same with one (or all) of the scenery discs. Also..use the "cancel" button for choosing default in you' re home dir.

Ok..when that' s done you can start the simulation after a double click on the X-Plane-586 in the X-Plane directory. 

You can also install the netinstaller after all this to upgrade from 8.6 to 8.64 It' s about an 700 Mb download but it goes like hell.

You will probably need a joystick because it seems that the numlock keypad is not working within the Linux and OSX version. That makes it a bit difficult to fly you' re plane, I can' t get used to flying with a mouse.

Enjoy

---

