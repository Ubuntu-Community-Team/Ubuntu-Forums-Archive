---
title: "&quot;Cannot Enable Desktop Effects&quot; Intel Graphics, Ubuntu 9.04 Beta"
date: 2009-04-11
forum: General Help
---

### Post by zephyrcat on 2009-04-11
I am getting the "Unable to Enable Desktop Effects" dialog when I try to enable desktop effects. I am aware that there are many, many threads about this already, but my problem seems to be somewhat different.

I have used Compiz Fusion on this same computer before and have also experienced the "Unable to Enable bla bla bla" message popping up randomly before.

I am using Intel integrated graphics:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```
This is the output of compiz-check:
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected. 

Would you like to know more? (Y/n) 

```
I have disabled the blacklist, but then I get hung at a screen where I can only see the desktop background (no menus, etc.).

My PCI ID is also *not* listed as blacklisted on the Compiz Fusion site:

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

Thanks!

---

### Post by Tipped OuT on 2009-04-11
Try re-installing Ubuntu, or installing the official drivers for your graphics card.

---

### Post by zephyrcat on 2009-04-11
As far as reinstalling, I just installed Ubuntu 9.04. (I don't think this a 9.04 bug, though.)

I just tried installing the drivers from this page:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=865&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=865&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng)

This is what happened:
```
DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Welcome to the DRI Driver Installation Script

The package you downloaded is for the following driver: 

Driver Name    : gdg
Description    : Intel 830M/845G/852GM/855GM/865G/915G Driver
Architecture   : I386
Build Date     : 20040604
Kernel Module  : gdg

Optional Information

Driver Version      :  
Special Description :  

Press ENTER to continue or CTRL-C to exit.



DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

Select from the following options:

  1. Install driver (default)
  2. Uninstall driver

Enter reponse [1-2], or CTRL-C to exit
1
get_osname()










DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ http://dri.sourceforge.net ]

==========================================================================

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```
This is dri.log:
```
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/thomas/Desktop/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/thomas/Desktop/dripkg/agpgart-2.0/backend.o
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/thomas/Desktop/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/thomas/Desktop/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/thomas/Desktop/dripkg/drm'
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.28-11-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
rm: cannot remove `/home/thomas/Desktop/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/thomas/Desktop/dripkg/drm'
make: *** [gdg.ko] Error 2
```

---

### Post by djbushido on 2009-04-11
From the make log, it appears that the driver is coded wrong - > home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:220: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;drm_agp&#8217;
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_add_bridge&#8217;:
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function &#8216;inter_module_register&#8217;
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: &#8216;drm_agp&#8217; undeclared (first use in this function)
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_remove_bridge&#8217;:
/home/thomas/Desktop/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function &#8216;inter_module_unregister&#8217;

All those errors indicate that the source can't compile.
Two questions then:
How old is your computer? In general, computers over 3-5 years old have extreme difficulty with compiz
Also, did the hardware driver manager not recognize the card? This tool is quite useful (System->Administration->Hardware Manager <or something like that>), and has saved me hours of nvidia pain.
Overall, it just sounds like your computer is too old. Could just be me.
Also, check to make sure that you have all dependencies installed, this could be referencing a library that didn't get included because it wasn't on the system. If that doesn't work, check with Intel - their driver could be defective.

---

### Post by tkelito on 2009-04-11
It looks like the drivers you are trying to install are from 2004, way out of date.  

I have never played with Intel Drivers for Linux but try this website:

[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

Good luck.

-tkelito

---

### Post by zephyrcat on 2009-04-18
As far as reinstalling, I just installed Ubuntu 9.04. I have used Ubuntu on this computer for a couple years and Compiz (well, Beryl originally) has almost always worked.

As far as the new drivers, is this the page I need to follow (the whole stack building part)?

[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

That looks like it would take forever.

---

### Post by SESF0908 on 2009-04-23
I have the same problem, compiz work fine in ubuntu 8.10, but when i upgrade to 9.04, it doesn't work.
I think the problem is that desktop effects set to "none", so i set it to normal, and it show this: "Desktop effects could not be enable"
I use a F80Lseries asus laptop, VGA intel GMA x3100 Glx.

I don't think this is a bug.

sorry for may bad english.

---

### Post by umaxtu on 2009-04-24
I'm having the same problem with my Dell Optiplex gx270 It worked beautifully on 8.10 it handled nearly everything compiz threw at it. It is Intel graphics as well hmmmm. Attached is a screenie with my graphics info.

---

### Post by alvaourr on 2009-04-26
Hi guys hope this helps.

I had the same problem as SESF0908, after upgrading but found this [**workaround**]("http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html") (All credits to guy on that site pls):


> In the new Ubuntu 9.04 Jaunty Jackalope, Intel graphic (video) drivers 965 (x3000 or x3100) are blacklisted so you cannot run Compiz thus your desktop effects cannot be enabled. There is a way to enable desktop effects, though this is not recommended because the drivers were blacklisted due to an error in xserver-xorg-video-intel and they will be whitelisted when the bug fill be fixed.

But if you want to use Compiz anyway, all you have to do is type this in a terminal:

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager



PS: For the "newer people, remember to add sudo to the start of the command above. :)

---

### Post by jtanmay on 2009-04-26
> **alvaourr said:**
> Hi guys hope this helps.

I had the same problem as SESF0908, after upgrading but found this [**workaround**]("http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html") (All credits to guy on that site pls):




PS: For the "newer people, remember to add sudo to the start of the command above. :)

Worked for me.
Thanks :)

---

### Post by waynoworlater on 2009-05-17
Thanks so much for the help! I love Ubuntu, especially for my Acer Aspire One. The NetBook Remix is awesome for those who haven't tried it.

but anyway, the terminal hack works ace, just type it in like said above.

:KS

> mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

### Post by mjschmidt on 2009-05-22
I'm trying this terminal command, but I keep getting Permission Denied.

I am a newb, but I am using sudo in front of the command, and I guess I am root because I am the only user.

Why is this happening? How can I get it to work? (simple explanation please. :-) )

---

### Post by beak02 on 2009-06-06
> **mjschmidt said:**
> I'm trying this terminal command, but I keep getting Permission Denied.

I am a newb, but I am using sudo in front of the command, and I guess I am root because I am the only user.

Why is this happening? How can I get it to work? (simple explanation please. :-) )

It could be something simple like your entering your password incorrectly (been there, done that - it's easily done!) It could also be that you've entered a different root password (though by default this should be the same as your login I think).

As a Side point that command doesn't appear to be working for me - I have the problem that is described above but entering the command seems to have no effect, apart from a white-out before it refuses to enable desktop effects.

---

