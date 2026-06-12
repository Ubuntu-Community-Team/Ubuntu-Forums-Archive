---
title: "Aero snap"
date: 2012-07-15
forum: Desktop Environments
---

### Post by driftlife on 2012-07-15
From this Article:
 
[http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu](http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu)
 
Followed the directions, but no luck. It's just not working...
 
Anyone know anything about the Aero snap feature?
 
I'm running Ubuntu 12.04 32 bit on a SunVirtual box. VT-x enabled.

---

### Post by Frogs Hair on 2012-07-15
The instruction is from 2009 and not applicable to the latest release. I haven't seen a current solution so far.

---

### Post by MG&amp;TL on 2012-07-15
> **Frogs Hair said:**
> The instruction is from 2009 and not applicable to the latest release. I haven't seen a current solution so far.

I might be missing the point slightly, but doesn't 12.04 do this by default? Just drag windows to the side/top of the screen.

---

### Post by na5h on 2012-07-15
> **MG&TL said:**
> I might be missing the point slightly, but doesn't 12.04 do this by default? Just drag windows to the side/top of the screen.

It doesn't work in Unity 2D...but the instructions that driftlife mentioned above can be used with keyboard shortcuts instead of with "hot corners".

---

### Post by Frogs Hair on 2012-07-15
> **MG&TL said:**
> I might be missing the point slightly, but doesn't 12.04 do this by default? Just drag windows to the side/top of the screen.

It works for me , I guess just haven't used the feature since installing 12.04. :oops: :) There are pending questions at Ask Ubuntu regarding Unity 2D.

---

### Post by driftlife on 2012-07-15
I don't even know if I'm using Unity 2D, total noob here.
 
If aero snap is supported or enabled by default, its not working for me.
 
Update:
Am using Unity 2D.
 
echo $DESKTOP_SESSION
 
Whats Unity 3D like?

---

### Post by driftlife on 2012-07-15
Ok, so trying to get Unity 3D going...
 
Using directions from:
 
[http://www.sysprobs.com/install-virtualbox-guest-additions-on-ubuntu-11-10-2d-and-3d-unity-issues](http://www.sysprobs.com/install-virtualbox-guest-additions-on-ubuntu-11-10-2d-and-3d-unity-issues)
unity --replaceInitializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done
 
 
(compiz:2133): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
WARN  2012-07-15 18:08:59 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-15 18:08:59 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-15 18:08:59 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-07-15 18:08:59 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window65012114
ERROR 2012-07-15 18:08:59 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by Frogs Hair on 2012-07-15
Unity 3D support test: ```
/usr/lib/nux/unity_support_test -p
```

---

### Post by driftlife on 2012-07-15
Yes to all.
 
However, I've read that Unity3D is not supported by Sun virutalbox. Maybe that is it...
3d Accelleration is on.
 
I'm trying to download and run the AMD driver for my Radeon 6470M.
Downloaded, but not sure how to run.... 
 
UPDATE:
[http://www.webupd8.org/2012/02/virtualbox-ubuntu-1204-guest-fixes.html](http://www.webupd8.org/2012/02/virtualbox-ubuntu-1204-guest-fixes.html)
According to this Unity 3D should be supported by virutal box.

---

