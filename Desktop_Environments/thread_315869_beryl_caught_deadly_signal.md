---
title: "beryl caught deadly signal"
date: 2006-12-09
forum: Desktop Environments
---

### Post by Chenzo on 2006-12-09
I am running beryl through xgl using the fglrx video drivers (radeon X800) in 64 bit edgy.  When I installed beryl 0.1.1 everything worked fine. After upgrading to Beryl 0.1.2 I get this error when typing $ beryl-manager:

** (beryl-manager:4864): WARNING **: Beryl caught deadly signal 11

All my title bars disappear and I have to reboot. Also, if I type $beryl-xgl I get:

$ beryl-xgl
XGL Present
Segmentation fault (core dumped)

I tried uninstalling and reinstalling everything, no luck.  Any help would be appreciated.

Thanks!

---

### Post by Isntitknoying on 2006-12-10
same exact issue, same exact timeframe. Thinking about going back to 0.1.1 and seeing if that makes a difference.

---

### Post by Chenzo on 2006-12-10
How do you force installing an old version? I miss my desk cube....

---

### Post by Isntitknoying on 2006-12-10
here's what I did to get this back to a working state again. Understand that this presumes a number of things. I have the amd64 architecture, and am using the fglrx driver on an ati x1300 pro. 

That said, my solution was to enter a normal gnome session, sudo apt-get --purge remove xserver-xgl, then apt-get autoremove the associate packages. 
Then I also purged the beryl package, emerald package, and emerald-themes package, and autoremoved all associated packages. I then modified my sources to only use the 
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy main-edgy-amd64 
source, which has the 0.1.1 packages, but apparently doesn't yet have the busted 0.1.2 packages. I then reinstalled xserver-xgl, beryl, and emerald-themes, and presto, i've got my cube and effects back. 

Still bitter that I can't get burn yet, but it's got to be something stupid that will fix it. 

Hopefully that will help someone out. 

John

---

### Post by Chenzo on 2006-12-10
Worked perfect for me!
Can't thank you enough. I had just fallen in love with Beryl when it stopped working.

Right now 0.1.1 is OK for me, but if/when I get 0.1.2 (or later) working I'll post the fix.

Vince

---

### Post by Isntitknoying on 2006-12-10
It may be possible for us to build from the svn, or the release from yesterday may fix this when it gets made into packages. I don't know if I'm in the mood to mess up my install again.

---

### Post by Chenzo on 2006-12-10
I can't help but try. Whenever 0.1.3 hits the repositories (I just checked and I'm still getting 0.1.2) I'm going to install as long as 0.1.1 is still available for me to fall back on.  I'll let you know if it works.

---

### Post by akshaymodi on 2006-12-11
I got beryl 0.1.3 and I still have the same problems. I am extremely new to linux and this is quite frustrating...](*,) ](*,) ](*,)

---

### Post by Isntitknoying on 2006-12-11
Tried installing 0.1.3 this morning, different error, same result. Beryl-XGL crashed or startup, when run from terminal I get an error. (Can't remember what it was off the top of my head, will post it when I get back home). 
It almost seems like there's a package that's not updating automatically when beryl updates. May have to try installing each package.

---

### Post by Rodneyck on 2006-12-11
If you added the .deb, then try installing through Synaptic or reinstalling through there.  Just a suggestion...

---

### Post by Chenzo on 2006-12-11
Same here... installed 0.1.3 and got the same error (deadly signal 11). Went back to 0.1.1 and it worked.

EDIT: is everyone here running 64 bit? I think we're all running XGL, so I'd guess we're all running fglrx as well? trying to find similarities...

---

### Post by Isntitknoying on 2006-12-11
64 Bit, XGL, fglrx here. ATI X1300 Pro AGP.

---

### Post by Isntitknoying on 2006-12-11
Alrighty, I've tried a few different things, but it all boils down to the same old errors. So with no further ado, here's everything I could think of to post. I'm using edgy amd64, fglrx, XGL, beryl. Beryl 0.1.1 works perfectly, 0.1.2 and 0.1.3 produce the following:

```
$ beryl-xgl
desktop:~$ beryl-xgl
XGL Present
Segmentation fault (core dumped)
```

```
desktop:~$ beryl
XGL Present
bberyl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
```

```
desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

```
desktop:~$ glxinfo |grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1300 Series Generic
```

```
desktop:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support please upgrade to Xorg 6.9 or later and use Option "TexturedVideo".

```

```
desktop:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) Error loading keymap /var/lib/xkb/server-0.xkm

```

For me the error starts right when the splash screen should be coming up, which is where the segmentation fault comes into play. No amount of killing/restarting/etc of beryl-manager and beryl-xgl produce any other results. 

Any light that you could shed on this would be great, there are a few of us out here that had everything broken by the upgrade from 0.1.1.

---

### Post by jooaakim on 2006-12-12
I get the same problems trying to run 0.1.3. Went straight from 0.1.1 to 0.1.3.

The strange thing is that it did work, briefly, before rebooting and the x-server not working for some weird reason. Reinstalled the nvidia-packages nd it worked, but not beryl.

It does work if i run beryl in a term tho, but the screen is all white.

---

### Post by Isntitknoying on 2006-12-12
Looks like we aren't the only ones. 

[http://bugs.beryl-project.org/ticket/62](http://bugs.beryl-project.org/ticket/62)

---

### Post by Chenzo on 2006-12-12
I'm running ATI X800 with fglrx, edgy 64.  I just tried beryl a 3rd time. so far, 0.1.2 failed, 0.1.3 failed, and svn snapshot failed. I also tried some other xorg.conf settings from another 64 bit install howto.  I get all of the exact same errors as isntitknoying, nothing I've tried makes a difference.  has anyone tried with aiglx and radeon drivers?

---

### Post by Progressive on 2006-12-13
Same problem, running Kubuntu edgy 64-bit, xgl , beryl 1.3, fglrx 8.31.5, ATI X1800

I didnt use any special 64bit how-tos, but it seems I have the correct amd64 packages for all the relevant programs.

xgl loads, but it is laggy

---

### Post by b0le on 2006-12-20
I have same problem. Ubuntu Edgy 64bit, xl, beryl 1.3, latest ati drivers (fglrx), ATI x800

 XGL works really good (the screensavers run normally now - they didn't before I installed it (they were real laggy)). Beryl loads up (I can see the crystal) - however, it is not using the Beryl desktop manager (when I change it to this the menus disappear and I have to restart)

---

### Post by b0le on 2006-12-22
I have exactly the same error message as Isntitknoying (the first 2 at least)

---

### Post by lupine_nickt on 2006-12-22
Hi,

Can I ask some of you to run the following command in terminal, and paste the output here for me? Along with your architecture (amd64 or i386) and graphics card driver (nvidia, ati/radeon, fglrx)?

```

apt-cache policy xserver-xgl

```

I believe I might have a fix; just need some suspicions confirming :p

(Right now, the official beryl repository contains a patched - compared to the ubuntu repo - version of xserver-xgl - but only for i386. I'm building an amd64 version, but I don't know for certain if this is the issue or not... not having an ATi card to test it out on...)

If a brave people wants to try re-updating using the "deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main" repo, they'll hopefully see an update to 0.1.3 for beryl, and an update to 0ubuntu2.1 for xserver-xgl (sorry about the naming scheme - I inherited this package from the previous maintainer)

No guarantees, though... :p

xF,

...Nick

---

### Post by b0le on 2006-12-22
```
xserver-xgl:
  Installed: 7.0.0.git.20060725-0ubuntu2
  Candidate: 7.0.0.git.20060725-0ubuntu2
  Version table:
 *** 7.0.0.git.20060725-0ubuntu2 0
        500 http://au.archive.ubuntu.com edgy/universe Packages
        100 /var/lib/dpkg/status

```

AMD Athalon64 3200+ and ATi Radeon X800 GTO (according to fglrxinfo - I'm not sure about the GTO part though) and fglrx drivers, running Edgy 64-bit.

---

### Post by lupine_nickt on 2006-12-22
Thought so. That's the unpatched version.

Can you try the version in the beryl ubutu repo, see if that gives you any more joy? It's the same code all those smug i386-ers have been running, so should be safe... 

Thanks :)

xF,

...Nick

---

### Post by b0le on 2006-12-22
I updated the xserver-xgl and now get:
```

$ apt-cache policy xserver-xgl
xserver-xgl:
  Installed: 7.0.0.git.20060725-0ubuntu2.1
  Candidate: 7.0.0.git.20060725-0ubuntu2.1
  Version table:
 *** 7.0.0.git.20060725-0ubuntu2.1 0
        100 /var/lib/dpkg/status
     7.0.0.git.20060725-0ubuntu2 0
        500 http://au.archive.ubuntu.com edgy/universe Packages

```However, beryl still doesn't work (get the same error):
```
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

```

And fglrxinfo gives;
```

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

EDIT: I couldn't find any update for Beryl though: 
$ beryl --version
beryl-core 0.1.3

---

### Post by kesman on 2006-12-23
Exactly same problems here. I have the repo version of fglrx installed, 8.28.8 and 64-bit edgy+Xgl from ubuntu.beryl-project.org -repo.. I'm using xfce4 as my desktop.

Has anyone tried with a newer fglrx?

---

### Post by noelferreira on 2006-12-23
i did,  same problem with 8.32.5 version of drivers. And i was unable to downgrading to my previous version of beryl. Maybe we have to wait for next version. It should work fine then.

noel ferreira

---

### Post by b0le on 2006-12-25
```

$glxinfo
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: [COLOR="Red"]1.2 (2.0.6011 (8.28.8))[/COLOR]

```

```

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: [COLOR="Red"]2.0.6011 (8.28.8)[/COLOR]

```

This is in a XGL session, and I was wondering why glxinfo has the 1.2 infront of OpenGL version (whereas fglrxinfo doesn't)

Here is the rest of glxinfo:
```

$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
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
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 1.2 (2.0.6011 (8.28.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  1 0 Ncon

```

---

### Post by energiya on 2006-12-25
XUbuntu 6.10, beryl-core 0.1.3
beryl-manager command -->
> WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

](*,)

---

### Post by rigdzinthar on 2006-12-25
yea I just tried the 0.1.4

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

---

### Post by b0le on 2006-12-25
[http://www.ubuntuforums.org/showthread.php?t=131267&page=20#post745383](http://www.ubuntuforums.org/showthread.php?t=131267&page=20#post745383)
[http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing](http://gentoo-wiki.com/HOWTO_XGL/Troubleshooting#GLX_EXT_texture_from_pixmap_is_missing)

These two pages say that the GLX_EXT_texture_from_pixmap_is_missing error is from "something" wrong with LibGL.so (and links to it)

I tried changing it, but I think I did it wrong - I will keep trying (hopefully I will eventually get it right - if that is what is causing the problem)

Now with fglrxinfo (and glxinfo) I get MESA instead of ATi as the OpenGL vendor (?) - Beryl loads but crashes after the splash screen, giving the error: GL_ARB_fragment_program is missing. Also, my computer now runs really laggily (trying to scroll down in Firefox is really jerky)

Hopefully someone with a bit more knowledge will look at this (and be able to fix it :))

Joel

I attached a diagram of all the different libGL.so's and the links between em

---

### Post by compwiz18 on 2006-12-27
It works!  I had the same error you all do - deadly signal 11, no screens found, etc.

I compiled it from scratch (fglrx, amd64, xgl)

I attach debs.  Remove beryl-core before you install anything else - if you already have it installed.

debs are too big (4.6MB) to attach, so I'll give you a link: [http://linux.punkforjesus.com/beryl/beryl-0.1.4.tar.gz](http://linux.punkforjesus.com/beryl/beryl-0.1.4.tar.gz)

to install, extract to their own directory and run **sudo dpkg -i *.deb** and you'll have Beryl.

have fun with Beryl 0.1.4!

---

### Post by kesman on 2006-12-27
compwiz18 , I tried your debs and they worked quite well, the only problem was with beryl-dev package which I couldn't install for some reason. Then after installing your packages, I got some errors of dependencies. After correcting them by apt-get install -f, Beryl no longer worked. It updated the 0.1.4 -version from ubuntu.beryl-project -repo.. Has anyone had any luck with that version?

---

### Post by wildekek on 2006-12-27
Great!

Works, except for beryl-dev. 
Also, beryl-settings doesn't start:
```
$ beryl-settings 
beryl-settings: symbol lookup error: beryl-settings: undefined symbol: beryl_settings_set_codeset

```

---

### Post by compwiz18 on 2006-12-27
Weird, beryl-settings works on mine...

edit: oops, maybe because I uploaded a tar.gz that was missing one of the debs...?

---

### Post by Isntitknoying on 2006-12-28
My fix was to build it from scratch from the svn. I'm currently at 0.1.3, but am planning to move up to 0.1.4 in the next day or two. It's a pain in the tail, but it works.

---

### Post by compwiz18 on 2006-12-28
> **Isntitknoying said:**
> My fix was to build it from scratch from the svn. I'm currently at 0.1.3, but am planning to move up to 0.1.4 in the next day or two. It's a pain in the tail, but it works.
You could download my .debs from the post above - they are built from the 0.1.4 SVN - save you the trouble :D

---

### Post by DarkWulf on 2006-12-28
Hey thanks! works for me (AMD64, Radeon 9800).

Only problem is I can't change my emerald theme for some reason? I'm hoping I'm just being stupid :)

---

### Post by compwiz18 on 2006-12-28
You can, but it doesn't work as expected, I think it is a bug.  To change the theme, either (a) log out, and back in, or (b), open a terminal, and run **emerald --replace** to start the new theme.

---

### Post by kesman on 2006-12-29
Compwiz18

Could it be possible for you to post a mini-howto of compiling/creating my own beryl deb-files?

---

### Post by compwiz18 on 2006-12-29
Yeah - there is a tutorial here somewhere but it had a few problems - I managed to get them sorted out.  I'll see if I can find the link again, and you can give it a shot: [http://ubuntuforums.org/showthread.php?t=281613](http://ubuntuforums.org/showthread.php?t=281613) is what I did - if you give me a second, I'll make one for amd64 and ati, I need to fix my mouse first :D

---

### Post by kesman on 2006-12-29
I tried that too, and it worked perfectly. For some reason apt still claims that the beryl-project -repo has a newer version of every part of beryl, and the version of emerald in the latest svn says it's 0.1.3 instead of 0.1.4, but I read somewhere that its just some mistake with the developers, and the version is actually 0.1.4 or something like that.

---

### Post by compwiz18 on 2006-12-29
yeah, I just removed the beryl repos from my repo list, so I didn't have to screw around with that.

---

### Post by kesman on 2006-12-30
Same here. Maybe add them again when they release 0.1.5 or newer version.

---

### Post by kcallis on 2007-01-03
> **compwiz18 said:**
> You could download my .debs from the post above - they are built from the 0.1.4 SVN - save you the trouble :D
Ok, reloaded the above files, and there has been some changes, but something is still not working correctly:

kcc ~ $ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

Also when I do glxgears -printfps I am getting

2882 frames in 5.1 seconds = 563.356 FPS
3240 frames in 5.1 seconds = 637.073 FPS
3240 frames in 5.1 seconds = 637.281 FPS

and processor usages jump up to 100%

I know that I am putting a little stress on my DV8000, but I am sure that it will get working correctly. After I installed the debs listed above, I immediately got a update notice. Should I remove the repo from sources.list or go ahead and upgrade?

EDIT: Removed repo based upon an earlier posting...

kcc ~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data
  beryl-settings emerald emerald-themes libberylsettings-dev libberylsettings0
  libemeraldengine-dev libemeraldengine0
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 132kB/4603kB of archives.
After unpacking 1729kB disk space will be freed.

---

### Post by kcallis on 2007-01-03
For a few minutes I was actually running beryl (or so it would seem)... Now that I have rebooted, I am back to metacity and can't get the beryl window manager to start...

---

### Post by crazedgremlin on 2007-01-06
Compwiz, you're AWESOME!!!  It worked perfectly for me albeit a little laggy because I'm using onboard graphics.

Thankyou thankyou thankyoou

---

### Post by spider5 on 2007-01-07
hi, compwiz18, 
It still freezes after I login in xgl-session.

when I try to invoke beryl, It echoes:
% beryl-xgl
XGL Present
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

so what's the problem anyway?

ATI X1300 Mobile , Merom T5600

---

### Post by compwiz18 on 2007-01-07
> **spider5 said:**
> hi, compwiz18, 
It still freezes after I login in xgl-session.

when I try to invoke beryl, It echoes:
% beryl-xgl
XGL Present
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

so what's the problem anyway?

ATI X1300 Mobile , Merom T5600
Try removing all packages starting with beryl and then reboot.  Now remove the beryl repositories from your repo list, and install all the debs in the package.  Reboot again.  Hopefully it will work this time...

---

### Post by spider5 on 2007-01-10
HI,compiz18.Thank you for your response.

That's not the key. 
I run fglrxinfo and find the driver fall back to mesa. maybe some updates or linux-generic change something. ATI driver is reinstalled but effectlessive, so I had to rebuild my OS from very beginning.

Now It works perfectly. You really do a great job.

I will post your method to Ubuntu China Wiki. It can help a lot.

---

### Post by MadKAT on 2007-01-19
I'm not even running AMD64 and I'm getting the same "deadly signal" error.  I'm running on an HP notebook with P4, ATI mobility 9600, and using fglrx.  I had to revert back to 0.1.1 as mentioned near the top of this thread to get it back to working condition.

However on my desktop PC with an NVidia card and using AIGLX, the new version is working fine.

As an aside, I looked at the the bug link posted on this thread, and I noticed it was closed as "not our bug" ... what's up with that??? 8)

---

### Post by compwiz18 on 2007-01-19
That is true - it isn't a beryl bug, it is a package bug, because when I compiled myself (and made .debs), it works fine.

---

### Post by iwi on 2007-01-19
Hi all :)
I have exactly this same problem on i386. I'm using glx on ATI Radeon X1400.
Did anyone check does it (i mean that .deb package) works for i386 architecture ?
If not, maybe someone has package for i386 already ?

Regards
Marcin 'iwi' Iwinski

---

### Post by crazedgremlin on 2007-01-21
> **iwi said:**
> Hi all :)
I have exactly this same problem on i386. I'm using glx on ATI Radeon X1400.
Did anyone check does it (i mean that .deb package) works for i386 architecture ?
If not, maybe someone has package for i386 already ?

Regards
Marcin 'iwi' Iwinski

[Here]("http://www.ubuntuforums.org/showthread.php?t=281613")
this should help (it's a guide to compiling beryl from source.)

---

### Post by iwi on 2007-01-21
> **crazedgremlin said:**
> [Here]("http://www.ubuntuforums.org/showthread.php?t=281613")
this should help (it's a guide to compiling beryl from source.)

thanx
:D
 i've upgraded beryl today morning from ubuntu.beryl-project.org and everythin looks great :)
i don't know who should i thank to - but anyway - you're doing very good job :)

---

### Post by MadKAT on 2007-01-21
Yes, me too. I've got the 0.2 beta2 now, and so far, it's looking great.  To whoever fixed the package in ubuntu.beryl-project.org, Thanks!!! :D

---

### Post by illu45 on 2007-02-03
Hey guys,

I've also been having trouble after I updated Beryl (to 0.1.2, I believe). Every time I launch beryl-manager it says" WARNING **: Beryl caught deadly signal 11" and reverts back to Metacity. Also, if I run beryl-xgl I get a segmentation fault (core dumped) error. I'm running on an ATI card with a 32-bit processor. 

Thanks for any advice,
illu45

EDIT: Got it fixed by purging and re-installing Beryl from the beerorkid.com repisotory. :)

---

### Post by MadKAT on 2007-02-09
Yes, I just upgraded again, and it was broken again.  Lucky, someone at [http://ubuntuforums.org/showthread.php?t=341036&page=10](http://ubuntuforums.org/showthread.php?t=341036&page=10) posted an easy way to get back to the previous version.

Basically what worked for me is: 
sudo apt-get remove 'beryl*'

sudo apt-get install beryl=0.1.99.2~0beryl1 beryl-core=0.1.99.2~0beryl1 beryl-manager=0.1.99.2~0beryl1 beryl-plugins=0.1.99.2~0beryl1 beryl-plugins-data=0.1.99.2~0beryl1 beryl-settings=0.1.99.2~0beryl1 beryl-settings-bindings=0.1.99.2~0beryl1 emerald=0.1.99.2~0beryl1 libberyldecoration0=0.1.99.2~0beryl1 libberylsettings0=0.1.99.2~0beryl1 libemeraldengine0=0.1.99.2~0beryl1 emerald-themes=0.1.99.2~0beryl1 -V

---

### Post by shareMenaPeace on 2007-02-09
> **Chenzo said:**
> Worked perfect for me!
Can't thank you enough. I had just fallen in love with Beryl when it stopped working.

Right now 0.1.1 is OK for me, but if/when I get 0.1.2 (or later) working I'll post the fix.

Vince

Hehe, since i use beryl i got so addicted a desktop without xgl/beryl is for me like a "naked Desktop" :)

Cheers

---

### Post by shareMenaPeace on 2007-02-09
For me this worked aswell
[http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl+howto](http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl+howto)

---

### Post by linex on 2007-02-14
there are so many ways listed in the thread

here's my prob
> beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0

which guide should i follow to fix the problem?

---

### Post by Tonren on 2007-02-23
I have the exact same problem as linex.  I have an ATI Radeon Xpress 200M, and I'm trying to run Beryl with XGL on fglrx (the 200M is apparently not well-supported by the open-source drivers, and fglrx doesn't work with AIGLX, so I'm stuck with XGL).

I'm using [this guide](http://www.ubuntuforums.org/showthread.php?t=281613) to install Beryl from source since I've gotten the impression that this is a package problem and not a Beryl problem from some other discussions out there.  I wonder if I should build XGL from source, too... anyway, I'm installing 0.1.99.2 because 0.1.9999.2 has two bugs (one of them a whitescreen bug) that makes it unusable for me.  I'll post more once I've finished (attempting) to install from source.

Oh, it's worth noting that I'm running 32bit Kubuntu.  I can't use compwiz's debs because they're 64bit.  I hope the "build from source" howto I linked above works for KDE as well as it does for Gnome, but I may have already run into complications...

**Edit (10:39 AM)**: In the howto build from source I posted, it instructs you to do this:

```
svn co svn://svn.beryl-project.org/beryl/tags/release-0.1.4/
```

I'm not sure what the story here is, but if I want 0.1.99.2, I'll need to do 

```
svn co svn://svn.beryl-project.org/beryl/branches/beryl-0.1.99.2/
```

I'm not sure what the difference is between the 0.1.4 **release** and the 0.1.99.2 **branch**.. stability, maybe?  But anyway, the only problem I was having with the repo package of 0.1.99.2 was the apparent "package problem" repeated by linex above, so I'm going to give the 0.1.99.2 branch a shot anyway.  Hopefully it isn't a mistake.  More later...

**Edit (12 Noon)**: Okay, I had to jerry-rig some things.  Everything built successfully, but beryl-settings, and thus beryl, wouldn't configure properly because beryl-settings-bindings wasn't installed.  I tried installing it from source by navigating to the SVN subdirectory, but it didn't work.  I cheated and did sudo aptitude install beryl-settings-bindings=0.1.99.2~0beryl1.  I hope this wasn't the problem area in the first place!  Anyway, I'm about to get into an XGL session and see if Beryl works now.  My fingers are crossed...!

**Edit (2:25 PM)**: It sort of works.  When I log into an XGL session and run "beryl-manager", the emerald appears and I get wiggly windows and a cube.  However, XGL seems really unstable - running Firefox at any time, or running Konsole too soon after KDE starts, causes a total freakout and everything freezes, forcing me to do a hard reset.

Also, "beryl-settings" doesn't exist.  I'm assuming this is related to the problem I had setting up beryl-settings because of beryl-settings-bindings, but I can't figure out how to successfully build beryl-settings-bindings from source.  So, Beryl is, for me, at this point, unusable.  I'll have to do some research and see if building XGL from source will fix the spontaneous freeze-panic-crashes, and maybe someone can tell me what to do about beryl-settings.

---

