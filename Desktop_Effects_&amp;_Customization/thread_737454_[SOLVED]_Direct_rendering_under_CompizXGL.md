---
title: "[SOLVED] Direct rendering under Compiz/XGL"
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by +++ IGOR +++ on 2008-03-27
I have an Asus G2Pc laptop which I use with Compiz Fusion and XGL to get those advanced desktop effects. But I have a small problem. I don't seem to be able to get direct rendering to work. I have searched the net withouth finding anything to explain why I can't get DRI to work.

This is the output from fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6473 (8.37.6)


And this is the output from glxinfo:

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


I have to mention that I just followed the standard Ubuntu description on how to get compiz and xgl to work.

Except for my inability to get DRI up and running I haven't had any problems with compiz. I am just hoping that someone here has an idea on how i get DRI on my computer.

---

### Post by tzepu on 2008-03-27
hy all
i am having exactly the same problem, and all i want is to use googleearth and some games that need  direct rendering
any suggestions?

---

### Post by mrmiserable on 2008-03-27
ok the driver 8.37 cannot run compiz without xgl and uses indirect rendering old driver

new ati driver 8.3 can run compiz without xgl and you can have direct rendering so you have a choice stick with ubuntu drivers from repos or download new driver from ati make sure you have all dependencies installed before trying
here is a great trouble shooting guide and installation options 
i recommend making method 2 this way you can uninstall from synaptic as they are .deb files 

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

to get driver go here

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

ati drivers can be very difficult to install sometimes so beware if you are unsure


good luck after installation fglrxinfo should give this output but not X600 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.1.7412 Release

good luck

dont forget to uninstall all previous drivers first and xserver-XGL

---

### Post by +++ IGOR +++ on 2008-03-28
I followed the description you gave me mrmiserable and I finaly got it working. Thanks for the help. This webpage is getting saved to my hardrive.

:)

---

### Post by mrmiserable on 2008-03-28
glad it worked

also ati update their drivers every month

good luck next month

only joking it should be easy from now on

---

### Post by +++ IGOR +++ on 2008-03-28
I hope so, this is gonna give me sleeping problems with I have to wade thru fire each time I update the drivers :)

---

### Post by tzepu on 2008-03-29
well, sadly, for me it did not worked,
it kept giving me an error about not being able to unpack some 32 libs 
i didn't seen that and after reboot ...... i had to reinstall ubuntu, i did that again(i mean this [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) ) and it blocked again there at this command 'sudo apt-get install -f' , i managed to install them manually, it worked but now  i get this
fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
and
glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
so 
i can't see if my direct rendering is enabled and i can't enable desktop effects either
anyway, in restricted drivers it shows me that there are drivers in use but are not enabled, just as the guy in the guide says it should look
i will try to redo this from the begining, hope this time it will be better
L.E. when i try co create .deb packages i get this (and i thing that the problem with those 32 libs is the root for all those that comes after it )(because , as i said 'few rows' earlier i managed to install them separatelly, it works but it leads me to an 'dead end')

sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy
Created directory fglrx-install.AO6647
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.471.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
Resolving build dependencies...
./packages/Ubuntu/ati-packager.sh: 311: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/fileu3xWYp': not found
Unable to resolve  ia32-libs.  Please manually install and try again.
Removing temporary directory: fglrx-install.AO6647

and this is it
 any suggestions?
btw i downloaded the drivers from 2 different sources, i thought first one might be corrupted, but i got the exact same error

---

### Post by +++ IGOR +++ on 2008-03-29
It could be that your graphics card isn't supported, if you find the name it has and check it against the "blacklisted" drivers that ATI has relieced you can atleast rule that problem out.

---

### Post by mrmiserable on 2008-03-29
tzepu 

are you using 64bit 

if so please read all of the wiki page i gave as it gives you answers to all the questions you have asked

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

good luck

edit

Install necessary tools:

sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms

Uninstall previous fglrx: Using Synaptic, completely remove any packages containing "fglrx" in their name.

If using 64bit make sure to collect package "ia32-libs" and " libGL.so.1" before proceeding!

---

### Post by tzepu on 2008-03-29
my card is supported, and i know that because i installed few times on it compiz, and it worked, now i just reinstalled third time today ubuntu, and each time i went further than before, last time i succeeded to enable direct rendering but when i followed an 'how to' to enable compiz, after restart i got nothing but an blank screen and everything i tried was useless, so i had to reinstall ubuntu third time today
@mrmiserable 
now i will follow your link to see if it helps and i will tell you if you are my hero or not :)
L.E. i am not that good at english as i wish so please tell me what you mean by 'collect'

---

### Post by mrmiserable on 2008-03-29
by collect i mean install from synaptic or apt

the names are libgl1-mesa-swx11 

and ia32-libs (problem is i dont know this) but found this link to it

[https://launchpad.net/ubuntu/+source/ia32-libs/](https://launchpad.net/ubuntu/+source/ia32-libs/)

 also have you tried to install driver with the option

sudo ./ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu --autopkg

this should get dependencies i think but i have never used it 

hope you get there in the end

---

### Post by tzepu on 2008-03-30
i can not create the package with this
sudo ./ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu --autopkg because it gives me an error bad command or so
i follow 'this how to' [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide) but at the line 
sudo apt-get install -f i get this error (by not following if there is an error in executing this command it costs me 2 ubuntu reinstalls)

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xorg-driver-fglrx
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/12.3MB of archives.
After unpacking 34.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 96084 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/amdcccle', which is also in package fglrx-amdcccle
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_7.1.0-8.37.6+2.6.22.4-14.10_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

and if i continue folowing that post and ignoring this after restart i get an blank screen and i have to reinstall ubuntu (did that three times today)

i suppose there is the problem
any suggestion to pass this?
i tried few ideas but all of them ended in disaster
i managed to resolve that problem with force overwrite but i am stuck again right after it (i mean that nothing goes well after it)
now i can't do anything about it( redo all over again, open synaptic or terminal) and i have to reboot
i might need to reinstall ubuntu again because as i see i can do that just once, it fails, and after reboot all i get is that blank screen
but i am not quiting yet

---

### Post by tzepu on 2008-04-04
well
i am a happy man (even if my wife says that i am masochist)
after several ubuntu reinstalls i managed NOT to install video drivers as below
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)
quite a lot of errors (variate, not to get bored)
but i managed to solve all my problems (most of them caused by my nooblicity)
here is how i did it
i use an laptop Acer 5112wlmi 64bit,with an ATI X1600 video card and i use ubuntu 7.10 64biti, dual booting with vista, 
after a fresh install (i did not even enabled RDM) i updated and upgraded ubuntu
after rebooting i instaled necessary tools with the command

sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms

because i run 64bit OS on a 64bit machine i installed this too

sudo apt-get install ia32-libs

after all this i instaled latest version of envy from this place

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

i installed it,runed it, followed onscreen indications
after restart i've got the new ati driver running (with direct rendering enabled) 

thank you for your help and consideration
all best wishes

---

### Post by +++ IGOR +++ on 2008-04-07
I don't know if MrMiserable is reading this thread anymore but I think he would be glad to se that his advice worked for you too :)

---

