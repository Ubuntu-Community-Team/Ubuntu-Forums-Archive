---
title: "Unity disrupted by Janitor"
date: 2013-01-09
forum: Desktop Environments
---

### Post by FuzzyFeat on 2013-01-09
Ubuntu 12.04

After using "Computer Janitor"  (I should have know that a janitor is not qualified to operate as a super user) Unity does not work any more. After trying to reinstall using ```
sudo apt-get install unity
``` I get this message:

```
The following packages have unmet dependencies:
 unity : Depends: libunity-coresynaptic
-5.0-5 (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
         Depends: unity-common (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
```
 
Suggestions please.

---

### Post by ajgreeny on 2013-01-09
Try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by FuzzyFeat on 2013-01-09
Thanks. Tried the command and now the list of the "UNMET" is getting longer.

```
The following packages have unmet dependencies:
 ubuntu-desktop : Depends: unity but it is not going to be installed
```

The same list of unmet dependencies still comes up when it try ```
sudo apt-get install unity
```

```
The following packages have unmet dependencies:
 unity : Depends: libunity-core-5.0-5 (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
         Depends: unity-common (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by ajgreeny on 2013-01-09
OK, you need to fix the broken packages first so try ```
sudo apt-get install -f
```

---

### Post by FuzzyFeat on 2013-01-09
First, thank you for the assistance.

after running  ```
sudo apt-get install -f
```   (I had run this before) the results were:

```
 master@slave:~$ sudo apt-get install -f
[sudo] password for master: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
``` 

After that I ran the install command for unity and got the same dependency problem.No change.

---

### Post by BigCat4 on 2013-01-09
I am not an expert but sometimes using aptitude instead of apt-get takes care of dependencies for me (running 12.04 with Unity).

---

### Post by FuzzyFeat on 2013-01-09
When I use "aptitude" I get  "command not found"

---

### Post by zombifier25 on 2013-01-10
Try doing a
```
sudo apt-get update
```
first, and then retry the instructions above.
Also, aptitude is not installed by default. You must install it:
```
sudo apt-get install aptitude
```
Aptitude handles dependencies better than apt-get, but I doubt it will help you much more.

---

### Post by FuzzyFeat on 2013-01-10
Installed "aptitude" and went through all the commands again and this is what I get. 

```
The following packages have unmet dependencies:
 unity : Depends: libunity-core-5.0-5 (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
         Depends: unity-common (= 5.10.0-0ubuntu6) but 5.12-0ubuntu1.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```
Looks like I will have to either repair the broken packages or do a full re-install.

Other problems have surfaced also: suspend no longer works. Used to work just fine. Now is locks up on resume with a dark screen. Trying to disable suspend but I can't remember the command for the system app.

---

### Post by ajgreeny on 2013-01-10
Now try installing and using **synaptic** which is very good at sorting out held or broken packages.
Use```
sudo apt-get install synaptic
```Start synaptic from dash and use the **Edit ->Fix Broken Packages** menu item.  If that does not work I do not know what else to suggest.

---

### Post by FuzzyFeat on 2013-01-10
Thank you all for the assistance. I had used synaptic and repaired the packages, however after much trial, including "failed to load session" alerts, I have determined that the "Janitor" totally trashed the operating system. When trying to load UNITY i recieved a list of unavailable plugin's
 ```
                
master@slave:~$ unity
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
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2e0021c

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2e0022a

```

The files listed are in the the folder:
```
master@slave:/usr/lib/compiz$ ls
libanimation.so      libfade.so         libopengl.so   libstaticswitcher.so
libccp.so            libgnomecompat.so  libplace.so    libunitymtgrabhandles.so
libcompiztoolbox.so  libgrid.so         libregex.so    libunityshell.so
libcomposite.so      libgtkloader.so    libresize.so   libvpswitch.so
libdecor.so          libimgpng.so       libscale.so    libwall.so
libexpo.so           libmousepoll.so    libsession.so  libworkarounds.so
libezoom.so          libmove.so         libsnap.so
master@slave:/usr/lib/compiz$ 

```

Is a puzzlement!

I will ponder these results and see what inspiration strikes.

---

### Post by FuzzyFeat on 2013-01-16
Well, I finally got most everything operating again. 

First I loaded gnome-panel. this gave me the opportunity to use the old desktop menues that made the following, since i had forgotten the names of some of my favorite apps, a lot easier.

First I took notes on the missing files I got in the error messages from my nonfunctioning apps. I used Synaptic to find the files. Many files were uploaded and wonder upon wonders, the next time I rebooted Unity showed up.

I am still unable to access HDMI with alsamixer, (still working on that one) but aside from that things seem to be operating well.

MORAL: Ubuntu Tweak/Janitor is a DANGERIOUS APPLICATION. DO NOT TRUST THE JANITOR WITH SUPER PRIVELAGES.

SOLVED!  (mostly)

---

### Post by FuzzyFeat on 2013-01-16
Solved

---

