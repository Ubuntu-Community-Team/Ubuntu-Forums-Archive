---
title: "Unity 2D and 3D does not work anyhow."
date: 2012-05-19
forum: Desktop Environments
---

### Post by sebinbenjamin on 2012-05-19
:sad:I recently had to do the **Alt + SysRq + R E I S U B**,as Ubuntu  froze. After restarting I found that there was no unity, just the wallpaper. I also tried logging in with Unity 2D, Gnome - still only wallpaper. 

I tries** unity --reset**, re installed unity - no use. I am stuck with this desktop. 

I get the following output when i run unity ::
[B]

sebin@sebin-desktop:~$ unity 
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key"
[/B]

:sad:

---

### Post by sebinbenjamin on 2012-05-19
i'm using ubuntu 12.04, upgraded from 11.10. 

Someone please help

---

### Post by lolpenguin on 2012-05-20
It looks like a lot of libraries are missing. Your computer probably got somehow corrupted as you reset it's power.

---

### Post by kansasnoob on 2012-05-20
I notice you used the Lubuntu tag on this thread but you're asking about Unity. Did you begin with Lubuntu and then add Unity?

If so Unity is part of the meta-package 'ubuntu-desktop'.

---

### Post by sebinbenjamin on 2012-05-20
I dont know about Lubuntu tags. Maybe got it by mistake.

I upgraded from Ubuntu 11.10 to Ubuntu 12.04. 

[]("http://ubuntuforums.org/member.php?u=554595")

---

### Post by sebinbenjamin on 2012-05-20
I needed to use the computer for some stuff, so I reinstalled Ubuntu 12.04.  I guess Hard disk got corrupted when I forced Reboot. 

Thanks for the Help

---

