---
title: "Xgl + Compiz with DRI on a i915"
date: 2006-02-21
forum: Desktop Environments
---

### Post by iMil on 2006-02-21
Hi there,

I managed running Xgl + Compiz on a IBM X41 laptop, using DRI with an Intel  i915 graphic card. The cube spins smoothly, woggle and 2d ops are obviously far from the results obtained with a NVidia card.
Please note this is a 1st shot, there still has problems with gdm and such, now it's up to you ;)

Here are the steps :

. Get latest DRI snapshots from [http://dri.freedesktop.org/snapshots/]("http://dri.freedesktop.org/snapshots/"), for this test I   used  [http://dri.freedesktop.org/snapshots/common-20060206-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/common-20060206-linux.i386.tar.bz2") [http://dri.freedesktop.org/snapshots/i810-20060206-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/i810-20060206-linux.i386.tar.bz2") and [http://dri.freedesktop.org/snapshots/i915-20060206-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/i915-20060206-linux.i386.tar.bz2")

. uncompress the three archives and mv (common, i810 then i915 in this order) directories content to a single directory :

mkdir all
mv common-20060206-linux.i386/* all/
mv i810-20060206-linux.i386/* all/
mv i915-20060206-linux.i386/* all/

. create a temporary X directory

mkdir /home/you/fakeX

. Execute install.sh in the "all" directory

. specify "/home/you/fakeX" as the X11R6 directory

. Copy the content of /home/you/fakeX/lib/modules/ to /usr/lib/xorg/modules/

cp -R /home/you/fakeX/lib/modules/* /usr/lib/xorg/modules/

. Check that the i915 module is loaded

$ lsmod|grep 915
i915                   22240  0 
drm                    80920  1 i915

. Have a look at your dmesg, you should have something similar to :

[4302209.541000] [drm] Initialized i915 1.4.0 20060119 on minor 0: 

. In your /etc/X11/xorg.conf, check you have the following

Section "Module"
        [...]
        Load    "dri"
        Load    "glx"
        [...]
EndSection

[...]

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL"
        Driver          "i810"
        VideoRam        131072
        Option          "DRI" "true"
EndSection

[...]

Section "DRI"
        Mode    0666
EndSection

. If you hadn't, stop gdm

# /etc/init.d/gdm stop

. Execute Xorg (yes, just Xorg, to figure out if DRI works)

# X

. Have a look at your /var/log/Xorg.0.log, you should see something like :

(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled

. Start gdm (still using Xorg)

. Check if everything's OK with your DRI / GLX extensions :

$ glxinfo|grep direct
direct rendering: Yes

FYI on the X41 i tried, i had about 1300 FPS with a glxgears -printfps

. IF YOU SEE a message complaining about libGL when launching glxinfo or glxgears, reinstall libgl1-mesa and libgl1-mesa-dri

. Stop gdm

/etc/init.d/gdm stop

. Start Xgl

# Xgl &

. Hit Ctrl-Alt-<Fkey> to return to the console. Launch an xterm from here

# DISPLAY=:0.0 xterm

. Hit Ctrl-Alt-F7 to return to Xgl

from here, get back to previous threads to launch compiz, gnome-window-decorator and friends :)

WARNING, I got lots of Xgl segfaults when playing with gnome-session

Have fun

---

### Post by houseofmore on 2006-02-25
Any idea if these will make it into the final dapper?

---

### Post by nzjrs on 2006-03-08
I am a little confused. How Is this dri driver different to the i810 driver currenlty in dapper flght 4?

---

### Post by elanthis on 2006-03-08
It's got all the latest CVS work that isnt' in any official driver releases yet.  Including various fixes and such that is required for Compiz to perform adequately.

---

### Post by firingstone on 2006-03-08
:) that is very nice of you share this
Hope to get no errors on the final Dapper

---

### Post by arrizaba on 2006-03-08
I have been looking how to instal Xgl on a i915 graphics card and I did not find anything....until now! Thnx!

---

### Post by aslocum on 2006-03-08
strange.. all i had to do to get it working was to install xgl and start it :)

i915gm

---

### Post by Tharna on 2006-03-08
[QUOTE=aslocum]strange.. all i had to do to get it working was to install xgl and start it :)

i915gm[/QUOTE]

Same here. But does this new dri fix the scrolling issues? If it does, I think I'll be trying this out.

---

### Post by anil_robo on 2006-03-08
[quote=aslocum]strange.. all i had to do to get it working was to install xgl and start it :)

i915gm[/quote]

I have i915GM and have installed xgl and compiz from synaptic. Why can't I run compiz?
```
anil_robo@rakshak:~$ gnome-window-decorator
gnome-window-decorator, Failed to load shadow images
anil_robo@rakshak:~$ thefuture
bash: thefuture: command not found
anil_robo@rakshak:~$ compiz
anil_robo@rakshak:~$ compiz.real: No composite extension

```:(

---

### Post by jamesshuang on 2006-03-09
exactly like it says - you don't have composite extension. 
Add this to your /etc/X11/xorg.conf: 

```

Section "Extensions"
    Option "Composite" "true"
EndSection

```

---

### Post by Fudgie on 2006-03-09
You get those messages when you try and run gnome-window-decorator and compiz from regular Xorg instead of Xgl. 

thefuture is a custom script to start compiz, not distributed with the debs.

---

### Post by Paloseco on 2006-03-09
My bash says that display was not found. :???:

---

### Post by elanthis on 2006-03-09
> exactly like it says - you don't have composite extension.
Add this to your /etc/X11/xorg.conf: 

That's wrong.  That setting is for *X.org*, not Xglx.  Compiz doesn't yet run on X.org, and won't until AIGLX is landed.  Compiz only runs on Xglx.  Xglx has built-in composite support that is completely independent of the composite support of the parent X.org server.

If you run inside of Xglx, you'll always have composite enabled.

---

### Post by anil_robo on 2006-03-10
[quote=elanthis]That's wrong.  That setting is for *X.org*, not Xglx.  Compiz doesn't yet run on X.org, and won't until AIGLX is landed.  Compiz only runs on Xglx.  Xglx has built-in composite support that is completely independent of the composite support of the parent X.org server.

If you run inside of Xglx, you'll always have composite enabled.[/quote]

That means I'm running xorg right now.
How do I run Xglx? I installed it from the repos :(

---

### Post by wlx on 2006-03-14
In Xorg, the glxinfo echo "direct Yes",
but in Xgl, the glxinfo echo "No", and it is not smooth.
What is the problem?

---

### Post by Fudgie on 2006-03-16
Xlg doesn't support direct rendering at the moment, and the intel drivers use a lot of software rendering until the driver gets fixes. There's been some work on this the last few days, so hopefully it won't be long now.

---

### Post by wlx on 2006-03-17
[QUOTE=Fudgie]Xlg doesn't support direct rendering at the moment, and the intel drivers use a lot of software rendering until the driver gets fixes. There's been some work on this the last few days, so hopefully it won't be long now.[/QUOTE]
Thank you!
It is a nice work.

---

### Post by Donald on 2006-03-17
Look at the "Howto Install xorg-aiglx + compiz (packages)" thread for an alternative to Xgl which also gives you all the fancy compiz-effects but runs *a lot* faster on an i915 (i810 driver class chipsets) at the moment.

---

### Post by firingstone on 2006-03-18
I got some problems with it 
first,how to run the install.sh double click and choose to run in terminal  or  type sudo ./install in the terminal ? Neither work on my pc.
second,why do we have to mv the three folders into one?

---

### Post by wlx on 2006-03-18
[QUOTE=firingstone]I got some problems with it 
first,how to run the install.sh double click and choose to run in terminal  or  type sudo ./install in the terminal ? Neither work on my pc.
second,why do we have to mv the three folders into one?[/QUOTE]
please follow the steps here:
[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)

---

### Post by firingstone on 2006-03-18
Yeah, I tried that.
Finally I reconfigured the xorg and let it recognize my 915 (it didn't in my fresh install)and follow the xgl howto.
Then I gooot the xgl stuff, it is awesome!!!

---

### Post by romaluca on 2006-03-18
when i can try to istall the i810-20060317-linux.i386
i receive this error 

Xorg Dir         : /home/romaluca/fakeX
Xorg Modules Dir : /home/romaluca/fakeX/lib/modules
Xorg Library Dir : /home/romaluca/fakeX/lib




DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script also needs to copy the DRM kernel modules to your
kernel module directory.

This version of the script supports 2.4.x and 2.6.x kernels.

Kernel Version   : 2.6.15-18-386
Module Directory : /lib/modules/2.6.15-18-386

If this is correct press ENTER, press C to change or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...done





DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

The script is now ready to complete the installation.

Press ENTER to continue or CTRL-C to exit.








DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.freedesktop.org](http://dri.freedesktop.org) ]

==========================================================================

Installing files:
        DRI Xorg modules...done
        kernel modules...done
        Copying extra files...done

Updating configuration:
        Removing old kernel module "i810"...done
        Inserting new kernel module "i810"...ERROR

There were errors updating the system configuration.
See the dri.log file for more information.

Checking configuration...done


In the file dri.log ther is:
make DRM_MODULES=i810.o modules
make[1]: Entering directory `/home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core'
+ ln -s ../shared-core/drm.h drm.h
+ ln -s ../shared-core/drm_sarea.h drm_sarea.h
+ ln -s ../shared-core/mga_dma.c mga_dma.c
+ ln -s ../shared-core/mga_drm.h mga_drm.h
+ ln -s ../shared-core/mga_drv.h mga_drv.h
+ ln -s ../shared-core/mga_irq.c mga_irq.c
+ ln -s ../shared-core/mga_state.c mga_state.c
+ ln -s ../shared-core/mga_ucode.h mga_ucode.h
+ ln -s ../shared-core/mga_warp.c mga_warp.c
+ ln -s ../shared-core/r128_drv.h r128_drv.h
+ ln -s ../shared-core/r128_drm.h r128_drm.h
+ ln -s ../shared-core/r128_cce.c r128_cce.c
+ ln -s ../shared-core/r128_state.c r128_state.c
+ ln -s ../shared-core/r128_irq.c r128_irq.c
+ ln -s ../shared-core/radeon_drv.h radeon_drv.h
+ ln -s ../shared-core/radeon_drm.h radeon_drm.h
+ ln -s ../shared-core/radeon_cp.c radeon_cp.c
+ ln -s ../shared-core/radeon_irq.c radeon_irq.c
+ ln -s ../shared-core/radeon_mem.c radeon_mem.c
+ ln -s ../shared-core/radeon_state.c radeon_state.c
+ ln -s ../shared-core/r300_cmdbuf.c r300_cmdbuf.c
+ ln -s ../shared-core/r300_reg.h r300_reg.h
+ ln -s ../shared-core/sis_drv.h sis_drv.h
+ ln -s ../shared-core/sis_drm.h sis_drm.h
+ ln -s ../shared-core/sis_ds.c sis_ds.c
+ ln -s ../shared-core/sis_ds.h sis_ds.h
+ ln -s ../shared-core/sis_mm.c sis_mm.c
+ ln -s ../shared-core/tdfx_drv.h tdfx_drv.h
+ ln -s ../shared-core/via_drm.h via_drm.h
+ ln -s ../shared-core/via_drv.h via_drv.h
+ ln -s ../shared-core/via_mm.h via_mm.h
+ ln -s ../shared-core/via_ds.h via_ds.h
+ ln -s ../shared-core/via_3d_reg.h via_3d_reg.h
+ ln -s ../shared-core/via_drv.c via_drv.c
+ ln -s ../shared-core/via_ds.c via_ds.c
+ ln -s ../shared-core/via_irq.c via_irq.c
+ ln -s ../shared-core/via_map.c via_map.c
+ ln -s ../shared-core/via_mm.c via_mm.c
+ ln -s ../shared-core/via_dma.c via_dma.c
+ ln -s ../shared-core/via_verifier.c via_verifier.c
+ ln -s ../shared-core/via_verifier.h via_verifier.h
+ ln -s ../shared-core/via_video.c via_video.c
+ ln -s ../shared-core/mach64_drv.h mach64_drv.h
+ ln -s ../shared-core/mach64_drm.h mach64_drm.h
+ ln -s ../shared-core/mach64_dma.c mach64_dma.c
+ ln -s ../shared-core/mach64_irq.c mach64_irq.c
+ ln -s ../shared-core/mach64_state.c mach64_state.c
+ ln -s ../shared-core/i915_drv.h i915_drv.h
+ ln -s ../shared-core/i915_drm.h i915_drm.h
+ ln -s ../shared-core/i915_irq.c i915_irq.c
+ ln -s ../shared-core/i915_mem.c i915_mem.c
+ ln -s ../shared-core/i915_dma.c i915_dma.c
+ ln -s ../shared-core/savage_drv.h savage_drv.h
+ ln -s ../shared-core/savage_drm.h savage_drm.h
+ ln -s ../shared-core/savage_bci.c savage_bci.c
+ ln -s ../shared-core/savage_state.c savage_state.c
+ ln -s ../shared-core/nv_drv.h nv_drv.h
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.15-18-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-18-386'
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_auth.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_bufs.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_context.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_dma.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_drawable.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_drv.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_fops.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_ioctl.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_irq.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_lock.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_memory.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_proc.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_stub.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_vm.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_sysfs.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_pci.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_agpsupport.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_scatter.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm_memory_debug.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/ati_pcigart.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/i810_drv.o
  CC [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/i810_dma.o
  LD [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm.o
  LD [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/i810.o
  Building modules, stage 2.
  MODPOST
  CC      /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm.mod.o
  LD [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/drm.ko
  CC      /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/i810.mod.o
  LD [M]  /home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core/i810.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-18-386'
make[1]: Leaving directory `/home/romaluca/Download/all/i810-20060317-linux.i386/drm/linux-core'
FATAL: Error inserting i810 (/lib/modules/2.6.15-18-386/kernel/drivers/char/drm/i810.ko): Unknown symbol in module, or unknown parameter (see dmesg)


What do i do?

---

### Post by damonw5 on 2006-03-18
I'll have to try this HOWTO sometime, but I found that using AIGLX + Compiz was MUCH faster on my i915 than XGL + Compiz. I can actually scroll through documents and web pages at a decent speed AND have my eye-candy!!!

---

### Post by GeneralZod on 2006-03-18
For anyone using this on a laptop - do you have any figures showing whether using XGL (or aiglx) improves or reduces battery life?  I know it takes the load off the CPU, but it then dumps it straight back onto the GPU which, while much more specialised, may not be as optimised for power-efficiency as the CPU.  It would be interesting to see which of the two factors is more important :)

---

### Post by anil_robo on 2006-03-18
My regular GNOME sessions keeps  stuck at "starting metacity window manager". I'm not able to do anything, nothing on desktop! :( no panels, no menus. :(

[IMG]http://img211.imageshack.us/img211/4937/metacityerror8sn.gif[/IMG]

However I am able to login to the "failsafe gnome" session. What wrong did I do? How do I get back metacity working? :(

---

### Post by motin on 2006-03-19
I only get this when trying to install:

> The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.


And dri.log quotes:

> + ln -s ../shared-core/savage_state.c savage_state.c
+ ln -s ../shared-core/nv_drv.h nv_drv.h
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.15-18-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-18-386'
Makefile:536: /usr/src/linux-headers-2.6.15-18-386/arch/i386/Makefile: Filen eller katalogen finns inte
make[2]: *** Ingen regel för att skapa målet "/usr/src/linux-headers-2.6.15-18-386/arch/i386/Makefile".  Stannar.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-18-386'
make[1]: *** [modules] Fel 2
make[1]: Leaving directory `/home/motin/all/drm/linux-core'
make: *** [i915.o] Fel 2

I have both the kernel-headers and the linux-source for 2.6.15 installed through synaptic. Wots the problem?

---

### Post by deepclutch on 2006-03-21
perhaps U should check ur kernel path-
/lib/modules/2.6.15-19-686/kernel/drivers/char/ for
drm.ko,i915.ko
already there.also modconf to make sure i915 is loaded...my tips...sometimes error doesnt mean it did not update your i915 module.if it updated there will be old module as "old.i915.ko.old" etc..so best of LUX :-D

---

### Post by Gizida on 2006-03-30
Tried it. Now Xorg hangs up and freezes everything, forcing me to go for that OFF button. the xorg log finishes on some (II) messages...

---

### Post by Vytas on 2006-04-25
I tried i915+ XGL (no Compiz) some time ago, using only packages from repositories. Everything was OK, except the speed was very slow

---

### Post by motin on 2006-05-10
> **iMil]Hi there,

I managed running Xgl + Compiz on a IBM X41 laptop, using DRI with an Intel  i915 graphic card. The cube spins smoothly, woggle and 2d ops are obviously far from the results obtained with a NVidia card.
Please note this is a 1st shot, there still has problems with gdm and such, now it's up to you  said:**
> http://dri.freedesktop.org/snapshots/[/url], for this test I   used  [http://dri.freedesktop.org/snapshots/common-20060206-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/common-20060206-linux.i386.tar.bz2) [http://dri.freedesktop.org/snapshots/i810-20060206-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/i810-20060206-linux.i386.tar.bz2) and [http://dri.freedesktop.org/snapshots/i915-20060206-linux.i386.tar.bz2](http://dri.freedesktop.org/snapshots/i915-20060206-linux.i386.tar.bz2)

. uncompress the three archives and mv (common, i810 then i915 in this order) directories content to a single directory :

mkdir all
mv common-20060206-linux.i386/* all/
mv i810-20060206-linux.i386/* all/
mv i915-20060206-linux.i386/* all/

. create a temporary X directory

mkdir /home/you/fakeX

. Execute install.sh in the "all" directory

. specify "/home/you/fakeX" as the X11R6 directory

. Copy the content of /home/you/fakeX/lib/modules/ to /usr/lib/xorg/modules/

cp -R /home/you/fakeX/lib/modules/* /usr/lib/xorg/modules/

. Check that the i915 module is loaded

$ lsmod|grep 915
i915                   22240  0 
drm                    80920  1 i915

. Have a look at your dmesg, you should have something similar to :

[4302209.541000] [drm] Initialized i915 1.4.0 20060119 on minor 0: 

. In your /etc/X11/xorg.conf, check you have the following

Section "Module"
        [...]
        Load    "dri"
        Load    "glx"
        [...]
EndSection

[...]

Section "Device"
        Identifier      "Intel Corporation 82915G/GV/910GL"
        Driver          "i810"
        VideoRam        131072
        Option          "DRI" "true"
EndSection

[...]

Section "DRI"
        Mode    0666
EndSection

. If you hadn't, stop gdm

# /etc/init.d/gdm stop

. Execute Xorg (yes, just Xorg, to figure out if DRI works)

# X

. Have a look at your /var/log/Xorg.0.log, you should see something like :

(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled

. Start gdm (still using Xorg)

. Check if everything's OK with your DRI / GLX extensions :

$ glxinfo|grep direct
direct rendering: Yes

FYI on the X41 i tried, i had about 1300 FPS with a glxgears -printfps

. IF YOU SEE a message complaining about libGL when launching glxinfo or glxgears, reinstall libgl1-mesa and libgl1-mesa-dri

. Stop gdm

/etc/init.d/gdm stop

. Start Xgl

# Xgl &

. Hit Ctrl-Alt-<Fkey> to return to the console. Launch an xterm from here

# DISPLAY=:0.0 xterm

. Hit Ctrl-Alt-F7 to return to Xgl

from here, get back to previous threads to launch compiz, gnome-window-decorator and friends :)

WARNING, I got lots of Xgl segfaults when playing with gnome-session

Have fun


This thread needs to be updated. 

I remembered that this thread helped me get DRI working on Dapper. Not while in Xgl, (no DRI in xgl), but in normal Xorg. 

Some questions: 
- What has happened with [http://dri.freedesktop.org/snapshots/?](http://dri.freedesktop.org/snapshots/?) The latest snapshot is from 2006-04-03 and the bleed egde directory is empty. Where does the development continue?
- Does Xgl work any better yet on laptops using i915?
- When I login to another gnome session all my settings are gone... How can I transfer settings from one session to another? Is it as simple as cp .gnome2 .gnome??

---

### Post by ahawks on 2006-05-23
I agree. I am running an hp nc6220 with an i915 card, and very very eager to get Xgl (or aiglx) + compiz running.

I tested with the Kororaa Xgl Live CD (Gentoo based :(), and it worked *beautifully* 

Following the instructions in this thread actually *broke* dri on my normal Xorg, and I never got gnome to launch without the server crashing.   Eventually (lastnight) I reinstalled Dapper from cd. 

Can anyone provide an update for Xgl on i915?  Are the latest DRI packages rolled into Flight 7? 8? ...?

---

### Post by dranger003 on 2006-05-30
I also think this thread needs to be updated.

I have been reading that some are getting DRI with Xgl and some other don't. I personnally never got DRI to work with Xgl... anyone can confirm this?

Also, I can only pull out ~800fps with a DRI enabled Xorg... anyone else getting the same results?

I am using an Intel i915GM in an IBM T43 laptop.

Thanks!

---

### Post by siDDis on 2006-05-30
I get 1500 fps with DRI and I have 950GMA and core duo.
Intel performance just pure sucks in linux. Bloody Intel, why cant they give us real drivers for Linux?

I just tried UT2004 on this machine and it was like ten timer slower in OpenGL compared to running it in software with the SAME settings.

---

### Post by psaur on 2006-06-01
I am really eager to get xgl to do something atleast on my laptop, but with no success yet. This morning I did a dist-upgrade to dapper and followed the instructions given at davehayes.org, 

[http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/](http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/)

I tried to follow the simple instructions given there, but when I tried to login, i got an error in my .xsession-errors

 i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1

This is perplexing, because I have 1:1.5.0 version of the i810 driver installed.  What could be wrong?

Thanks!

---

### Post by killbill on 2006-06-08
[QUOTE=psaur]I am really eager to get xgl to do something atleast on my laptop, but with no success yet. This morning I did a dist-upgrade to dapper and followed the instructions given at davehayes.org, 

[http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/](http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/)

I tried to follow the simple instructions given there, but when I tried to login, i got an error in my .xsession-errors

 i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1

This is perplexing, because I have 1:1.5.0 version of the i810 driver installed.  What could be wrong?

Thanks![/QUOTE]

Frankly, I followed this tutorial but got crashed.
And to ur question, you may try common and i915-20060330, then you won't get the error above. however. still no dri yet on my intel 845G card.

I got 
```

libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering

```
on dri according to glxinfo,
but it says it's enabled in Xorg.0.log.............

Any solution to this&#65311;

---

### Post by konradsa on 2006-06-25
[QUOTE=psaur]I am really eager to get xgl to do something atleast on my laptop, but with no success yet. This morning I did a dist-upgrade to dapper and followed the instructions given at davehayes.org, 

[http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/](http://www.davehayes.org/2006/05/22/howto-xgl-and-compiz-on-ubuntu-dapper-new-and-improved/)

I tried to follow the simple instructions given there, but when I tried to login, i got an error in my .xsession-errors

 i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1

This is perplexing, because I have 1:1.5.0 version of the i810 driver installed.  What could be wrong?

Thanks![/QUOTE]

Hi,

I used to have the same problem, and I don't remember exactly how I fixed it anymore, but I think I used

dpkg-reconfigure xserver-xorg

and changed the framebuffer settings there. Play around with that a little bit and try different options, it eventually worked for me. I think I changed the framebuffer interface setting around, try both yes and no.

---

### Post by gwi on 2006-07-05
[QUOTE=wlx]please follow the steps here:
[https://wiki.ubuntu.com/XglHowto](https://wiki.ubuntu.com/XglHowto)[/QUOTE]
Nice, must be the shortest howto ever :confused: 
```

XglHowto

This page does not exist yet. You can create a new empty page, or use one of the page templates. Before creating the page, please check if a similar page already exists. 

```

---

### Post by Cloud79 on 2006-07-05
I got it working by using this two repoisitories in sources.list

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

//Linus

---

### Post by obi-nine on 2006-08-31
I've created an updated guide to installing Compiz/Aiglx for i915 chipset:

[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

Hope it helps!

---

### Post by lobstaj on 2006-10-21
> **aslocum said:**
> strange.. all i had to do to get it working was to install xgl and start it :)

i915gm

Does it run smoothly though? I also tried xgl from the packages and it kind of worked, but not more. With the aiglx stuff from gandalfn ([http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/)) it works a lot better. At least on my i915 (don't know about gm or such).

---

