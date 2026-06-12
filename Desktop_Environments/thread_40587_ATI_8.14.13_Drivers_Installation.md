---
title: "ATI 8.14.13 Drivers Installation"
date: 2005-06-09
forum: Desktop Environments
---

### Post by JGJones on 2005-06-09
New ATI drivers for Linux and it is great....good FPS increase according to glxgears (maximised in 1600x1200) - previously I was getting about 400fps maximised, now I get over 2500fps.

Even better....they have a wonderful easy to use installer for Linux available now - much better than anything nvidia offers (last time I looked) as it is a GUI installer!

GUI Installer is a much bigger download though, but for those that want a nice easy installer it works very very well, but fglrxconfig is still done in text afterward, but it's nice to have the installation done easily.

Hopefully this will help those that have had problems with installing ATI and getting 3D hardware acceleration up and running (I spent a few days getting 3D to work on last version)

Link to ATI Installer (35.1Mb) - [http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run)

Link to ATI RPM for XOrg (8.3Mb) - [http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.14.13-1.i386.rpm](http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.14.13-1.i386.rpm)

For ATI Installer just open up terminal and go to the directory you saved the .run file in.

type:

sudo sh ati-driver-installer-8.14.13.run

For RPM...well I didn't do that, but previous driver instruction should apply.

---

### Post by sapo on 2005-06-09
so you have just installed it and overwrite the old driver and it worked? withou problems or some kind of config error?

---

### Post by luca.costantino on 2005-06-10
[QUOTE=JGJones]

CUT

For ATI Installer just open up terminal and go to the directory you saved the .run file in.

type:

sudo sh ati-driver-installer-8.14.13.run


[/QUOTE]

i have a big problem...
i have just dowloaded the installer, but when I try to install the drivers i receive an error...
-------------------
root@hfish:/home/hfish/Desktop # sh ati-driver-installer-8.14.13.run
Creating directory fglrx-install
Verifying archive integrity...Error in MD5 checksums: aa50921687ab56ede6a5d9e665e03e8c is different from 8562a7f5b3a0bc52f3ea4c78a96f1ac0
root@hfish:/home/hfish/Desktop # 
------------------

what do I havr to do??
thanks :)

---

### Post by JGJones on 2005-06-10
[QUOTE=luca.costantino]i have a big problem...
i have just dowloaded the installer, but when I try to install the drivers i receive an error...
-------------------
root@hfish:/home/hfish/Desktop # sh ati-driver-installer-8.14.13.run
Creating directory fglrx-install
Verifying archive integrity...Error in MD5 checksums: aa50921687ab56ede6a5d9e665e03e8c is different from 8562a7f5b3a0bc52f3ea4c78a96f1ac0
root@hfish:/home/hfish/Desktop # 
------------------

what do I havr to do??
thanks :)[/QUOTE]

sudo before the command (but since it failed checksum, download it again to make sure)

By the way, 2nd post in thread raised a good point, before I installed the driver I did uninstall the previous driver via apt-get remove.

The only snag I got was that I lost mouse wheel scroll but since I had made a backup of xorg.conf file, I just copied the old mouse settings over and problem fixed.

No other errors whatsoever - I am surprised and I might be the only lucky one :) But I tried it on another machine....works just the same.

---

### Post by Razman on 2005-06-10
Can I see the video device section in xorg.conf  from the ATI made script?

My glgears went from 1155FPS to 113FPS
and UT2004 says it cannot access the glx subsystem.

---

### Post by thewebguy on 2005-06-10
do either of you have any idea if this would be safe to try on a radeon mobility 9700 ?

orrrrr, if you're not sure, can you tell me how i can back whatever i need to up before i try it (and how to revert), so i can be the one to see if it's safe?

---

### Post by Razman on 2005-06-10
[QUOTE=thewebguy]do either of you have any idea if this would be safe to try on a radeon mobility 9700 ?

orrrrr, if you're not sure, can you tell me how i can back whatever i need to up before i try it (and how to revert), so i can be the one to see if it's safe?[/QUOTE]
 You need to back up, for sure /etc/X11/xorg.conf
Which I didn't! hehe

but had I, I could've just put that back.

I have everything worknig, just UT2004 won't work and  fglrxinfo say the following

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
and It isn't using the ATI gl subsystem, which it was previous to these driver updates.

---

### Post by bryan986 on 2005-06-11
I had the same issue, but I got it to work, try this:

I am using kde, but this should still be helpful for gnome as well

write these down because it drops to console

1. stop kde kdm "sudo /etc/init.d/kdm stop", or for gnome gdm "sudo /etc/init.d/gdm stop"
2. install the ati drivers with the .run package
3. do "sudo fglrxconfig" to setup the drivers
4. I restarted my comptuer here just to be safe, but starting kdm/gdm up again might work as well

My stats:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)

glxgears
20135 frames in 5.0 seconds = 4027.000 FPS
21681 frames in 5.0 seconds = 4336.200 FPS
21671 frames in 5.0 seconds = 4334.200 FPS
21725 frames in 5.0 seconds = 4345.000 FPS

fgl_glxgears
3212 frames in 5.0 seconds = 642.400 FPS
3991 frames in 5.0 seconds = 798.200 FPS
3979 frames in 5.0 seconds = 795.800 FPS
3979 frames in 5.0 seconds = 795.800 FPS
3991 frames in 5.0 seconds = 798.200 FPS

Now I just have to tackle dual monitor mode

[QUOTE=Razman]You need to back up, for sure /etc/X11/xorg.conf
Which I didn't! hehe

but had I, I could've just put that back.

I have everything worknig, just UT2004 won't work and  fglrxinfo say the following

```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
and It isn't using the ATI gl subsystem, which it was previous to these driver updates.[/QUOTE]

---

### Post by jarno on 2005-06-11
And it still seems not to support DVI on Radeon 9200-cards  ](*,) 
I think I'm going to buy Matrox G550.

--
    /jarno

---

### Post by brj on 2005-06-13
[QUOTE=jarno]And it still seems not to support DVI on Radeon 9200-cards  ](*,) 
I think I'm going to buy Matrox G550.

--
    /jarno[/QUOTE]

same problem here,

dvi-output is detected as primary head, but it stays dark :(
(i have no problem when running WinXP, so it has do be a driver issue)

jakob

---

### Post by Segovia on 2005-06-13
[QUOTE=JGJones]good FPS increase according to glxgears (maximised in 1600x1200) - previously I was getting about 400fps maximised, now I get over 2500fps.[/QUOTE]
You call that a "good" increase?  I'd say that's nothing short of astonishing.   ;-) 

However, I'm fairly certain that you didn't have your previous drivers configured properly, since I can attain 400fps in glxgears with no hardware acceleration at all.   [-X

---

### Post by bryan986 on 2005-06-13
I am using a dvi->vga adapter for my lcd monitor, so my dvi out port is working

I also got dual screens working successfully with flgrxconfig, with my lcd on the left, and my crt on the right, the lcd is using the dvi port with a vga adapter, and the crt is on the vga port

---

### Post by merc on 2005-06-13
[QUOTE=bryan986]I am using a dvi->vga adapter for my lcd monitor, so my dvi out port is working

I also got dual screens working successfully with flgrxconfig, with my lcd on the left, and my crt on the right, the lcd is using the dvi port with a vga adapter, and the crt is on the vga port[/QUOTE]

As far as I know, a DVI-I port carries an analog signal (for crt) as well as digital signals (for dvi).

So if you have a dvi-vga adapter, its only using the analog signals to drive your  monitor. The other guys have actual lcd monitors that need the digital signal, which they claim  is not working.

For all you know, your dvi port might not be giving out digital signal either.

---

### Post by brj on 2005-06-13
[QUOTE=merc]As far as I know, a DVI-I port carries an analog signal (for crt) as well as digital signals (for dvi).

So if you have a dvi-vga adapter, its only using the analog signals to drive your  monitor. The other guys have actual lcd monitors that need the digital signal, which they claim  is not working.

For all you know, your dvi port might not be giving out digital signal either.[/QUOTE]

that sounds reasonable and explains why he's the only one who has a working dvi-output. so it looks like ati is not capable of providing a linux-driver supporting all features of their graphic-cards  :???: 

jakob

---

### Post by norepie on 2005-06-16
In reply to several of the mesg. with the MESA driver.  I tried this on Fedora Core 3 and 4, same result each time.  The FGLRX driver loads; However, I still have the MESA Open GL running.  I tried to build the custom Kernel and it errored.  So yes I tried the new ATI installer.  The following is the error that is generated.  The Open GL drivers for ATI and kernel module are not compiled.  This might be the problem below with building the special kernel module.

If you don't look at the ATI log or the build log, you don't know the OpenGL modules are not being built and installed

Card=ATI 9600 Extasy / 400mhz / 256DDR / AGP

[root@localhost fglrx-install]# ./check.sh
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 6.8.2

libglx.a / libdri.a are still of the MESA Opengl so when you fglrxinfo:

[root@localhost ~]# fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


The compile build error has a count of 2 and will not allow you to perform the install.

root@localhost build_mod]# ./make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.11-1.1369_FC4/build SUBDIRS=/download/ati/lib/modules/f                          glrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
  CC [M]  /download/ati/lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /download/ati/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
/download/ati/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.c:57: error: static d                          eclaration of ‘__fgl_agp_try_unsupported’ follows non-static declaration
/download/ati/lib/modules/fglrx/build_mod/2.6.x/agp_backend.h:92: error: previou                          s declaration of ‘__fgl_agp_try_unsupported’ was here
make[2]: *** [/download/ati/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o] Erro                          r 1
make[1]: *** [_module_/download/ati/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
make: *** [kmod_build] Error 2
build failed with return value 2

So does anyone have any ideas on what the fix is.  I have seen the MESA ghost all over the internet, but no one has looked at the maybe the build is failing.  AT least this is true for Fedora / so maybe the same with RedHAt and others.

For the funny note!! At least the Control Panel Works with the FGLRX driver loaded.
Gives you info about your card and points out your using MESA OPEN GL.

Norepie

---

### Post by brj on 2005-06-17
[QUOTE=brj]that sounds reasonable and explains why he's the only one who has a working dvi-output. so it looks like ati is not capable of providing a linux-driver supporting all features of their graphic-cards  :???: 

jakob[/QUOTE]


the current ati-driver has a problem with the dvi-output of the radeon 9200:

[http://ati.cchtml.com/show_bug.cgi?id=69](http://ati.cchtml.com/show_bug.cgi?id=69)

jakob

---

### Post by bryan986 on 2005-06-17
> **norepie]In reply to several of the mesg. with the MESA driver.  I tried this on Fedora Core 3 and 4, same result each time.  The FGLRX driver loads said:**
> # ./check.sh
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 6.8.2

libglx.a / libdri.a are still of the MESA Opengl so when you fglrxinfo:

[root@localhost ~]# fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


The compile build error has a count of 2 and will not allow you to perform the install.

root@localhost build_mod]# ./make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.11-1.1369_FC4/build SUBDIRS=/download/ati/lib/modules/f                          glrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
  CC [M]  /download/ati/lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /download/ati/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
/download/ati/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.c:57: error: static d                          eclaration of ‘__fgl_agp_try_unsupported’ follows non-static declaration
/download/ati/lib/modules/fglrx/build_mod/2.6.x/agp_backend.h:92: error: previou                          s declaration of ‘__fgl_agp_try_unsupported’ was here
make[2]: *** [/download/ati/lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o] Erro                          r 1
make[1]: *** [_module_/download/ati/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
make: *** [kmod_build] Error 2
build failed with return value 2

So does anyone have any ideas on what the fix is.  I have seen the MESA ghost all over the internet, but no one has looked at the maybe the build is failing.  AT least this is true for Fedora / so maybe the same with RedHAt and others.

For the funny note!! At least the Control Panel Works with the FGLRX driver loaded.
Gives you info about your card and points out your using MESA OPEN GL.

Norepie

did you try my what I suggested in my post on the first page of this topic?

[http://ubuntuforums.org/showpost.php?p=208111&postcount=8](http://ubuntuforums.org/showpost.php?p=208111&postcount=8)

---

### Post by NotSoSuperUser on 2005-06-18
Hi...

Tried everything here, but at the end of installations, it tells me during install there were errors, check /usr/share/fglrx/fglrx-install.log   ...or something along those lines, in the install log, it reads...

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.


Im pretty new to linux, some help appreciated please.

Cheers
Chris

---

### Post by dezgot on 2005-06-18
I installed with the installer and no error messages popped up, the config file it wrote has been properly found and applied (changed my resolution) and i can see the ATI control panel thing now, but glxgears runs at 150fps and flg_glxgears not at all.  I have a Sony S360 notebook with a Mobile 9700 64mb (M11).  ATI Control reports all my hardware correctly.  fgl_glxgears says:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32


When I run startx from the console it doesn't complain at all until the last thing it says: a warning:  "(EE) fglrx(0): incompatible kernel module detected - HW acceleration with OpenGL will not work." 


and it is right.  Can someone offer advice?  I am really new to linux, is there any other information that i could provide to help you guys help me?  

All problems aside, even though i still have no acceleration, the installer is quite impressive.

Thanks for any help.

BTW:  Ubuntu is great:  Everything worked out of the box except the modem (naturally, probably will never work) and right now i know that there is no power management working (not clocking down my Pentium M like the Suse liveeval CD did) and i don't know what even would provide that.  So far i love it.

---

### Post by norepie on 2005-06-18
Hy guys I found some patchs for the fglrx module fails to compile with gcc-4.0.0.

Mozilla bug 132 !!!

agpgart code! Problem



Common subdirectories: a/2.6.x and b/2.6.x

diff -puN a/agpgart_be.c b/agpgart_be.c

--- a/agpgart_be.c	2004-05-06 22:51:27.000000000 -0400

+++ b/agpgart_be.c	2004-06-17 12:44:19.000000000 -0400

@@ -1402,7 +1402,7 @@ unsigned long agp_generic_alloc_page(voi

     }

 #endif

- atomic_inc(&page->count);
+ get_page(page);
set_bit(PG_locked, &page->flags);
atomic_inc(&agp_bridge.current_memory_agp);

@@ -1449,7 +1449,7 @@ void agp_generic_destroy_page(unsigned l
put_page(page);
UnlockPage(page);
#else /* AGPGART_2_4_19 */
- atomic_dec(&page->count);
+ __put_page(page);
clear_bit(PG_locked, &page->flags);
wake_up(&page->wait);
#endif /* AGPGART_2_4_19 */
@@ -4413,7 +4413,7 @@ static unsigned long ali_alloc_page(void
if (page == NULL)
return 0;

- atomic_inc(&page->count);
+ get_page(page);
set_bit(PG_locked, &page->flags);
atomic_inc(&agp_bridge.current_memory_agp);

@@ -4509,7 +4509,7 @@ static void ali_destroy_page(unsigned lo
put_page(page);
UnlockPage(page);
#else /* AGPGART_2_4_19 */
- atomic_dec(&page->count);
+ __put_page(page);
clear_bit(PG_locked, &page->flags);
wake_up(&page->wait);
#endif /* AGPGART_2_4_19 */
diff -puN a/firegl_public.c b/firegl_public.c
--- a/firegl_public.c 2004-03-17 17:00:29.000000000 -0500
+++ b/firegl_public.c 2004-06-17 12:44:54.000000000 -0400
@@ -2010,7 +2010,7 @@ static __inline__ vm_nopage_ret_t do_vm_
pMmPage = virt_to_page(kaddr);
#endif /* LINUX_VERSION_CODE < 0x020400 */

- atomic_inc(&(pMmPage->count)); /* inc usage count of page */
+ get_page(pMmPage); /* inc usage count of page */

#if LINUX_VERSION_CODE >= 0x020400
// __KE_DEBUG3("vm-address 0x%08lx => kernel-page-address 0x%p\n",
@@ -2052,7 +2052,7 @@ static __inline__ vm_nopage_ret_t do_vm_
// Don't increment page usage count, cause ctx pages are allocated
// with drm_alloc_pages, which marks all pages as reserved. Reserved
// pages' usage count is not decremented by the kernel during unmap!!!
- atomic_inc(&(pMmPage->count)); /* inc usage count of page */
+ get_page(pMmPage); /* inc usage count of page */
#endif

#if LINUX_VERSION_CODE >= 0x020400 

Have not had time to try it out yet!

Norepie

---

### Post by beefsprocket on 2005-06-18
[QUOTE=dezgot]I installed with the installer and no error messages popped up, the config file it wrote has been properly found and applied (changed my resolution) and i can see the ATI control panel thing now, but glxgears runs at 150fps and flg_glxgears not at all.  I have a Sony S360 notebook with a Mobile 9700 64mb (M11).  ATI Control reports all my hardware correctly.  fgl_glxgears says:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32


When I run startx from the console it doesn't complain at all until the last thing it says: a warning:  "(EE) fglrx(0): incompatible kernel module detected - HW acceleration with OpenGL will not work." 
[/QUOTE]
Same Problem here. Back with the xorg-drivers-fglrx package for now.

---

### Post by dezgot on 2005-06-18
See, i know so little i didn't even know that there was a package like that.  I installed it and everything is working here (unless my cpu can get 1500fps, which is lower than i was expecting.  Except the external vga port, which i guess i don't need.   And the CPU throttling.  But i would still like to know about my previous post if anyone comes up with anything.

---

### Post by AndreAPL on 2005-07-04
can't get it working... at the end of install i get a error... kernel not suported ? 2.6.10, amd64  :neutral: 
tryed rpm > deb and still couldn't get it working  :-? (giving a incorrect install, and library problems)

---

