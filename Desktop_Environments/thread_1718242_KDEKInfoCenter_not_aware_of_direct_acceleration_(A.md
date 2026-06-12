---
title: "KDE/KInfoCenter not aware of direct acceleration (ATI)"
date: 2011-03-31
forum: Desktop Environments
---

### Post by hazica on 2011-03-31
Hi everyone,

I am experiencing a very dubious issue with Kwin/KInfoCenter, namely: I have had inconsistent performance when Desktop effects are enabled (Sometimes it is smooth, when **not** a lot of apps are running. After the system has been running for a while and a lot of programs are open, the effects get choppy and rather annoying). What I have discovered as of yesterday though is this: **glxinfo** tells me that direct rendering is actually enabled.

```

raymears@raymears-laptop:~$ glxinfo | grep direct
direct rendering: Yes

```

I have also figured out from **KInfoCenter** that the whole of KDE is relatively uncertain in regards to whether there is any direct rendering available or not. Screenshot: [http://img22.imageshack.us/i/kinfocenter.png/](http://img22.imageshack.us/i/kinfocenter.png/)

Whereas when I do a **kwin --replace**, I get this *contradictory* information (Check out the value of "*direct rendering*"):

```

    raymears@raymears-laptop:~$ kwin --replace
    OpenGL vendor string:                   ATI Technologies Inc.
    OpenGL renderer string:                 ATI Mobility Radeon HD 4650
    OpenGL version string:                  1.4 (3.3.10524 Compatibility Profile Context)
    Driver:                                 Catalyst
    Driver version:                         1.4
    GPU class:                              R700
    OpenGL version:                         1.4
    X server version:                       1.9
    Linux kernel version:                   2.6.35

    Direct rendering:                       no

    Requires strict binding:                yes
    GLSL shaders:                           no
    Texture NPOT support:                   yes
    QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
    QFileSystemWatcher: failed to add paths: /home/raymears/.config/ibus/bus
    Bus::open: Can not get ibus-daemon's address.

```

So it says it doesn't have access to** direct rendering**. Is this information actually relevant? Because from within the "Advanced" tab, under the "Desktop effects" configuration screen, in "System settings" I can check and uncheck the box labelled "Enable direct rendering."

And subjectively speaking, I see a difference between the two modes for the first couple of minutes after the switch. But after that, it behaves in exactly the same manner, regardless of the mode used. And I get the same FPS values in both modes.

If everything was running using indirect rendering it would explain the shitty, inconsistent performance.

Other information: running Kubuntu 10.10, KDE 4.6, on a Vaio with an ATI graphics adapter, using the ATI proprietary driver, installed manually.

```

raymears@raymears-laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4650
OpenGL version string: 3.3.10524 Compatibility Profile Context

```


Any ideas why kwin doesn't play along?

Thanks

PS: I have also tried compiz, as a yardstick of sorts, and its performance is sublime. Too bad it's config and the integration with KDE are crap.

---

