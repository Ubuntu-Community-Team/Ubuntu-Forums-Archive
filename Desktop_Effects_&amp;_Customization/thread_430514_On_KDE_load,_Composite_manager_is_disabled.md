---
title: "On KDE load, Composite manager is disabled"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by brm on 2007-05-02
I am attempting to install Beryl on a system running Feisty Fawn and KDE with an nVidia display adapter.

As soon as KDE loads, the following message comes up:
The Composite Manager crashed twice within a minute and is therefore disabled for this session.

This is my current configuration:

bruce@Herodotus:~$ uname -a
Linux Herodotus 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
bruce@Herodotus:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
bruce@Herodotus:~$ dpkg -l | grep nvidia
rc  nvidia-glx                                 1.0.9631+2.6.20.5-15.20                    NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-glx-new                             1.0.9755+2.6.20.5-15.20                    NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-glx-new-dev                         1.0.9755+2.6.20.5-15.20                    NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
ii  nvidia-kernel-common                       20051028+1ubuntu7                          NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   1.0.9755+2.6.20.5-15.20                    NVIDIA binary 'new' kernel module source
bruce@Herodotus:~$

Relevant extracts from /etc/X11/xorg.conf:
Section "Module"

   ... <snip> ...

    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "v4l"
    Load           "vbe"
EndSection

   ... <snip> ...

Section "Monitor"
    Identifier     "Dell 2405FPW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV36.2 [GeForce FX 5700]"
    Monitor        "Dell 2405FPW"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1600x1200" "1440x900" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by rolf-c on 2007-05-02
Has it worked in the past and is not working now?

---

### Post by brm on 2007-05-02
I last tried to enable the composite manager under Dapper. It never worked there either, at least not under KDE. A the time, I did not try any other desktop environments (such as Gnome) nor window managers either.

---

### Post by rolf-c on 2007-05-02
I've not tried KDE with composites but I will before too long. In the mean time, I don't really believe this is a KDE issue (but I've been wrong plenty of times before).

Try this:
```
rolf@unit1:~$ glxinfo |grep direct
direct rendering: Yes
rolf@unit1:~$ 

```

If direct rendering is not Yes then we can start with the nVidia driver.

---

### Post by brm on 2007-05-02
```
bruce@Herodotus:~$ glxinfo | grep direct
direct rendering: Yes
bruce@Herodotus:~$  
```

---

### Post by rolf-c on 2007-05-02
Hmm.

Try adding this to your Xorg.conf file with your other loads.  I noticed you didn't list it in your cut-n-paste above:

```
        Load "dri"
```

---

### Post by brm on 2007-05-02
Rolf,

Thanks for the assistance.

One of the basic instructions since nVidia began publishing a proprietary "blob" for Linux systems has been to disable "dri". In accordance with your suggestion, I tried adding it anyway and restarted X. It did not resolve the composite manager problem :-( .

I double-checked nVidia documentation in case the advice had changed and I had missed it. The orginal advice is still good and one should *_not_* use "dri" with the nVidia proprietary driver. See:
[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=137&p_created=1099952988&p_sid=4bbtIBAi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTAmcF9jYXRzPTAmcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PUxpbnV4IGRyaQ**&p_li=&p_topview=1]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=137&p_created=1099952988&p_sid=4bbtIBAi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTAmcF9jYXRzPTAmcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PUxpbnV4IGRyaQ**&p_li=&p_topview=1")

See also /usr/share/doc/nvidia-glx-new/examples/XF86Config.sample.gz

---

### Post by rolf-c on 2007-05-02
You know, I thought I had that in my Xorg.conf but should have looked first.  I checked and sure enough, it's not in there.

Ok which nVidia driver are you using?

```
rolf@unit1:~$ dmesg |grep NVIDIA
NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
```

---

### Post by brm on 2007-05-02
```
bruce@Herodotus:~$ dmesg | grep NVIDIA
[   71.634142] nvidia: module license 'NVIDIA' taints kernel.
[   71.952862] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
bruce@Herodotus:~$

```

This is the most up-to-date nVidia driver available through normal Ubuntu repositories. I have, however, had the same problem with the composite manager since the first release of Compiz in early 2006. That was "several versions ago" in terms of the nVidia driver.

---

### Post by rolf-c on 2007-05-02
I don't know if dropping to 9631 is going to help.

How about for kicks we drop out of KDE and into gnome for a test?  I'm dubious but running out of suggestions.

---

### Post by brm on 2007-05-02
Aha! It works in Gnome. So we appear to have a KDE problem.

Honestly, since I use KDE 99.99% of the time that I am in an XWindows environment, I was afraid of my lack of familiarity with Gnome. But it was not that hard to see that some of Beryl's eye candy was working: wobbly window moves, "rotating" cubes (rotating at blink speed) and (I don't remember the formal name for this effect:) thumbnaiiling all open applications like the Mac OS X dock.

---

### Post by rolf-c on 2007-05-02
I wouldn't have guessed KDE but here we are.  Well, it's a start anyway. Now it's just a matter of time before you nail it down.  If you do find the answer for KDE, please post it here!

---

### Post by kruppe on 2007-05-21
I get the same problem. Composite manager keeps crashing. Gnome fine.

---

### Post by brm on 2007-05-21
My conclusion is that it is something in our KDE configuration.

I disabled the old KDE configuration by renaming the folder .kde.

When it loads, if KDE does not find the configuration folder .kde, it creates a new one.

After I did that, Beryl now works. There are stability problems and the configuration utility is an opaque nightmare, but none of that is KDE's problem. Beryl works.

It is beyond my technical expertise to track down where in the KDE config the problem is truly hidden.

---

### Post by ps60k on 2007-07-23
Wow, this is an old topic (14 months)...

Short version:

Go to the KDE Control Center -> Desktop -> Window Behavior -> Translucency [tab]  and turn OFF "use translucency/shadows", apply and then restart KDE.

If translucency/shadows was enabled, KDE was trying to enable it's built-in composite manager on top of Beryl, and you cannot run two composite managers at the same time. HOW it got enabled, I don't know (read below), but shut it off and things should work fine.



Detailed version:

In spite of this thread being a little stale, I had this issue come up today. Installed Beryl, used it fine for a week, tweaked the settings, and then it stopped working, with KDE throwing that error. 

Back before Beryl/Xgl/Compiz became somewhat stable, I used to messed around with KDE's built in composite manager a bit. It quickly became obsolete once  Xgl/Beryl/Compiz came out, but it's still built into KDE, albeit disabled by default.

When the error that the [KDE] composite manager crashed twice, I realized I had never turned on the KDE composite manager in the first place; I intended on using Beryl instead. I knew that you cannot run two composite managers at one time, so maybe KDE is trying to launch it's own internal composite manager on top of Beryl? It seems odd because I don't remember turning on the KDE composite manager.

What makes it even more interesting is when brm "deletes" (hides, renames, whatever...) the old KDE config folder, the error goes away and Beryl works again. Perhaps when brm "deleted" the old KDE config, which had the composite manager enabled, it defaulted to disabled when KDE wrote a fresh config on startup, hence allowing Beryl to run unopposed. 

Long story short, I went to where you control KDE's composite manager, and sure enough, it was somehow enabled.

Try shutting it off, restarting KDE, and see how it turns out.

---

