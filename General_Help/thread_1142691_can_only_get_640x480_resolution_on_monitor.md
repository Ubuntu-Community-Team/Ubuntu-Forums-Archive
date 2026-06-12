---
title: "can only get 640x480 resolution on monitor"
date: 2009-04-29
forum: General Help
---

### Post by simtaalo on 2009-04-29
my laptop screen died so i'm having to use the laptop with an external monitor. the monitor is a samsung syncmaster 753DFX, the laptop is running jaunty with nvidia geforce go 7400 graphics card.

anyone know how to get a better resolution?

---

### Post by jasreca on 2009-04-29
install envyng-qt and let it download and install latest nvidia driver.

---

### Post by simtaalo on 2009-04-29
i'm running 180.44 which AFAIK is pretty new

---

### Post by max_power on 2009-04-29
check out Post # 3 in this thread

[http://ubuntuforums.org/showthread.php?t=1112186]("http://ubuntuforums.org/showthread.php?t=1112186")

---

### Post by CatKiller on 2009-04-29
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by simtaalo on 2009-04-29
nicely explained catKiller - thanks :) got 1280x1024 now 

although i noticed one teeny mistake, you used 'gksudo' instead of 'gksu' ;)

---

### Post by CatKiller on 2009-04-30
> **simtaalo said:**
> nicely explained catKiller - thanks :) got 1280x1024 now 

although i noticed one teeny mistake, you used 'gksudo' instead of 'gksu' ;)

In this context, they are equivalent. From **man gksu**:
> 
       gksu  is a frontend to su and gksudo is a frontend to sudo.  Their pri&#8208;
       mary purpose is to run graphical commands that need  root  without  the
       need to run an X terminal emulator and using su directly.

       Notice  that  all the magic is done by the underlying library, libgksu.
       Also notice that the library will decide if it should use su or sudo as
       backend  using the /apps/gksu/sudo-mode gconf key, if you call the gksu
       command. You can force the backend by using the gksudo command,  or  by
       using the --sudo-mode and --su-mode options.

although I hadn't actually looked up the difference until you piqued my interest.

---

### Post by simtaalo on 2009-04-30
i remember reading somewhere that using gksudo could be problematic in some cases. not sure what thread it was.

---

### Post by CatKiller on 2009-04-30
> **simtaalo said:**
> i remember reading somewhere that using gksudo could be problematic in some cases. not sure what thread it was.

Using **sudo** directly for graphical applications can cause problems in certain cases because the application then uses the user's own configuration files rather than root's, even though it's root that's running the application. This can lead to permissions problems on those configuration files when the application is run as a normal user at some point in the future.

As far as I know, gksudo does not have the same limitation.

Although it has others, like not being able to Tab-complete the arguments in the same way that you can with sudo. I tend to write the command out with sudo so that I can Tab-complete the rest, and then stick gk at the beginning.

---

### Post by simtaalo on 2009-04-30
cool , cheers for info

---

