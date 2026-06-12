---
title: "Error ! Required OpenGL extension &quot;GL_EXT_texture_sRGB_decode&quot; is not supported"
date: 2013-02-10
forum: Gaming &amp; Leisure
---

### Post by Angelgold45 on 2013-02-10
Hi all ,Everytime I try to open a game in steam that supports Linux I always get this error 

Error ! Required OpenGL extension "GL_EXT_texture_sRGB_decode" is not supported. Please update your OpenGL driver

I have no idea where to start to try fixing this please help I'm somewhat noobish

---

### Post by thnewguy on 2013-02-10
You didn't give much information as to which Ubuntu version you were using or what kind of video card, those would be useful. The first thing you should probably do is launch Steam and from the application's menu check for video driver updates. It will report on whether an upgrade is available for your card and give you the option to install the new version.

---

### Post by Angelgold45 on 2013-02-10
> **thnewguy said:**
> You didn't give much information as to which Ubuntu version you were using or what kind of video card, those would be useful. The first thing you should probably do is launch Steam and from the application's menu check for video driver updates. It will report on whether an upgrade is available for your card and give you the option to install the new version.

Im using Ubuntu 12.04 

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
Notebook-PC:~$ glxinfo | grep OpenGL
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200 Series
OpenGL version string: 3.3.11627 Compatibility Profile Context
OpenGL shading language version string: 3.30
OpenGL extensions:

and everything in steam is up to date

---

### Post by rudeboyskunk on 2013-02-10
You and I have the same graphics card.

This is because it uses the ATI Legacy Driver, which does not support many Valve Source games (GoldSrc yes, Source no).

So if you want to play TF2, Half-Life 2, L4D/2, Portal, CS: Source, CS:GO, etc etc (when they all eventually come out), you need to get a new graphics card.  Since you're using a laptop, I guess you need a new laptop.

---

### Post by snafu006 on 2013-02-10
> **rudeboyskunk said:**
> You and I have the same graphics card.

This is because it uses the ATI Legacy Driver, which does not support many Valve Source games (GoldSrc yes, Source no).

So if you want to play TF2, Half-Life 2, L4D/2, Portal, CS: Source, CS:GO, etc etc (when they all eventually come out), you need to get a new graphics card.  Since you're using a laptop, I guess you need a new laptop.


you are wrong

 i have the same card as him and i can play TF2 CS:GO all them. here is where i found this [http://steamcommunity.com/app/221410/discussions/0/846938351012409765/#p7](http://steamcommunity.com/app/221410/discussions/0/846938351012409765/#p7)

step 1 open terminal

(past) 
sudo apt-get install libc6-dev-i386
hit enter 
enter you login password



                 to make it work with the new 13.1 legacy drivers on a radeon hd  4250, i had to COMPLETELY UNINSTALL the old drivers first (otherwise i  would get the same sRGB error): 
sudo sh /usr/share/ati/fglrx-uninstall.sh --force
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
-> i removed the workaround described in this topic (it was useful for some time, big thanks)
-> after reboot, installed the new ones:
sudo sh 'REPLACE-WITH-PATH-TO-amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' --force
-> then rebooted again.
-> (optional) made some performance adjustments in the catalyst control center panel 

started steam (not from console, directly now). it works!

P.S If you cant find the ATI drivers 13.1 i have them why i am saying this is because the ATI site is no letting me download from there website so if you can get them then NVM

---

### Post by Angelgold45 on 2013-02-11
> **snafu006 said:**
> you are wrong

 i have the same card as him and i can play TF2 CS:GO all them. here is where i found this [http://steamcommunity.com/app/221410/discussions/0/846938351012409765/#p7](http://steamcommunity.com/app/221410/discussions/0/846938351012409765/#p7)

step 1 open terminal

(past) 
sudo apt-get install libc6-dev-i386
hit enter 
enter you login password



                 to make it work with the new 13.1 legacy drivers on a radeon hd  4250, i had to COMPLETELY UNINSTALL the old drivers first (otherwise i  would get the same sRGB error): 
sudo sh /usr/share/ati/fglrx-uninstall.sh --force
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
-> i removed the workaround described in this topic (it was useful for some time, big thanks)
-> after reboot, installed the new ones:
sudo sh 'REPLACE-WITH-PATH-TO-amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' --force
-> then rebooted again.
-> (optional) made some performance adjustments in the catalyst control center panel 

started steam (not from console, directly now). it works!

P.S If you cant find the ATI drivers 13.1 i have them why i am saying this is because the ATI site is no letting me download from there website so if you can get them then NVM


Thank you the only problem I have is the

"sudo sh 'REPLACE-WITH-PATH-TO-amd-driver-installer-catalyst-13.1-legacy-linux-"
step

i replaced the path to and everything and the terminal keeps giving me

"sh: 0: Can't open /home/blah/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run"

---

### Post by snafu006 on 2013-02-11
> **Angelgold45 said:**
> Thank you the only problem I have is the

"sudo sh 'REPLACE-WITH-PATH-TO-amd-driver-installer-catalyst-13.1-legacy-linux-"
step

i replaced the path to and everything and the terminal keeps giving me

"sh: 0: Can't open /home/blah/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run"

just do this open terminal type:

sudo sh ( then just drag and drop the ati driver into terminal ) --force

example: sudo sh '/home/snafu/Desktop/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' --force

---

### Post by rudeboyskunk on 2013-02-12
I keep trying to build the package and it keeps giving me errors.

```
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.BJc3CX'
dh_shlibdeps -l/tmp/fglrx.BJc3CX/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.BJc3CX/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: symbol dlsym used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XInitExtension used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol sem_close used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XCloseDisplay used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XOpenDisplay used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XDisplayString used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XQueryExtension used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: 12 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XOpenDisplay used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReadPad used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFree used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlsym used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XGetErrorDatabaseText used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol dlclose used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XMaxRequestSize used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XCreateGC used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XFreeFontInfo used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XEHeadOfExtensionList used by debian/fglrx/usr/lib/fglrx/libGL.so.1.2 found in none of the libraries.
dpkg-shlibdeps: warning: 22 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerAg.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libamdocl64.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libSlotMaximizerBe.so debian/fglrx/usr/lib/fglrx/libOpenCL.so.1 debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.BJc3CX'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.uJmaNq

```

This is the last part of the terminal output, where all the errors start.  I have all of the dependencies installed (according to the AMD install site).

Any ideas?

---

