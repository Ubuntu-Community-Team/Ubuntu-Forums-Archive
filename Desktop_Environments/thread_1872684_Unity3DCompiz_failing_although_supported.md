---
title: "Unity3D/Compiz failing although supported"
date: 2011-10-31
forum: Desktop Environments
---

### Post by DuXati on 2011-10-31
Hi all,

Last week I had me a fresh install of Ubuntu 11.10 64bit. After login, Unity hangs, meaning only the user and calendar box in the top panel show up and nothing more happens. I cannot open any programs or see the Unity dash. Unity2D does work, so I tried to enable Compiz there using 

```
compiz --replace
```

This fails, after which some effects like the desktop cube work, but I lose my window borders and the only useful thing I can do is log out (not so useful actually :)). When terminating the hanging command, I lose all keyboard input. The output of the command:

```

Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing mousepoll options...done
Initializing wobbly options...done
Initializing cube options...done
Initializing shift options...done
Initializing thumbnail options...done
Initializing ring options...done
Initializing rotate options...done
Setting Update "sync_to_vblank"
Setting Update "prev_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a00336

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a00344

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a00352

```

Syslog and Xorg.0.log do not mention any errors when trying this.

I'm using a Dell Latitude E6500 with Intel Mobile Integrated Graphics. I'm not using a proprietary driver, the additional driver panel does not suggest one. Also, unity_support_test claims I can run Unity 3D. The output:

```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

Before Ubuntu 11.10, I was using Ubuntu 10.04 with Compiz and all effects worked very well (desktop cube, transparent windows etc), so it isn't a hardware problem.

Any idea someone? I searched around for days, can't seem to find a related issue and could really use some help.

Thanks!

---

### Post by Mark Phelps on 2011-10-31
I've had Unity crash when I made the mistake of installing ccsm -- and only OPENING it!  This may not be the same problem as you have, but the only fix I found that worked is uninstalling compiz and unity, cleaning out the leftovers, reinstalling compiz and unity.  

Directions are in the link below:[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by DuXati on 2011-11-03
Hi Mark,

Thanks for the reply, I'll give it a try. What do you mean by "cleaning out the leftovers"? apt-get autoremove and autoclean?

---

### Post by GiovanniEmex on 2011-11-05
I installed ccsm and opened it to change the size of the Dash and everything was OK. After installing compiz-plugins-extra I tried to open ccsm again and the Unity plugin just disappeared. I had to uninstall the extras, reboot, and look for /usr/bin/ccsm to execute it for re-enabling the Unity plugin.

---

### Post by bluexrider on 2011-11-05
Before you reinstall anything. Check for your ~/home/USER/.compiz folder and the /.unity

Remove them---- then reinstall

---

### Post by DuXati on 2011-11-06
Ok, tried this, but I still get the same errors as before. compiz --replace fails (did not install Unity yet). I'll just go for unity-2d for now. 

Thanks for the help!

---

### Post by jmacx81 on 2011-11-06
bump!
I want my cube and my wobbly windows and I want them now! :)
I'm just not ready to try these things until I see some success stories here.

---

### Post by DuXati on 2011-11-07
One thing we can try is check the logs. I've tried to monitor syslog and Xorg.0.log, but couldn't find anything useful in there. Is there something specific I should look for?

---

