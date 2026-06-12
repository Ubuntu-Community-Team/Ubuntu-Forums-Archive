---
title: "Did the lastest compiz update break again?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by sclough on 2006-09-15
This is separate from the last "Today's compiz updates" thread.  I rebooted after installing the compiz updates that were posted a few days ago.  Anyway, now compiz does not start.  If I manually run start-compiz, all I get is "appending output to nohup.out".  Not exactly very helpful since it doesn't write anything to the out file, it looks like it might just die.  Anybody solved this mystery yet?

---

### Post by pcolamar on 2006-09-15
Just the same here.

Actually, when I tried the "compiz-start" I worsened the situation.

At start up I got a slow gnome instead of the xgl/compiz, but after  the manual start I got the typical problem of no frame around the windows.

sigh !

---

### Post by hotstovejer on 2006-09-15
I not only get that problem, but I also lose my top panel, with my menu and my clock and all my other applets.

---

### Post by sclough on 2006-09-15
I never realize how much compiz adds until it breaks like this and I'm forced to log back into a default Gnome session.

---

### Post by StephenL on 2006-09-15
My compiz also broke this morning after applying the updates...

---

### Post by pcolamar on 2006-09-15
Actually it seems that the last upgrade broke the ATI drive.
See fglrxinfo & glxinfo output below.
I might try later to reinstall the ATI drive.
---------
palmer@palmer-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
-----------
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
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

---

### Post by btboudreaux on 2006-09-15
Mine is broken too, but my ati drivers seem to be intact. The update manager said to do a dist-upgrade for compiz, now all hell broke loose... well just no eye candy.... Any solutions?

---

### Post by Dinerty on 2006-09-15
[http://www.ubuntuforums.org/showthread.php?t=250489](http://www.ubuntuforums.org/showthread.php?t=250489)

this thread any help to you guys?

---

### Post by sclough on 2006-09-15
Well, I haven't read every single post, but that thread is what got me going after the last time they broke it with the change to CSM and start-compiz, so I'm guessing this is a different issue.  I guess I need to check my ATI drivers for starters.

---

### Post by btboudreaux on 2006-09-15
> **Dinerty said:**
> [http://www.ubuntuforums.org/showthread.php?t=250489](http://www.ubuntuforums.org/showthread.php?t=250489)

this thread any help to you guys?

That update was a week ago and I got it working after it broke that update. (Just had to edit startup sessions) I'm sure it's not the same problem as today's update. (at least I don't think it is.

---

### Post by Dinerty on 2006-09-15
My bad guys, I was intrigued to know if mine would break so updated 3 mins ago and everything was fine, however to get the new up dates to show I clicked the "check" button on  "Update Manager" and some more new updates appeared.

I know it is not much to go on guys at the moment, I just checked the compiz forums but can't see any new threads about todays updates.

---

### Post by btboudreaux on 2006-09-15
brad@brad-2:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

ATI drivers seem to be working.

Glxgears run fine.

Also, everything that was compiz is now gone in the System menu.

Also, like I said before, I did a dist-upgrade where it installed 3 compiz packages, then it broke. Don't know if that's relevant.

---

### Post by hexion on 2006-09-15
I read many threads with people complaining about compiz crashes... and telling that their systems are unusable...

**There goes an advice to avoid that**:

Everytime you update compiz, take a look at the version you upgraded (your previous version) and note it in a text file.

In example, you run "aptitude update && aptitude upgrade" and it shows upgrades to compiz, compiz-gnome, compiz-core, and cgwd.

Ok, you type "YES" to continue, and dpkg shows you are updating from version "compiz.ubuntu-17.deb" to "compiz.ubuntu-18.deb" (the other 3 packets has their version number too).

You note that package names (ALL FOUR!) and reboot or restart X to see the changes.

Oops!!! There's problem out there.... No problem, don't get on your nervs... remember it's alpha software.

Just downgrade to previous version. How to do that??? Simple.

- Open a terminal
- List your text file where you noted previous versions before the buggy upgrade.
- Go to /var/cache/apt/archives/
- Install previous packets with dpkg -i (all in a single line)

> cd /var/cache/apt/archives
sudo -s
dpkg -i compiz.ubuntu-17.deb compiz-gnome.ubuntu-17.deb compiz-core.ubuntu-17.deb cgwd-15.deb 
Then reboot and everything is like before the upgrade. Then wait a couple of days to upgrade again and FOR SURE there's a new version of compiz solving that problems.

---

### Post by btboudreaux on 2006-09-15
anyone else with any new info?

---

### Post by btboudreaux on 2006-09-15
Ok fixed it.

Don't know if anyone was having the same issues as me. But with dist-upgrade, it updated compiz packages and somehow the themer and csm disappeared and broke compiz. 

I did:

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd

and it reinstalled with my settings intact.

Hope that helps if anyone had my problems.

---

### Post by iam_foo on 2006-09-15
im waiting.
thanks to the ppllzz who posted though

:twisted:

---

### Post by sclough on 2006-09-18
If it helps anybody else, I too found the ATI drivers were no longer working.  I had to remove the fglrx packages and then reinstall the driver and now all is good again.

---

