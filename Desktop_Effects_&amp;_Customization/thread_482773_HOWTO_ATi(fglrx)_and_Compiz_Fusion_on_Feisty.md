---
title: "HOWTO: ATi(fglrx) and Compiz Fusion on Feisty"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by jtraub on 2007-06-24
These are the steps I used to get it working on Ubuntu Feisty. I assume that you have fresh system install with proprietary drivers enabled. 

Update your system
```
sudo aptitude update
sudo aptitude upgrade
```

Install XGL
```
sudo aptitude install xserver-xgl
```

Add an Xgl login session
```

sudo gedit /usr/local/bin/startxgl.sh
```
Put following code into file
```

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
exec gnome-session
```

To create the login entry, create a new file /etc/X11/sessions/xgl.desktop
```

sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop
```
Make it looks like
```

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Remove Compiz and Desktop Effects
```

sudo aptitude remove compiz-core desktop-effects
```

It will ask to remove ubuntu-desktop too. Don't worry, because it is a metapackage and we will bring ubuntu-desktop back in a few minutes.

Add Gompiz-git repository to your /etc/apt/sources.list
```

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Add keys
```

KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
```

Update your system
```

sudo aptitude update
```

Install Compiz
```

sudo aptitude install compiz
```

Install Compiz Config
```

sudo aptitude install compizconfig-settings-manager
sudo aptitude install libcompizconfig-backend-gconf
```

Install Compiz pugins
```

sudo aptitude install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unsupported
```

Bring back ubuntu-desktop
```

sudo aptitude install ubuntu-desktop

```

Now you can log off and log into XGL. 

Start Compiz
```
compiz --replace
```

_**Troubleshooting**_
_**Problem**_
**Effects aren't visible**
if compiz --replace prints to terminal
```

/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

```
**_Solution_**
Upgrade from Synaptic your libdecoration to version 0.5.

---

### Post by Bo0ddha on 2007-06-26
I'm an idiot ignore....

---

### Post by AriciU on 2007-06-26
> **jtraub said:**
> 

_**Troubleshooting**_
**Effects aren't visible**
if compiz --replace prints to terminal
```

/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

```

Upgrade from Synaptic your libdecoration to version 0.5.

Thanks. This fixed my problem with compiz not loading at all. Using nvidia not ATI.

---

### Post by lundish on 2007-06-26
what if i get:

slawek@113:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
slawek@113:~$

---

### Post by jtraub on 2007-06-26
> **lundish said:**
> what if i get:

slawek@113:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
slawek@113:~$

Have you installed XGL? Are you logged in XGL session?
This error means that you try to run compiz in X.Org sesseion, not XGL.

---

### Post by lundish on 2007-06-27
> **jtraub said:**
> Have you installed XGL? Are you logged in XGL session?
This error means that you try to run compiz in X.Org sesseion, not XGL.


I did everything as fallowed.

---

### Post by shannon.cummins on 2007-06-27
I did everything as stated as well.  I have an ATI Radeon 9600 mobility, and when I start the XGL session, and log in the screen is unviewable.  I can see something but it is distorted so bad that nothing can be read almost like the screen isnt synced, it has horizontal lines all up and sown the screen.  Any ideas as to the problem?

---

### Post by shannon.cummins on 2007-06-27
Here is my glxinfo command output

```
scummins@scummins-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

and my fglrxinfo output

```
scummins@scummins-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

---

### Post by applefreakpeeps on 2007-06-28
That just means that u dont have dri with fglrx as yet
in your xorg.conf see taht fglrx is selected and not radeon/vesa

Add these to the end of your xorg.conf file

Section Extensions
Option "Composite" "Disable"
EndSection

Press Ctrl+Alt+Backspace to restart X-server and now try. And ya.. wen u start XGL u will lose DRI. That is normal. U shud get DRI using Generic Radeon Renderer in x-server (Normal not XGL) when you type fglrxinfo, if the driver is installed properly.

---

### Post by Ravanous on 2007-06-29
I followed this as well as I could (I am running Kubuntu 7.04)

I get the following:
```
compiz --replace
/usr/bin/compiz.real: No composite extension
/usr/bin/compiz: line 47: metacity: command not found
```

fglrxinfo output:
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6474 (8.38.6)
```

---

### Post by kpolice on 2007-06-29
Did you installed XGL? Are you login into your XGL session, in your login screen (GDM) you have to select your XGL session before you login.

BTW This is for GNOME + GDM, not for KDE.

---

### Post by NightKast on 2007-06-30
When I put this in the terminal:

sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop

I get this error:
[http://img.photobucket.com/albums/v56/navyseals10/Screenshot-dvudvu-desktop.png](http://img.photobucket.com/albums/v56/navyseals10/Screenshot-dvudvu-desktop.png)

---

### Post by NightKast on 2007-06-30
Is the xgl files suppose to go on the desktop? The problem is I have no permissions to run it or copy it. How do I fix it?

---

### Post by rafucho on 2007-07-01
I followed the steps, but strangely the login window tells me, that 

"startxgl.sh can't be found"

I tried with another name say startx.sh, and it didn't work. What could I have done wrong?

Thanks in advance

---

### Post by kpolice on 2007-07-01
You didn't save the file in the proper directory.

---

### Post by biochip2k on 2007-07-01
Here are a few more tips to complement this Excellent How-To.

Probably mostly users who wants to try out compiz fusion probably already have beryl installed, wondering how to upgrade in the safe way if you installed beryl following the instructions of another How-to: very easy!.

you need to be in a gnome session (without XGL & Beryl) and write the following in terminal to uninstall beryl packages.
```
sudo apt-get remove beryl*
```
and confirm you want to remove it, then just follow this [5 min. how-to]("http://ubuntuforums.org/showthread.php?t=482773") of this thread from the step "*Remove Compiz and Desktop Effects*".

Also you may like to have the following code in **/usr/local/bin/startxgl.sh** to have the shutdown button instead of just the logout.
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

And if you would like to start compiz every time you log in :) then when you are log in in your XGL Session (now with Compiz), you have to go through SYSTEM / PREFERENCES / SESSIONS > *Startup Programs > New* and write:
```

Name: Compiz Fusion
Command: compiz --replace

```

have a happy Desktop!.

---

### Post by Alfafa on 2007-07-03
I had the problem with the texture_from_pixmap support also

I have fixed it by reinstalling some packages in the right order:

sudo apt-get --reinstall install libgl1-mesa-glx

sudo apt-get --reinstall install xorg-driver-fglrx

Hope this helps someone :-)

---

### Post by udanek on 2007-07-03
Many thanks, works without problems on my notebook (Asus with Ati Mobility Radeon X1400).

---

### Post by Spudgun on 2007-07-04
> **kpolice said:**
> You didn't save the file in the proper directory.

Yes he did. However, the file needs to be made executable, which the tutorial didn't state.

---

### Post by pikul on 2007-07-06
> **Alfafa said:**
> I had the problem with the texture_from_pixmap support also

I have fixed it by reinstalling some packages in the right order:

sudo apt-get --reinstall install libgl1-mesa-glx

sudo apt-get --reinstall install xorg-driver-fglrx

Hope this helps someone :-)

Amazing guide :p I've follow all the steps and end up getting the texture_from_pixmap support also, after using this 2 commands my fglrx drivers stop working, i guess because of the reinstall install xorg-driver-fglrx command, it was giving me the vesa driver :( so all i did was install again my drivers with the ati .run file, restart and then compiz fusion started working excellent :popcorn: i have a ati radeon xpress 200M card.

Sooo it you get the texture_from_pixmap 

- sudo apt-get --reinstall install libgl1-mesa-glx
- sudo apt-get --reinstall install xorg-driver-fglrx
- Reinstall your ati drivers

That did it for me :o

---

### Post by DaveTRG on 2007-07-07
I'm also getting the same error:

Fatal: Failed test: texture_from_pixmap support

I'm not sure how to tell if I'm in XGL or not (forgive me for being a noob ;-))...  What can I try from here?

---

### Post by DaveTRG on 2007-07-08
Also, if it helps to troubleshoot the texture_from_pixmap support error, I'm using an nvidia geforce 3 ti200 card with the nvidia-glx-new package installed as my driver.  When I run glxinfo, it shows errors as follows:

```
dave@ubuntu:~$ glxinfo

name of display: :0.0

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

Error: couldn't find RGB GLX visual



   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav

 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat

----------------------------------------------------------------------

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x2b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x2c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x2d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x2e 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x2f 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x30 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x31 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x32 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x33 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x34 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x35 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x36 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x37 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x38 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x39 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x3a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x3b 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x3c 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x3d 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x3e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x3f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x40 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x41 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x42 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x43 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x44 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x45 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x46 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x47 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x48 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x49 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x4a 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x4b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x4c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x4d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x4e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x4f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x50 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x51 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x52 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x53 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x54 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x55 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x56 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x57 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0x58 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Xlib:  extension "GLX" missing on display ":0.0".

Xlib:  extension "GLX" missing on display ":0.0".

0xd2 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Segmentation fault (core dumped)


```

Here's my xorg.conf file if it helps:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

#

# This file was generated by dexconf, the Debian X Configuration tool, using

# values from the debconf database.

#

# Edit this file with caution, and see the xorg.conf(5) manual page.

# (Type "man xorg.conf" at the shell prompt.)

#

# This file is automatically updated on xserver-xorg package upgrades *only*

# if it has not been modified since the last upgrade of the xserver-xorg

# package.

#

# If you have edited this file but would like it to be automatically updated

# again, run the following command:

#   sudo dpkg-reconfigure -phigh xserver-xorg



Section "Files"

        FontPath        "/usr/share/fonts/X11/misc"

        FontPath        "/usr/share/fonts/X11/cyrillic"

        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"

        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"

        FontPath        "/usr/share/fonts/X11/Type1"

        FontPath        "/usr/share/fonts/X11/100dpi"

        FontPath        "/usr/share/fonts/X11/75dpi"

        # path to defoma fonts

        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection



Section "Module"

        Load    "i2c"

        Load    "bitmap"

        Load    "ddc"

        Load    "dri"

        Load    "extmod"

        Load    "freetype"

        Load    "glx"

        Load    "int10"

        Load    "vbe"

EndSection



Section "InputDevice"

        Identifier      "Generic Keyboard"

        Driver          "kbd"

        Option          "CoreKeyboard"

        Option          "XkbRules"      "xorg"

        Option          "XkbModel"      "pc105"

        Option          "XkbLayout"     "us"

EndSection



Section "InputDevice"

        Identifier      "Configured Mouse"

        Driver          "mouse"

        Option          "CorePointer"

        Option          "Device"                "/dev/input/mice"

        Option          "Protocol"              "ImPS/2"

        Option          "ZAxisMapping"          "4 5"

        Option          "Emulate3Buttons"       "true"

EndSection



Section "InputDevice"

        Driver          "wacom"

        Identifier      "stylus"

        Option          "Device"        "/dev/input/wacom"

        Option          "Type"          "stylus"

        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY

EndSection



Section "InputDevice"

        Driver          "wacom"

        Identifier      "eraser"

        Option          "Device"        "/dev/input/wacom"

        Option          "Type"          "eraser"

        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY

EndSection



Section "InputDevice"

        Driver          "wacom"

        Identifier      "cursor"

        Option          "Device"        "/dev/input/wacom"

        Option          "Type"          "cursor"

        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY

EndSection



Section "Device"

        Identifier      "Geforce TI200"

        Driver          "nvidia"

        BusID           "PCI:1:0:0"

        Option          "UseDisplayDevice"  "DFP"

EndSection



Section "Monitor"

        Identifier      "Generic Monitor"

        Option          "DPMS"

        HorizSync       28-51

        VertRefresh     43-60

EndSection



Section "Screen"

        Identifier      "Default Screen"

        Device          "Geforce TI200"

        Monitor         "Generic Monitor"

        DefaultDepth    24

        SubSection "Display"

                Depth           1

                Modes           "1024x768" "800x600" "640x480"

        EndSubSection

        SubSection "Display"

                Depth           4

                Modes           "1024x768" "800x600" "640x480"

        EndSubSection

        SubSection "Display"

                Depth           8

                Modes           "1024x768" "800x600" "640x480"

        EndSubSection

        SubSection "Display"

                Depth           15

                Modes           "1024x768" "800x600" "640x480"

        EndSubSection

        SubSection "Display"

                Depth           16

                Modes           "1024x768" "800x600" "640x480"

        EndSubSection

        SubSection "Display"

                Depth           24

                Modes           "1024x768" "800x600" "640x480"

        EndSubSection

EndSection



Section "ServerLayout"

        Identifier      "Default Layout"

        Screen          "Default Screen"

        InputDevice     "Generic Keyboard"

        InputDevice     "Configured Mouse"

        InputDevice     "stylus"        "SendCoreEvents"

        InputDevice     "cursor"        "SendCoreEvents"

        InputDevice     "eraser"        "SendCoreEvents"

EndSection



Section "DRI"

        Mode    0666

EndSection


```

Any help is much appreciated...

---

### Post by Brokenlynx on 2007-07-08
My problem with this setup is after the installation of the propietary drivers and seeing DRI enabled from a failsafe terminal session I cannot start any Xserver, basically once DRI is enabled and from running 'glxinfo | grep rendering' or 'fglrxinfo' and getting the correct output I am unable to get to a desktop from the login screen. I see either just a blank tan coloured screen when starting xorg or a black and white one whn trying xgl.

I am using a laptop with Mobility Radeon M10.

Please any help with this would be appreciated.

---

### Post by firmwire on 2007-07-08
> **Murador said:**
> Same thing here :(
I installed compiz fusion yesterday, worked great.

Today I got the updates, but the windows borders have disappeared. Launching Beryl instead of compiz doesn't work either.
And I got the same "ccp plugin not working" as you

I'm running feisty amd64 / nVidia graphics


Has anyone that had received the error above, fixed their issue?
I have an ATI x1600, and that same error occured. Lost all windows border and cube.
I tried formatting and reinstalling again last night and doing all the "fixes" that I could find, but nothing worked. I did see some new "fixes" in the forums this morning that I haven't tried. Hopefully those will work.
I then even tried reinstalling and getting Beryl to work last night, using both methods; fxgl and the open source driver, but nothing worked. 

Since Compiz Fusion is the way to go, I really would like to get it working again.

---

### Post by firmwire on 2007-07-08
Something I found this morning.

> **blackdevil said:**
> Talked to Trevinho, and the problem is that the deb isnt updated in  the script. He is apparently working on it now and the fix should be out soon hopefully.

---

### Post by silent1643 on 2007-07-08
my errors
on xgl session load
```
justin@justin-desktop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
justin@justin-desktop:~$ 

```

also getting
```

"startxgl.sh can't be found" 
```

---

### Post by cyu6722 on 2007-07-08
also gettingX session: /usr/local/bin/startxgl.sh not found when i tried to log in through XGL. I checked the location and it was right there.

---

### Post by LuisAugusto on 2007-07-08
You FORGOT one step, you didn't give the /usr/local/bin/startxgl.sh executable permission! 

This should fix all the problems whit file not found:

```
 sudo chmod a+x /usr/local/bin/startxgl.sh
```

---

### Post by Leira on 2007-07-09
> **jtraub said:**
> 
Now you can log off and log into XGL. 

Start Compiz
```
compiz --replace
```



thanks for this how-to, b4 i try Compiz-fusion, i have a question, can i still use the Desktop Effects to enable and disable Compiz then? and if not, how can i disable compiz on the fly?

---

### Post by Goda on 2007-07-09
When I go into an XGL session the graphics go crazy. I can barely make out a window from all the choppy background and definitly cant read anything.

---

### Post by firmwire on 2007-07-09
Check your xorg.conf file. 

/etc/X11/xorg.conf 

You may have to check what driver it is looking for.

Make sure your have the correct driver loaded:

 Driver 'flgrx' , 

and that you edit the Composite line at the bottom to 0:

Section "DRI"
Mode 0666
EndSection
Section "Extensions"
Option "Composite" "0"
EndSection

---

### Post by ShAdEd_PaSt on 2007-07-09
I have all that in my xorg.conf and its still all blurry with nothing readable. any ideas?

---

### Post by firmwire on 2007-07-09
Have you checked your monitor's sync rates?
Horizontal and Vertical?

---

### Post by Drone4four on 2007-07-09
My decorations still don't show up after i follow the initial guide.  Here is the error message from compiz --replace: ```
drone4four@kubuntu:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugin group (group)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin splash (splash)
Adding plugin animation (animation)
Adding plugin snow (snow)
Adding plugin dbus (dbus)
Adding plugin opacify (opacify)
Adding plugin fakeargb (fakeargb)
Adding plugin gotovp (gotovp)
Adding plugin clone (clone)
Adding plugin place (place)
Adding plugin reflex (reflex)
Adding plugin annotate (annotate)
Adding plugin scaleaddon (scaleaddon)
Adding plugin cube (cube)
Adding plugin png (png)
Adding plugin firepaint (firepaint)
Adding plugin minimize (minimize)
Adding plugin put (put)
Adding plugin glib (glib)
Adding plugin move (move)
Adding plugin ring (ring)
Adding plugin screenshot (screenshot)
Adding plugin resize (resize)
Adding plugin wall (wall)
Adding plugin scalefilter (scalefilter)
Adding plugin text (text)
Adding plugin extrawm (extrawm)
Adding plugin inotify (inotify)
Adding plugin switcher (switcher)
Adding plugin wobbly (wobbly)
Adding plugin mblur (mblur)
Adding plugin blur (blur)
Adding plugin zoom (zoom)
Adding plugin fade (fade)
Adding plugin trailfocus (trailfocus)
Adding plugin neg (neg)
Adding plugin thumbnail (thumbnail)
Adding plugin expo (expo)
Adding plugin addhelper (addhelper)
Adding core settings (General Options)
Adding plugin tile (tile)
Adding plugin showdesktop (showdesktop)
Adding plugin rotate (rotate)
Adding plugin vpswitch (vpswitch)
Adding plugin fadedesktop (fadedesktop)
Adding plugin water (water)
Adding plugin crashhandler (crashhandler)
Adding plugin winrules (winrules)
Adding plugin video (video)
Adding plugin plane (plane)
Adding plugin resizeinfo (resizeinfo)
Adding plugin snap (snap)
Adding plugin scale (scale)
Adding plugin imgjpeg (imgjpeg)
Adding plugin decoration (decoration)
Adding plugin cubereflex (cubereflex)
Adding plugin regex (regex)
Adding plugin bench (bench)
Initializing core options...done
Initializing place options...done
Initializing minimize options...done
Initializing move options...done
Initializing resize options...done
Initializing zoom options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing decoration options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)
Initializing rotate options...done
Initializing scale options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Setting Update "cursor_theme"
Setting Update "fullscreen_visual_bell"
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

---

### Post by pikul on 2007-07-09
> **Goda said:**
> When I go into an XGL session the graphics go crazy. I can barely make out a window from all the choppy background and definitly cant read anything.

That happend to me a few times, just restart or press ctrl-alt-backspace to restart xserver and login again until it works, after like 10 times login in to my xgl session stop doing it :lolflag:

---

### Post by faraaz on 2007-07-10
Hi, your guide worked like a charm for me! Only trouble is, I'm not able to change themes in Emerald for some reason.

Can someone tell me how I do this?? Clicking on a different theme doesn't help...

---

### Post by OneSeventeen on 2007-07-10
> **pikul said:**
> Amazing guide :p I've follow all the steps and end up getting the texture_from_pixmap support also, after using this 2 commands my fglrx drivers stop working, i guess because of the reinstall install xorg-driver-fglrx command, it was giving me the vesa driver :( so all i did was install again my drivers with the ati .run file, restart and then compiz fusion started working excellent :popcorn: i have a ati radeon xpress 200M card.

Sooo it you get the texture_from_pixmap 

- sudo apt-get --reinstall install libgl1-mesa-glx
- sudo apt-get --reinstall install xorg-driver-fglrx
- Reinstall your ati drivers

That did it for me :o

I am having the same problem (with radeon xpress 200m) but I don't know how to reinstall my ati drivers... how do I do that?

Also, what command do you use to start compiz?

---

### Post by Goda on 2007-07-10
> **firmwire said:**
> Have you checked your monitor's sync rates?
Horizontal and Vertical?

Do you know how we go about doing that, and what we want it set at?

---

### Post by ShAdEd_PaSt on 2007-07-10
> **firmwire said:**
> Have you checked your monitor's sync rates?
Horizontal and Vertical?
Nah I haven't, I'll try that.

---

### Post by DaveTRG on 2007-07-11
> **Drone4four said:**
> My decorations still don't show up after i follow the initial guide.  Here is the error message from compiz --replace: ```
drone4four@kubuntu:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugin group (group)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin splash (splash)
Adding plugin animation (animation)
Adding plugin snow (snow)
Adding plugin dbus (dbus)
Adding plugin opacify (opacify)
Adding plugin fakeargb (fakeargb)
Adding plugin gotovp (gotovp)
Adding plugin clone (clone)
Adding plugin place (place)
Adding plugin reflex (reflex)
Adding plugin annotate (annotate)
Adding plugin scaleaddon (scaleaddon)
Adding plugin cube (cube)
Adding plugin png (png)
Adding plugin firepaint (firepaint)
Adding plugin minimize (minimize)
Adding plugin put (put)
Adding plugin glib (glib)
Adding plugin move (move)
Adding plugin ring (ring)
Adding plugin screenshot (screenshot)
Adding plugin resize (resize)
Adding plugin wall (wall)
Adding plugin scalefilter (scalefilter)
Adding plugin text (text)
Adding plugin extrawm (extrawm)
Adding plugin inotify (inotify)
Adding plugin switcher (switcher)
Adding plugin wobbly (wobbly)
Adding plugin mblur (mblur)
Adding plugin blur (blur)
Adding plugin zoom (zoom)
Adding plugin fade (fade)
Adding plugin trailfocus (trailfocus)
Adding plugin neg (neg)
Adding plugin thumbnail (thumbnail)
Adding plugin expo (expo)
Adding plugin addhelper (addhelper)
Adding core settings (General Options)
Adding plugin tile (tile)
Adding plugin showdesktop (showdesktop)
Adding plugin rotate (rotate)
Adding plugin vpswitch (vpswitch)
Adding plugin fadedesktop (fadedesktop)
Adding plugin water (water)
Adding plugin crashhandler (crashhandler)
Adding plugin winrules (winrules)
Adding plugin video (video)
Adding plugin plane (plane)
Adding plugin resizeinfo (resizeinfo)
Adding plugin snap (snap)
Adding plugin scale (scale)
Adding plugin imgjpeg (imgjpeg)
Adding plugin decoration (decoration)
Adding plugin cubereflex (cubereflex)
Adding plugin regex (regex)
Adding plugin bench (bench)
Initializing core options...done
Initializing place options...done
Initializing minimize options...done
Initializing move options...done
Initializing resize options...done
Initializing zoom options...done
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing decoration options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:588): Wnck-WARNING **: Unhandled action type (nil)
Initializing rotate options...done
Initializing scale options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
Setting Update "cursor_theme"
Setting Update "fullscreen_visual_bell"
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

I had this same problem and changing my color depth fixed it. I changed the following in /etc/X11/xorg.conf

DefaultDepth 16

to

DefaultDepth 24

After this is changed you'll want to restart gdm by going to a terminal session (Ctrl + Alt + F2 for example), and typing the following:

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

In Kubuntu, use kdm in place of gdm there.

Hopefully this helps.

---

### Post by astrophoenix on 2007-07-14
in kubuntu, kdm is the graphical login prompt which starts up the X server. I simply edited /etc/kde3/kdm/kdmrc to switch from Xorg to Xgl.

This was easier and better then creating a script in /usr/local/bin and a desktop file in /etc/X11/sessions. 

there was a line in the kdmrc file which looked like this:

```
ServerCmd=/usr/bin/X -br
```

I changed it to this:

```
#ServerCmd=/usr/bin/X -br
ServerCmd=/usr/bin/Xgl -fullscreen -ac -br -accel glx:pbuffer -accel xv:pbuffer

```

and there was also this line, which I commented out (add a # at the beginning of the line):

```
ServerArgsLocal=-nolisten tcp
```

I'm sure gdm and xdm probably have a similar config file somewhere.

I also found I had to run compiz like this:

```
compiz --replace ccp
```

---

### Post by codewolf on 2007-07-15
i'm having troubles connecting to the added apt server
i added the key and i think the server is just offline
is there mirror i can use ?
```

root@cwhome:~# sudo aptitude update
Err http://download.tuxfamily.org feisty Release.gpg
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Get:1 http://nl.archive.ubuntu.com feisty Release.gpg [191B]                                         
Ign http://nl.archive.ubuntu.com feisty/main Translation-en_US                                        
Ign http://nl.archive.ubuntu.com feisty/restricted Translation-en_US                                  
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]                                   
Ign http://security.ubuntu.com feisty-security/main Translation-en_US                                 
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US                           
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US                             
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US                           
Err http://download.tuxfamily.org feisty/eyecandy Translation-en_US                                   
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)


and offcourse we get:
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err http://download.tuxfamily.org feisty/eyecandy compiz-core 1:0.5.1+git20070712~3v1ubuntu4
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err http://download.tuxfamily.org feisty/eyecandy compiz-plugins 1:0.5.1+git20070712~3v1ubuntu4
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err http://download.tuxfamily.org feisty/eyecandy compiz-gnome 1:0.5.1+git20070712~3v1ubuntu4
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err http://download.tuxfamily.org feisty/eyecandy compiz 1:0.5.1+git20070712~3v1ubuntu4
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err http://download.tuxfamily.org feisty/eyecandy compiz-fusion-plugins-main 0.0.1+git20070713~3v1ubuntu3
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err http://download.tuxfamily.org feisty/eyecandy libcompizconfig0 0.0.1+git20070711~3v1ubuntu2
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err http://download.tuxfamily.org feisty/eyecandy python-compizconfig 0.0.1+git20070711~3v1ubuntu0
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
Err http://download.tuxfamily.org feisty/eyecandy compizconfig-settings-manager 0.1.0+git20070714~3v1ubuntu1
  Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)
E: Failed to fetch http://download.tuxfamily.org/3v1deb/pool/feisty/eyecandy/compiz-core_0.5.1+git20070712~3v1ubuntu4_i386.deb: Could not connect to download.tuxfamily.org:80 (88.191.250.18). - connect (111 Connection refused)

```

**edit: i mailed the guuys of the server they restarted apache so problem solved

---

### Post by j_medic78 on 2007-07-16
I followed the instructions posted here, and Compiz worked fine, but now all of a sudden, when I log on, the screen is totally messed up. It's all scrambled, and I can't make anything out. Any advice would be greatly appreciated. Before that happened, I changed the effects in the Compiz Manager, and then I was unable to move or close my windows. I can still log on normally, but I really like the desktop effects. Bummer deal.:confused:

---

### Post by j_medic78 on 2007-07-16
BTW, I'm running Feisty on a Dell E1505 laptop with an ATI X1400 video card.

---

### Post by kyousukun on 2007-07-18
i managed to somehow make it all work but i have a problem,
the themes dont work anymore, only the titlebars have themes applied to them.
here's the screenshots:

[[IMG]http://farm2.static.flickr.com/1113/846916770_7c1843439b.jpg[/IMG]]("http://www.flickr.com/photos/7592458@N04/846916770/")
[[IMG]http://farm2.static.flickr.com/1127/846916776_272d002ec5.jpg[/IMG]]("http://www.flickr.com/photos/7592458@N04/846916776/")

and this is how the theme should look like
[[IMG]http://farm2.static.flickr.com/1209/846150989_d1634bd449.jpg[/IMG]]("http://www.flickr.com/photos/7592458@N04/846150989/")

i upgraded to ubuntu studio 7.04 from a fresh ubuntu7.04 and as you can see in the screenshots, the themes do not work well but when i login to a default session other than xgl i dont have this problem
hope someone can help me with this.

---

### Post by jimminy_kriket on 2007-07-18
ctrl-alt-backspace then log back in. Usually works for me

---

### Post by kyousukun on 2007-07-19
> **jimminy_kriket said:**
> ctrl-alt-backspace then log back in. Usually works for me

im still having the same results. :(

---

### Post by TheProphet[S] on 2007-07-22
> **kyousukun said:**
> i managed to somehow make it all work but i have a problem,
the themes do not work anymore, only the titlebars have themes applied to them.

I think it is a common problem. The solution I found is to run:

```

gnome-settings-daemon 
```

using the alt+F2 shortcut and typing it in the dialog box.

Hope this helps.

---

### Post by BioSore on 2007-07-23
Alright, I'm another user with a ATI x200m card.  I've followed the instructions for installing XGL and am currently using the fglrx driver.

However, when I log into an XGL session, a black window automatically opens up titled "Xglx".  Then, whether I leave this window open or not, when I attempt to start Compiz through "compiz --replace" I am given the same ol' error,
```

grios@grios:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
grios@grios:~$

```
I've tried the suggestions earlier, which are
```

sudo apt-get --reinstall install libgl1-mesa-glx
sudo apt-get --reinstall install xorg-driver-fglrx

```
but this doesn't seem to fix any issue.  I can't seem to find any other suggested fixes to this problem, and am out of ideas.  I haven't heard of anyone else having a window opening titled "Xglx" before, so I'm assuming that has something to do with it.  I've backtracked through the steps to see if I mis-typed something, but I can't find any mistakes on my part (yet).

---

### Post by kyousukun on 2007-07-24
> **BioSore said:**
> Alright, I'm another user with a ATI x200m card.  I've followed the instructions for installing XGL and am currently using the fglrx driver.

However, when I log into an XGL session, a black window automatically opens up titled "Xglx".  Then, whether I leave this window open or not, when I attempt to start Compiz through "compiz --replace" I am given the same ol' error,
```

grios@grios:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
grios@grios:~$

```
I've tried the suggestions earlier, which are
```

sudo apt-get --reinstall install libgl1-mesa-glx
sudo apt-get --reinstall install xorg-driver-fglrx

```
but this doesn't seem to fix any issue.  I can't seem to find any other suggested fixes to this problem, and am out of ideas.  I haven't heard of anyone else having a window opening titled "Xglx" before, so I'm assuming that has something to do with it.  I've backtracked through the steps to see if I mis-typed something, but I can't find any mistakes on my part (yet).

i havent fixed my problem yet (the problem posted above yours) coz i recently installed sabayon linux and having adsl configuration problems with it. ubuntu is still better (for me),

and i still like compiz fusion better than beryl, but there are problems with 3d cube plugin, when i turn the cube with 3d cube enabled the window doesnt bend around the corners unlike in beryl.

when i had your problem, the pixmap support thingy,
i only get that error when on opengl (or when im not logged in xgl)
i dont get that error when i disable the restricted driver (when not in xgl)

what i did was, 
first enable the ati in the restricted drivers manager, then it downloaded the latest driver
second, set up the xgl, then remove the preinstalled compiz and desktop effects
third, install compiz fusion,
lastly, reboot and choose xgl in the sessions in GDM/log in screen,
 then i dont get the the pixmaps support error thing.

im not sure if this can help...

---

### Post by kyousukun on 2007-07-24
> ```

gnome-settings-daemon 
```

using the alt+F2 shortcut and typing it in the dialog box.

Hope this helps.

yes this solves the problem:KS thank you very much:popcorn:

got another question, how do i make
gnome-settings-manager + compiz --replace to load at startup?
should i make a startup program in sesions?
i want to edit the /usr/local/bin/startxgl.sh file so that it will automatically load gnome-settings-manager, then i'll just make a desktop shortcut/launcher of compiz --replace

---

### Post by chris_c28 on 2007-07-24
I can run compiz fine, but then emerald themes don't refresh when I change it from the Emerald Theme Manager. They do refresh after I kill and restart emerald, but I remembered not having to do this.

Any ideas?

---

### Post by Jamesbowden on 2007-07-25
I followed the instructions as described

but when I try and log in I get a message tell me that "X session can not find /usr/local/bin/startxgl.sh"

I checked and its is there, I even chmod u+x'd it to see if that would help, but still no luck.

any ideas?

---

### Post by Cyberapoc on 2007-07-25
I got the same problem. On logging into XGL this happens:

X session cannot find /usr/local/bin/startxgl.sh

Something to do with changes on the server is my guess...

Help is appreciated!

Thanks

---

### Post by kyousukun on 2007-07-25
> **Jamesbowden said:**
> I followed the instructions as described

but when I try and log in I get a message tell me that "X session can not find /usr/local/bin/startxgl.sh"

I checked and its is there, I even chmod u+x'd it to see if that would help, but still no luck.

any ideas?

you should type it as
```
sudo chmod a+x /usr/local/bin/startxgl.sh
```
to make it executable

---

### Post by LazyLaPlante on 2007-07-26
hello,

im using kubuntu and when i type

compiz --replace --force-fglrx

i get this message:

Fatal: Failed test: copy texture not available

am i the only one having this problem, i found nothing by googling.

p.s.: when i type

compiz --replace

i get:

Fatal: Failed test: texture_from_pixmap support

thanks

---

### Post by kyousukun on 2007-07-26
reading this thread starting from the first post should help you figure out the problem. if you cant find a solution try mine,
if your'e on the xgl session you should have the restricted driver enabled.
```
sudo dpkg-reconfigure xserver-xorg
```
then look for the part where you'll have to select fglrx should do the trick (thats what i did)
and to also edit the config where i can have a 1280x1024 selection for the screen resolution.

---

### Post by kyousukun on 2007-07-26
i had a problem and solved it.
-when in the login screen, everything's fine.
-when i log in to session "gnome-xgl" (default), i get a messed up screen, only strips of horizontal lines of the GUI.
-no mater how many times i restart X (ctrl+alt+BACKSPACE), i still get the same problem
-but when i log in to session "gnome" i get everything ok but without the desktop effects.
Answer:
-log in to the session "gnome" and look if the restricted driver is enabled (mine got disabled and i didn't know how)
-after that, do ```
sudo dpkg-reconfigure xserver-xorg
``` and select flgrx and just select the defaults all the way through and maybe select/add some screen resolution sizes too..
-log back in to session "gnome-xgl" and youre done

by the way i followed this howto:
["How To : Compiz Fusion for ATI cards + Xgl in Feisty"]("http://ubuntuforums.org/showthread.php?t=488385")
its easier and you dont have to remove desktop effects the the compiz-core provided in feisty

---

### Post by MissDjax on 2007-07-29
> **BioSore said:**
> Alright, I'm another user with a ATI x200m card.  I've followed the instructions for installing XGL and am currently using the fglrx driver.

However, when I log into an XGL session, a black window automatically opens up titled "Xglx".  Then, whether I leave this window open or not, when I attempt to start Compiz through "compiz --replace" I am given the same ol' error,
```

grios@grios:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
grios@grios:~$

```
I've tried the suggestions earlier, which are
```

sudo apt-get --reinstall install libgl1-mesa-glx
sudo apt-get --reinstall install xorg-driver-fglrx

```
but this doesn't seem to fix any issue.  I can't seem to find any other suggested fixes to this problem, and am out of ideas.  I haven't heard of anyone else having a window opening titled "Xglx" before, so I'm assuming that has something to do with it.  I've backtracked through the steps to see if I mis-typed something, but I can't find any mistakes on my part (yet).

I have exactly the same problem. And I have this Black "Xglx" window as well.
grafic card: x800 pro

---

### Post by Shmits on 2007-07-31
help! because i did this (not exactly) almost every command i put in the terminal, and when trying to open the package manager it says "you must manually run 'dpkg --configure -a' to correct the problem." what does this mean?

---

### Post by Jamesbowden on 2007-08-02
> **Shmits said:**
> help! because i did this (not exactly) almost every command i put in the terminal, and when trying to open the package manager it says "you must manually run 'dpkg --configure -a' to correct the problem." what does this mean?

it means open up your terminal and type

```
dpkg --configure -a
```
 
that should fix it.

I'm not trying to be rude, but the out out you just pasted/typed told you what to do. and a lot of the time, ubuntu will do that.

I little suggestion for you is that if something tells you to "manually run <random command>" it means type it into a terminal and press enter :cool:

hope this helped.

---

### Post by bourger on 2007-08-02
Well, at last Compiz works on my desktop!
Just one problem.
After ```
compiz --replace
``` themes stop functioning, as described on previous pages. But when I run ```
gnome-settings-daemon
```, CPU goes mad, 100% load on both cores (C2D 4400).
Terminal at that time gives an uncessant queue of lines like this: ```
Warning:       No symbols defined for <I6B> (keycode 265)
```
Themes, though, are working at that moment. 

And besides, there is notification of beryl updates. Should I install them?
Thanks for any help.

P.S. One more question. I enabled 4 workspaces, but when I try to rotate the cube (Ctrl+Alt+Left/Right), there are oly two surfaces, like turning a sheet of paper. And it seems, it's always the same workspace - indicator on workspace applet doesn't change, just the windows on one side of "sheet" appear opened, and on the another - minimized.

---

### Post by bourger on 2007-08-03
Well, problem with a "sheet of paper" instead of cube is solved by enabling 4 workspaces not in Xgl session, but in regular Gnome.
But seemingly there is no switching between workspaces - open windows on different surfaces of the cube appear merely minimized, but they are always the same, unlike as if I'd changed the workspace by clicking on the applet.
High load of CPU still persists - with the ongoing warnings in terminal.
It's connected with keyboard applet somehow - while *gnome-settings-daemon* is running, it freezes.

---

### Post by superbungalow on 2007-08-04
I get an error when logging in with XGL, something like:

Unable to launch /usr/local/bin/startxgl.sh
X ---------------- /usr/local/bin/startxgl.sh not found
failing back to default session

something like that anyway. Any ideas?

---

### Post by superbungalow on 2007-08-04
please? also when I run compiz replace, the terminal outputs:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

Which I'm guessing is because I'm not running XGL, because it failed.

---

### Post by superbungalow on 2007-08-04
Umm, I don't know exactly what I did, I copied some code from another tutorial and rebooted, but now when I run compiz --replace, It starts up, I get all the code, like initializing this and that and wobbly windows thing, then I have no windows borders, but then the borders come back, but nothing has changed. What should I do?

---

### Post by flyboy_2003 on 2007-08-07
After logging out and logging into the XGL session, I get an error:

Unable to launch "/usr/local/bin/startxgl.sh"

"/usr/local/bin/startxgl.sh" not found

I looked, and the file is there. I tried to chmod it to 744 to make it executable, but that did not help.

???

---

### Post by couzin2000 on 2007-08-12
ok -- I've been through 5 different HOWTOs, installed countless apps, uninstalled several, tyoed so much stuff in Terminal that my fingers are now crooked - permanently.

But nothing still works. When I installed Beryl right off of Synaptics, it WORKED - not amazingly, but it worked.

Now I find out that Compiz replaces it, then compiz fusion... and now I have to upgrade. Well, my program does not work now. So far, I've done everything everyone has told me, and I get 0 results. 

Can someone please point me to the 1st step and make sure that my system is clean? thank you.

---

