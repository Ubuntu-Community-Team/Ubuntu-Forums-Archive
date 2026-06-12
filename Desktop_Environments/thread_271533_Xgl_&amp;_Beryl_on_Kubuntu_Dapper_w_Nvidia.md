---
title: "Xgl &amp; Beryl on Kubuntu Dapper w/ Nvidia"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Splittor on 2006-10-04
I started playing with Compiz last month because I was very interested in it, and thought it was simply beautiful.  However, I have switched to Beryl due to the supportive community aspect of it, it seemed more natural.  

I am by absolutely no means a Linux guru, and it is very possible someone else may have a better way to do this, or upgrades and suggestions.  Please tell me and I will look at them!   That also being said, since I am not the best with Linux, I may or may not be able to help you diagnose a problem or a crash.  I apologize if this is the case, but I also hope someone else who knows the ins and outs better could assist with that!

_Let's do this!_

First off, I must give note to the great tutorial written by DJRobbieF, for installing Xgl & Beryl on Dapper Gnome w/ Nvidia.  His guide can be found here - [http://ubuntuforums.org/showthread.php?t=268036&highlight=xgl+beryl+djrobbief](http://ubuntuforums.org/showthread.php?t=268036&highlight=xgl+beryl+djrobbief) It is immensely helpful for anyone looking to install Beryl in Gnome. 

_Preliminary Editing_

First, we need to edit your repository listing to enable the universe and multiverse repository list, so we can grab extra packages and libraries if necessary.  Let's fire up Kate in a terminal -

```
sudo kate /etc/apt/sources.list
```

To the 2 main Ubuntu repositories -

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
```

You will need add in at the end after main restricted: multiverse universe to each line.  When finished, the repository should say:

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted multiverse universe
```

You will then need to update and upgrade to grab some extraneous required libraries

```
sudo apt-get update
sudo apt-get upgrade
```

_Nvidia Driver Install and Config_

To start off, it is a good idea to install Nvidia drivers.  This can be accomplished by opening a terminal and typing:

```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

This will install the Nvidia driver.  You can then have it configure your Xorg.conf by running in the terminal:

```
sudo nvidia-xconfig
```

To make sure everything was configured right, let's check out the file and make sure.  In the terminal, type:

```
sudo kate /etc/X11/xorg.conf
```

Scroll down to the "Modules" section, and make sure that GlCore and dri modules are commented out (or do not exist, due to nvidia-xconfig).  The glx module should be enabled.  Next, scroll down to the Device section.  The Driver should say "nvidia".  Underneath it, add in: Option          "RenderAccel"  "true"

The next section is "Screen"  Ensure that the DefaultDepth is set to 24!!!  Save the file, and close it.

_Onward to Eye Candy_

To start with, if you have Compiz installed, you will need to completely remove it in order to properly install Beryl.  This can be done by:

```
sudo apt-get remove compiz compiz-gnome cgwd cgwd-themes xserver-xgl csm
```

Next, you will need to edit your /etc/apt/sources.list, so let's fire up Kate:

```
sudo kate /etc/apt/sources.list
```

To the sources.list, add in 
```
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main 
```

You will then need to grab Quinns key and allow it by:
```
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc)
sudo apt-key add quinn.key.asc
```

Now we need to update Kubuntu and then install the Beryl packages and Xgl.

```
sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes
```

Now we need to create the script to launch Xgl:
```
sudo kate /usr/bin/startxgl.sh
```

Inside the script, we must place this to run Xgl properly:
```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Start kde
exec startkde
```

Save the file and close out.  Now we should create a new desktop entry so we can select between Xgl and KDE in case of a crash.  This prevents a lot of agony of having to fix things from within command-line environment by having the KDE session still exist untouched.  Once again, let's fire up Kate and create our file:

```
sudo kate /usr/share/xsessions/xgl.desktop
```

Inside the file, add:
```
[Desktop Entry]
   Encoding=UTF-8
   Name=xgl
   Exec=/usr/bin/startxgl.sh
   GenericName[en_US]=
   Icon=
   Type=Application
```

Now, we need to make the scrips executable, so let's go ahead and do that.
```
sudo chmod 755 /usr/bin/startxgl.sh
sudo chmod 755 /usr/share/xsessions/xgl.desktop
```

Lastly, we must map out the keyboard.  We do this by creating another script:
```
sudo kate /home/yourusername/.kde/Autostart/xmodmap.sh
```

Note: replace "yourusername" with your actual username (whatever /home/???/ is.)

Inside the file, type in:

```
xmodmap /usr/share/xmodmap/xmodmap.??
xmodmap -e "keycode 22 = BackSpace"
``` 

Where ?? is your locale.  (For those of you in the US like me, the extension is .us, and so on)

Note: Selecting the wrong locale may produce undesired results and/or Beryl not functioning correctly.

Mapping keycode 22 to Backspace is important, otherwise you will find out if you accidentally Shift+Backspace, you will kill Beryl and XGL and log out.  Mapping out the Backspace key eliminates this problem.

Save the file and exit out of it.  Make it executable by:

```
sudo chmod 755 /home/yourusername/.kde/Autostart/xmodmap.sh
```

You're done editing files now!  On to trying it out!

_Conclusion_

Attention: This is VERY dirty.  Does anyone know of better way to get it working consistently in an automatic startup method?  Please let me know!

Now you need to reboot the machine (not kill X, a full reboot is required).  Upon reboot, you can select the "xgl" session from the MENU button at the login screen.  Upon login, navigate to the Kmenu, and select Run Command.  In there, type in beryl-manager  The beryl-manager icon should appear in the tray (red diamond).  Right click on beryl-manager, and go to "Select Window Manager"  Then, check the "Beryl" box instead of KWin, and in a few seconds Beryl will load and you can play with all the new eye candy!  You can change themes using Emerald, or change the settings of Beryl.

While this is dirty, I like it since it gives me a fallback.  If Xgl/Beryl crashes, then the system should automatically revert back to KWin rather than crashing to a terminal.  While it is not perfect, I find it is useful to have this backup.

Any questions, comments, or improvements, please let me know!  This is my first HowTo and I am no Linux guru.  I will do the best I can to help if I can.  Thank you, and enjoy Beryl!

---

### Post by Splittor on 2006-10-05
No one finds this useful?:(

---

### Post by jethro10 on 2006-10-05
I did.

Perhaps people just use it and dont reply......


J

---

### Post by atraylen on 2006-10-05
Hmm I followed this tutorial and whenever I start an Xgl session kde hangs at the load screen for a few minutes and then kicks me back out to the login.  And when I load up into a regular X session I run the Xgl server and I get this error?

```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
[1] 5987

Fatal server error:
no GLX visuals available

[1]+  Exit 1                  Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer

```

Any Ideas ????

Great Tut btw... I looked at many for this and this was the only one that really seemed to be geared specifically for Kubuntu users trying to install Beryl.  Thx

---

### Post by klgsx on 2006-10-05
would this HOW-TO work on:

Unbutu dapper
with ATI/Radeon 9200

and what are the advantage of Beryl over Xgl/compiz?

I am trying to boot-up my laptop to make a case of dropping up all my house M$ pcs.

thanks

---

### Post by Iarwain ben-adar on 2006-10-05
Hi,
when i try to start the xgl session, it waits aswell..

Throws me back after some 10-15sec :S


Iarwain

---

### Post by Splittor on 2006-10-05
> Great Tut btw... I looked at many for this and this was the only one that really seemed to be geared specifically for Kubuntu users trying to install Beryl. Thx

Thanks for the support atraylen.  Glad to see it was useful.

For your problem, double-check your /etc/X11/xorg.conf and make sure the "glx" module is being loaded in the "Module" section, and that the "dri" and "glcore" modules are commented out and not being loaded.

Since your issue Iarwain ben-adar seems to be kind of the same as atraylens, check your config as well.

If the nvidia-xconfig did not work, you will need to try:

```
sudo nvidia-glx-config enable
```

And then need to edit the /etc/X11/xorg.conf file manually, doing what I said as above.

This seems like a logical choice, I do not know much about Linux, but since the GLX module cannot be found, better make sure it is being loaded correctly. 

(This is why I have XGL set up as a different session...imagine this being your default and only session!  It would be really bad doing this from a command line!)

And klgsx, if you give me some time, I have a laptop with Dapper and an ATI Radeon 9000.  I can try to get it working on my laptop and give you feedback at a later time, I just do not use my laptop, but I think you will need to use AIGLX.

---

### Post by Iarwain ben-adar on 2006-10-06
Well,
after the edit, the xgl session starts :D

Without beryl :(
this is what i get when i try to start beryl
```
iarwain@iarwain-desktop:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1
iarwain@iarwain-desktop:~$

```

And also, when i type in beryl, my keyboard stops responding, except when i Ctrl-Ald-Del (never thought that i had to use that again:???: )

Btw, thanks for the clear howto, it's simple to follow =)


Iarwain

---

### Post by Splittor on 2006-10-06
Iarwain, I just tried that, and that seems to be a bug.  I got the same output and it crashed X.  

Run beryl-manager instead from the run command, or beryl-manager & from terminal (so you can close the terminal without killing Beryl).  Then you can select to use Beryl as your window manager from the icon that should appear in the tray.

I'll have to find more on this issue, I apologize.

Thank you for the encouragement on my HowTo! :)

---

### Post by Iarwain ben-adar on 2006-10-07
Hi,
thanks!
It works now :D

Just one more question, how can i use my keyboard and mouse normally?
Because now i have to hold the Ctrl key to use them properly..


Iarwain

---

### Post by dfunkydog on 2006-10-07
I got this message
> dfunkydog@416bux:~$ sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes
Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
libglitz-glx1 is already the newest version.
E: Couldn't find package beryl

I'm stuck, can anyone help?

---

### Post by pony-tail on 2006-10-07
I have it working on my PIII test machine -about 10 minutes ago.
Is there any way to get it to load without running the "beryl-manager" command . Just have it load on the XGL session or similar ?

---

### Post by Splittor on 2006-10-07
Iarwain that's kind of unusual...I have absolutely no idea on your problem man...haha.  Sorry, I'll look and see what I can find.

dfunkydog...did you add the repositories, update, upgrade, and then try finding those packages?  You need to add the repository that contains the Beryl packages, since they are not in the standard repository listing.  Read up towards the top of the tutorial.

And pony-tail, not at the moment it seems (not in a stable manner, at least).  I acknowledged it is kind of a dirty method, but I do not know of any other way really that will allow it to work each time with stability.  If you can find one, please let me know, and thank you!

---

### Post by Iarwain ben-adar on 2006-10-07
Hi Splittor,
no problem :D

Just using it to toy with atm..

Anyhow, thanks for making the tut,
gave me something to fiddle with :D


Iarwain

---

### Post by Splittor on 2006-10-07
Yes, you have some new problem I have not seen before, and I'm not even sure how to cause it to occur.  Maybe someone else wil have a similar problem and perhaps an idea on a work around.

---

### Post by pony-tail on 2006-10-07
I have had it working in KDE in Gentoo .
I will see if I can find the forum post I got the howto from - If I can find it again I will see if I can maybe cross reference the two howtos and figure something out .
It's good to have an old PIII laying around that I can muck about with .
Right now though I am trying to get it working on Mepis 6 with a Radeon 9800xt and FGLRX.
Let you know how it goes.

---

### Post by Splittor on 2006-10-07
Thanks a lot, any info is appreciated.  I tried creating symlinks to the startup scrips in /.kde/Autostart, but that didn't work I don't think.

Again, thanks a lot for trying to improve my methodology.

---

### Post by pony-tail on 2006-10-07
I tried it on Mepis -
get the cube - but the desktops are just plain white (the diamond is on both the top and bottom of the cube ) just prior to loading beryl the machine feels dead slow .
Not sur if it is the FGLRx drivers or Mepis's Kernel etc.
Oh well:(

---

### Post by pony-tail on 2006-10-07
Just set it up on a Soltek Qbic P4 with an X700 radeon (Automatix already installed with FGLRX ) took 15 minutes - no noticeable issues .
Soltek is model - 3402 if that is important to anybody . X700 is Sapphire AGP.

---

### Post by Charles Hand on 2006-10-08
> 
```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

This will install the Nvidia driver.  

I have to build the nvidia driver as a module when I build my kernel. Does the above procedure replace that driver, or do I have to remove the old one somehow?

---

### Post by Splittor on 2006-10-08
As far as I know, it should replace the existing driver and you should not need to remove the existing driver, I don't think I've ever removed a driver.

---

### Post by Iarwain ben-adar on 2006-10-08
> **Splittor said:**
> Yes, you have some new problem I have not seen before, and I'm not even sure how to cause it to occur.  Maybe someone else wil have a similar problem and perhaps an idea on a work around.

Hi,
i 'fixed' my problem, just fiddled with some beryl-manager settings :D


Iarwain

---

### Post by dfunkydog on 2006-10-08
> dfunkydog...did you add the repositories, update, upgrade, and then try finding those packages? You need to add the repository that contains the Beryl packages, since they are not in the standard repository listing. Read up towards the top of the tutorial.

I did that... I have given up on beryl and installed compiz which works fine on gnome,but with and xgl session it crashes to a logon screen after a few minutes.

---

### Post by dfunkydog on 2006-10-08
> dfunkydog...did you add the repositories, update, upgrade, and then try finding those packages? You need to add the repository that contains the Beryl packages, since they are not in the standard repository listing. Read up towards the top of the tutorial.

I did that... I have given up on beryl and installed compiz which works fine on gnome, but with and xgl session it crashes to a logon screen after a few minutes.

---

### Post by Splittor on 2006-10-08
Compiz and Beryl aren't that much different, except Beryl is more of a community driven effort.

And you were trying to do it in Gnome before as well?

---

### Post by wheezart on 2006-10-10
Splittor, i have a problem with XGL and Xorg. I've followed your instructions and manged to install Beryl (...coool....) but ran into this problem. Every time i start Xorg nvidia-settings seems to be working fine - all of the settings are present and so on and forth, but when i start XGL my nvidia-settings go ***wham*** and no actual settings aside from the nvidia-settings configuration appear... 
I have a MSI Nvidia geForce MX 440 (bog standart piece of hardware, mind you) and i've installed the latest drivers using your method, but nothing works ok. I'm including ```

gnu@gnu-desktop:~$ glxinfo

name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 440/AGP/SSE/3DNOW!
OpenGL version string: 1.2 (1.5.6 NVIDIA 87.62)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod, GL_EXT_texture_lod_bias,
    GL_EXT_texture_object, GL_EXT_vertex_array,
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

and

~/.xsession-errors 

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "gnu"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/gnu-desktop:/tmp/.ICE-unix/4936
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...
Window manager warning: "0xf0" found in configuration database is not a valid value for keybinding "run_command_terminal"
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
xmodmap:  commandline:1:  bad keycode input line
xmodmap:  unable to open file '22' for reading
xmodmap:  unable to open file '=' for reading
xmodmap:  unable to open file 'BackSpace' for reading
xmodmap:  4 errors encountered, aborting.

(gnome-panel:5013): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5013): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(gnome-panel:5013): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(gnome-panel:5013): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(gnome-panel:5013): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Invalid X Screen 0 specified on line 18 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 19 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 20 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 21 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 22 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 23 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 24 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 25 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 26 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 27 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 28 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 29 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 30 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 31 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 32 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 33 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 34 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 35 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 36 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 37 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 38 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 39 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 40 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 41 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 42 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 43 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 44 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 45 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 46 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 47 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 48 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: Invalid X Screen 0 specified on line 49 of configuration file
       '/home/gnu/.nvidia-settings-rc' (NV-CONTROL extension not supported
       on X Screen 0).


ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


``` whoooa... anywizzy, can you give me a hint as to what exactly is going on?

---

### Post by Splittor on 2006-10-10
You are using Gnome?

---

### Post by wheezart on 2006-10-11
> **Splittor said:**
> You are using Gnome?
Heh, kinda good question =) Yes =)

---

### Post by finnjimm on 2006-10-11
Thanks, now I have Beryl running! A couple of questions though... first of all my fonts in KDE are TINY when using Beryl. From Xorg.0.log it seems that DPI setting is the same with regular X.org and KDE. I'm running as the same user so font config etc. should be the same.

The second question is about direct rendering, as glxinfo shows that direct rendering is not enabled under Xgl, is this normal?

Edit: Xgl is also a CPU hog on my machine. For example if I have a maximized Firefox or Konsole window and I open Amarok player window, Xgl starts to take almost 100% CPU time... I guess there's something broken in my system, but what could it be?

My hardware is P4 3 ghz, Geforce FX 5500.

---

### Post by Splittor on 2006-10-11
Yah wheezart, I hope you didn't follow my guide too closely, since it was for KDE....but it looks like it's not registering the X session correctly, since I did a glxinfo and I got a display name of 1:0.  Yours is showing up as 0:0.  Check your xorg.conf to make sure it's loading the appropriate modules...hmmm...

finnjimm, it could be running short of RAM, especially since Firefox and Amarok both tend to take pretty heavily on system resources.  I'm watching my CPU load and xgl stays between 10-20% cpu usage.

---

### Post by LightsOut on 2006-10-12
When i try to load XGL from the kde menu it hangs a bit then throws me back to the kde login. Here are the module and device sections in my xorg.conf

```

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV41.8 [GeForce Go 6800]"
    Driver         "nvidia"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
EndSection

```

---

### Post by LightsOut on 2006-10-12
nevermind i got it working. this is too cute lol.

---

### Post by Splittor on 2006-10-12
Sweet...the problem was that Option "AllowGLXWithComposite" "true" ?

I know that was in my xorg.conf beforehand and I took it out.

---

### Post by LightsOut on 2006-10-12
nope the problem was that I forget to set the depth to 24. I dont know why i overlooked that.

---

### Post by Splittor on 2006-10-12
Probably because it's not in a [code] block.  I was looking at fixing that since it probably gets overlooked..

---

### Post by finnjimm on 2006-10-14
> **Splittor said:**
> 
finnjimm, it could be running short of RAM, especially since Firefox and Amarok both tend to take pretty heavily on system resources.  I'm watching my CPU load and xgl stays between 10-20% cpu usage.

I have 300 MB free of total 1 GB RAM when having Firefox and Amarok open. The Xgl starts using all CPU time when I have a maximized window (Firefox or Konsole, doesn't matter) and Amarok's window on top of it (even when not playing music). Then, if I start playing music desktop responsiveness goes nearly to zero.

On the other hand, playing music with no big or maximized windows makes no such effect.

---

### Post by YoungGods on 2006-10-14
Just finished installing Beryl and everything went great... thanks a lot for the howto :D

---

### Post by BLTicklemonster on 2006-10-15
I suppose I have beryl up and running. My fonts are smaller, I see the beryl gem, but .... what now? What am I supposed to see or do? What's the fuss all about?


Whoa, never mind, found it. Wow.

---

### Post by YoungGods on 2006-10-15
not sure if this is XGL/Beryl related since I did not tried it before installing Beryl (fresh kubuntu install) but I can't seem to make my ALTGR (right alt) key to work :???: my keyboard is a Microsoft Wireless Multimedia Keyboard 1.0A and the layout is set to Portugal (keymap pt). 
I've checked the xmodmap.sh file created during the install and it seems OK "xmodmap /usr/share/xmodmap/xmodmap.pt" but I can't find the xmodmap folder in /user/share :???: 
any ideas how to solve this issue?

---

### Post by BLTicklemonster on 2006-10-15
Odd, I had problems before when adding render acceleration, so this time, I did this:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
#        Option “RenderAccel” “true”
	VideoRam	128
EndSection
```

And I get the spinning cube effect along with the rad doll window drag effect. That renderaccel kept me from getting this going last time I tried beryl, over a week ago or so. I tried it without editing that this time just to see if it would work.

So if anyone else has a problem like that, just try it anyway.

---

### Post by YoungGods on 2006-10-16
> **YoungGods said:**
> not sure if this is XGL/Beryl related since I did not tried it before installing Beryl (fresh kubuntu install) but I can't seem to make my ALTGR (right alt) key to work :???: my keyboard is a Microsoft Wireless Multimedia Keyboard 1.0A and the layout is set to Portugal (keymap pt). 
I've checked the xmodmap.sh file created during the install and it seems OK "xmodmap /usr/share/xmodmap/xmodmap.pt" but I can't find the xmodmap folder in /user/share :???: 
any ideas how to solve this issue?

If anyone as the same problem here's how to solve it:
- install gnome-applets-data (this will create the /usr/share/xmodmap/ folder and the xmodmap files)
- make sure your xmodmap.sh script is pointing to /usr/share/xmodmap/xmodmap.?? (change ?? to your locale)
and that's it ;)

---

### Post by trubblemaker on 2006-10-16
anyone know if these instructions will work with on the  intel i810 driver or is that just wishful thinking?

---

### Post by leodp on 2006-10-17
Hi Splittor,

working nice here with Nvidia GeForce2 Ti 64MB; not so slow as I thought, althought ~4 to 28% of my 1GHz CPU (512MB RAM) power is on Xgl (fast texture filter).
Mplayer seems ok at full screen, although on a window it's a bit choppy.

I wonder what Vista can do on my HW ;-)

Thanks for the help!

Ciao, Leo

---

### Post by jhenager on 2006-10-17
> **Splittor said:**
> Yah wheezart, I hope you didn't follow my guide too closely, since it was for KDE....but it looks like it's not registering the X session correctly, since I did a glxinfo and I got a display name of 1:0.  Yours is showing up as 0:0.  Check your xorg.conf to make sure it's loading the appropriate modules...hmmm...
Splittor, I am running Gnome and I followed your instructions. It worked anyway. I think somewhere in the last two paragraphs I saw KDE and thought, 'Oh great, here comes another reformat and reinstall, but I then went back to the top and tried to amend anything that pertained to KDE.
I actually did the same thing with Automatix. Maybe the digital Gods are forgiving to me....
As for your code, wheezart, the first flag I see is:
"direct rendering: No"
That may be it right there.

---

### Post by Splittor on 2006-10-17
Well I'm glad my tutorial works for Gnome as well, really.

Sorry about being away from the forums for a bit, now I'm back to support the tutorial.

jhenager - Thanks a ton for telling me you tried to use it on Gnome, since most of the code should really not be window-manager specific (except for the use of kate instead of gedit, and other things).  I may aim to write another tutorial using Gnome instead.

leodp - Thanks for the support, I hope everything works well for you, any questions you know where to find me!

trubblemaker - The instructions that are video driver independent will work, except you will still have to get the appropriate GL modles and activate acceleration.  The machine I have that I think has an Intel 810i I can't reformat and do a trial install, but I'll look around and see what there is, you can also check the Beryl forums where I also hang out at [Beryl Forums]("http://forum.beryl-project.org/")

YoungGods - thanks for pointing that out to me, I thought maybe I had made that change already, or that it was already included in the repositories.  Thanks for finding that!  Hope it all works for you!  And btw, my right alt key doesn't work either, neither does my right ctrl key, and I use a Belkin wired keyboard.  I just don't think they like the right keys :p 

BLTickleMonster - Enjoy Beryl, I hope everything works for you and that you got your bug solved!

---

### Post by BLTicklemonster on 2006-10-19
Thanks Splittor. Only thing I want to know now is how to get the cube to show up looking 3d when I spin it. I only see it side-on, there's no top or bottom, and the background when the cube spins, how can I put an image there?

---

### Post by acheun on 2006-10-19
use ctrl+alt+uparrow/downarrow key for the top and bottom of the cube.  
You can also add your picture to the top/bottom of the cube.  For the background, it's call skydome(or similar).  they are all set in beryl-manager in the same section.
Sorry as I'm not with my ubuntu machine, i can only provide this base on my memories.

---

### Post by BLTicklemonster on 2006-10-19
ah, thanks!

---

### Post by Splittor on 2006-10-19
acheun got it correct.

Good luck BL, any other questions just put em in here...

---

### Post by YoungGods on 2006-10-19
Hi Splittor, 

I'm still having a bit of trouble with the keyboard... the ALTGr key is now working but my left ALT key is not ](*,)  it works before loading Beryl as the window manager and I can ALT+TAB with no problems, but not with Beryl. This also means I cannot rotate the cube with CTRL+ALT+left/right. 
If I pull a window near the border it will go to the next desktop and rotate de cube as expected. 

Here's the xev output when I press the left ALT key with Beryl as the window manager:

KeyPress event, serial 30, synthetic NO, window 0x2a00001,
    root 0x52, subw 0x0, time 1650394214, (68,-12), root: (92,100),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False


Also if I have the green Adept Notifier icon (no update) on the notification area when I load Beryl as the window manager it goes to my panel as a regular window (just like firefox or anything else). 

Anyone knows how to solve this? thanks a lot for your help

---

### Post by Splittor on 2006-10-21
The adept-notifier icon seems to be a bug, it's been happening to me, and other people as well.

The keyboard...I don't know...that's stuff I've never seen before...sorry I'm not very good at this :( 

**side note** I'm no longer using XGL, I've updated to Edgy and am using the Nvidia beta drivers with AIGLX.  I will continue to support the tutorial and help those in need.  

The update to Edgy is well worth it though, consumes less system resources, and Beryl 0.1.1 is quite nice!

---

### Post by finnjimm on 2006-10-21
Is my performance poor, as I have around 70 fps maximum with P4 3GHz and GeForce FX 5500 (beryl-settings, Amarok and Konsole with top open)? When playing music in Amarok and moving windows everything seems quite sluggish and CPU usage goes near 100%... Could someone with similar setup confirm?

---

### Post by Splittor on 2006-10-21
finnjimm - I was messing around the other day, and you can unlock the FPS limiter.  There is a function on the "General" options called "Sync To VBlank."  This tries to set your FPS equal to the refresh rate of your monitor, so you don't experience tearing.  I was getting only 75 fps and no higher and no less, but once I disabled it, I can now get between 300-700 depending on the number of windows open, and I'm yet to experience tearing.

Side note: I used Trevino's SVN repo and am using 0.1.1

Performance improves a ton if you drop XGL and go to Edgy's integrated AIGLX, it's XGL that is taking all the resources.

---

### Post by pichalsi on 2006-10-26
hi, i wanted to follow your tutorial, but as i see your last post... i have edgy and nvidia card but i think not the last beta driver... can you point me to some howto?

Edit : nevermind, i got it working, ROx :P

---

### Post by jixun on 2006-11-01
Thanks Splittor! Your guide was quite helpful.

I have that Adept Notifier window hanging around too. Seems like a bug with Xgl...

I tried using AIGLX first (included by default in Edgy) but my X server dies whenever I call beryl-manager. After trying a bunch of xorg.conf settings (none worked), I gave up and followed these instructions to install xserver-xgl instead. Worked like a charm! Btw, I'm not seeing any performance issues with Beryl+Xgl. It seems just as fast as my normal desktop.

Fwiw, I'm running Kubuntu Edgy with the Nvidia beta driver (self-compiled from the official Nvidia package). Not sure what the problem with AIGLX is, but for now I'm happy enough with Xgl. Running glxgears is painfully slow though.

---

### Post by k-rob on 2006-11-02
:KS :KS :KS :KS :KS  Thanks soooo much for this tutorial! I tried this once before with someone else's tut' and sh*t-canned my system. Had to do a complete re-install <Bleck!> Man, you've saved me many, many hours of frustration - I especially liked the safety fallback KDE login in case things went sideways <again> That's the only reason I tried this again -- This time I followed YOUR tutorial [I'm running Kubuntu 6.06.1 i386 on a Gateway Desktop AMD64 X2 with Nvidia 7300LE] and it worked like a charm first go!   --CHEERS--

---

### Post by Zeroangel on 2006-11-04
Interesting guide, would you be able to update this for Kubuntu Edgy? I'm using it and i'm wary of wrecking my OS so am just waiting for an updated guide.

Has anyone tried this guide on Kubuntu Edgy?

> **Splittor said:**
> Lastly, we must map out the keyboard.  We do this by creating another script:
```
sudo kate /home/yourusername/.kde/Autostart/xmodmap.sh
```Note: replace "yourusername" with your actual username (whatever /home/???/ is.)

A better solution than that is simply to run this command:```
sudo kate /home/$USER/.kde/Autostart/xmodmap.sh
```That will automatically use the proper home dir.

---

### Post by __j__ on 2006-11-07
> **jixun said:**
> I have that Adept Notifier window hanging around too. Seems like a bug with Xgl...

It's not just Xgl. I'm using AIGLX and the Adept Notifier window sticks around for me as well. It's a little annoying but just killing and restarting adept_notifier makes it behave properly.

```
killall adept_notifier && adept_notifier
```

---

### Post by blip on 2006-11-11
Just wanted you to know that after spending more hours than I care to think of trying to get Compiz working... this was successful on the first try!

Even running multiple animations at the same time I can only barely push my processor (3.0 Ghz Pentium D) above 25%! And I think that it has made KDE, if anything, more stable!

---

### Post by kgooding on 2006-11-29
> **finnjimm said:**
> Is my performance poor, as I have around 70 fps maximum with P4 3GHz and GeForce FX 5500 (beryl-settings, Amarok and Konsole with top open)? When playing music in Amarok and moving windows everything seems quite sluggish and CPU usage goes near 100%... Could someone with similar setup confirm?

I have a similar problem...

I have 1gb ram, 3.06 ghz proc. and nvidia GForce 5200FX graphics card.

I am running KDE, Kubuntu Edgy.. With Beryl/XGL and nvidia drivers.
As soon as I run Amarok, top outputs Xorg using 30% + of cpu.
Even upon closing Amarok, Xorg hogs cpu. To resolve I have to restart xserver.

This is annoying as I want to use amarok to have a home network music station over wireless.

I am certain its a beryl issue, possible down to nvidia drivers. I dont want to use AIGXL instead of XGL beacuse I am a n00b to linux and I am worried I'll loose my setup.

I have tried using both nv and nvidia drivers, no luck. I also upgraded amarok to 1.4.4 I think it is (Latest version as of 11/28/2006)


Any ideas much appreciated. Thanks all. Other from that.. top notch tutorial.

Kurt

---

### Post by lcaley on 2006-11-29
First off, thanks for the awesome how-to. This is definitely one of the best ones I've ever seen and the only one worth my time to even read for Kubuntu. I have one thing to add, and one question to ask. 

First off, I think I've found (at least for now) a stable way to load beryl-manager on start up. 

-Go to your .kde/Autostart folder in your home directory (it's hidden, so make sure hidden files are turned on)
-Right click and create a link to application
-Name it beryl-manager
-Now, go to the Application tab, and in the command box, type "beryl-manager" (no quotes)

And thats it! Basically all it does is makes a shortcut to start beryl-manager on KDE start up.

Like I said, this has been stable for me, for about 2 hours now with a few reboots, but I'm not totally sure it will always be like that. 


And now for my question. In my xgl session that the guide showed us how to make, my only options for logging off are to end current session. How would I go about getting the normal "end current session, restart, shutdown" options?

Thanks and congrats on your first, and very successful, how-to! 


Cheers

---

### Post by trevorh7000 on 2006-12-10
[QUOTE=finnjimm;1603698]Thanks, now I have Beryl running! A couple of questions though... first of all my fonts in KDE are TINY when using Beryl. From Xorg.0.log it seems that DPI setting is the same with regular X.org and KDE. I'm running as the same user so font config etc. should be the same.



finnjimm

Did you manage to resolve the tiny font issue. I have just got beryl going on gnome and it has made all my fonts tiny. When I start a xorg session they are back to normal.

Trev

---

### Post by Chake99 on 2007-01-27
Woah I have beryl working, thanks a lot for the tutorial, I am highly appreciative. 

Couple questions: 

How to resolve tiny font issue?

I have only one desktop in the desktop pager at the bottom right, despite the cube having four different sides. Additionally, I cannot give the different sides different wallpapers. Is there a way to increase desktops to 6, get the pager working and show different wallpapers?

Games either don't run in beryl or run very slowly, run with improper colors, or have the menus on top. How does one properly run games in beryl?

Under what would I change the shadow settings that beryl'd windows give? The shadows are brighter than the background :S.

---

### Post by Splittor on 2007-02-18
Thank you everyone for your support! 

Sorry I have not been around much lately....studies keep me busy not...I'll try to be around more often and hopefully get another tutorial out soon...

---

### Post by Decapitated on 2007-03-12
BIG Thanks to you!    I finally have got Beryl!

I have tried 4 guides and none of them worked(I even wrecked my system once).
but now i have it and it is awesome!!

Thanks...

-Decapitated

---

### Post by lanchongzi on 2007-03-13
whatever i have written below is back to normal, once i restarted to PC
i leave the note here just for the case you want to read it :)
still no ideas why it happened though
and this HOW TO really is a very good one
thank you very much for putting so much effort in it




hi there

i encountered i weired problem following your advice
after:

Nvidia Driver Install and Config

To start off, it is a good idea to install Nvidia drivers. This can be accomplished by opening a terminal and typing:

Code:

sudo apt-get install nvidia-kernel-common nvidia-glx

This will install the Nvidia driver. You can then have it configure your Xorg.conf by running in the terminal:

Code:

sudo nvidia-xconfig

To make sure everything was configured right, let's check out the file and make sure. In the terminal, type:

Code:

sudo kate /etc/X11/xorg.conf

Scroll down to the "Modules" section, and make sure that GlCore and dri modules are commented out (or do not exist, due to nvidia-xconfig). The glx module should be enabled. Next, scroll down to the Device section. The Driver should say "nvidia". Underneath it, add in: Option "RenderAccel" "true"

The next section is "Screen" Ensure that the DefaultDepth is set to 24!!! Save the file, and close it.


al my nicely configured panels disappeared ( except kooldeck on the bottom of my screen )
now i can't open KMenu, don't have acces to my applications menu ( at least no that I know of ...)
i typed the panel command which directs me to the panel menu - where every thing is set just the way i wanted it  just WITHOUT having them


any ideas???


P.S. i didn't restart the computer yet - have to work on sth  :)
so maybe it will be all back to normal once it reboots

will post as soon as i did it and know a bit more


P.P.S.  very nice tutorial - not dirty at all
one of the best looking ones   :)

cheers

---

### Post by lanchongzi on 2007-03-13
back again

so I tried beryl manager and the terminal command beryl manager & both time with the result that my screen  goes white ( while all the apps are still running - apparently, since ican still listen to my music ) in the end i had to restart three times - thats never happened before  :( sad sad again )
but with the same effects again
however i can acces the beryl settings manager - without having thatwhite screen

but, still how can I have that beautifull beryl?

btw. i have kompose and 3ddesktop ( the later not active ) on my KDE - might that be the problem ?
or maybe it is that i put that worldmap thing ( can't remember ) - the one from your tutorial, where you said that it would be'us' for people in the states - i also have it set to us
since i figured it would be the keyboard layout, right?
anyway i live in china, but in the install progress i choose the US keyboard layout

can anyone help me?

thanks in advance

L

---

### Post by armorm2 on 2007-09-10
ok....I've gone through the usual 20 hours of searching for an answer to my problem with no luck. I'm trying to install Beryl 0.3.0. A simpler description of the problem - 

1) i run 'beryl' in terminal.....screen flashes and gives me the error directly below in terminal. Also all of the window title bars (minimize, max...buttons) stop showing.

2) i run beryl-manager.........screen flashes me to the login screen.

For both of the above, it is not the 'white screen of death' error. 

More specifically, i get a segmentation fault ERROR when i try to run it:
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.2)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.2)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Segmentation fault

The first time i installed it, i got the little diamond/emerald/whatever to show. I was even able to choose between the window managers (metacity, kwin, and beryl) when i right clicked on it. The problems began when i did 'CTRL ALT BCKSPCE' after installing and choosing between wind. managers. When i logged in again beryl would give me the above error and my kxdocker began having this stupid black frame error (which ironically is supposed to be fixed by installing a compositon manager). 

So I got the latest NVIDIA driver for my video card. Next i re-installed beryl (and its dependencies) successfully according to synaptic packet manager. Here's a little info. about my system:

-Ubuntu Dapper 6.06 w/ kernel 2.6.15-29-686 and KDE version 5:45 
-NVIDIA Geforce FX5500 w/ driver 100.14.11 installed from NVIDIA's site
-This is what my xorg.conf looks like:

*********************************************************************
....blah blu bla

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

...bla blu blah bla
..........

Section "Monitor"
    Identifier     "DELL E173FP"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Monitor        "DELL E173FP"
    DefaultDepth    24
    Option         "NoLogo" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "RenderAccel" "true"
    Option         "XaaNoOffscreenPixmaps" "true"
    Option         "AddARGBGLXVisuals" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection
********************************************************************

as you can see i've been adding a bunch of extra options i found online to try and make beryl work. Some of those options were under the 'Device' section, but got moved under the 'Screen' section by the NVIDIA driver installer after i installed the latest driver. Here's what running 'glxinfo'gives:

********************************************************************
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap,
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos,
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit,
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object,
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs,
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side,
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB,
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square,
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program,
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage,
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint,
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range,
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners,
    GL_NV_register_combiners2, GL_NV_texgen_reflection,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle,
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3,
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
blah blah bla
.....
**********************************************************************

at this point i have no idea what is going wrong. If anyone could help, i would really apreciate it. I can post any other info about the problem as well....thank you in advance.

---

