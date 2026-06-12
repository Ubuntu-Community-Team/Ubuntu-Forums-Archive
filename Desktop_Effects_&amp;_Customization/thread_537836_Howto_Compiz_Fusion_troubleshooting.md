---
title: "Howto: Compiz Fusion troubleshooting"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by michael37 on 2007-08-29
A lot of people report problems with Compiz Fusion in Fiesty Fawn 7.04.  If you have a problem, let us help you by providing information about your system configuration as well as which versions you run.

**Gutsy users: DO NOT USE THIS THREAD.  At the time of writing this message, Gutsy is still in beta, and most HOWTOs do not work for Gutsy.  If you are having problems, either report them to beta feedback or uninstall Gutsy and revert back to Fiesty**

Here are commands that you can run in your terminal.  Post the output of these commands so other forum members can help you!

[LIST]
[*]Which version of Ubuntu am I running?  Fiesty is recommended as a stable version where Compiz Fusion can be enabled.  
```
cat /etc/lsb-release && uname -m
```
[*]Which graphics card are you using: ATI, Nvidia or Intel?
```
egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
```
[*]Is my OpenGL running?
```
glxinfo | egrep 'OpenGL|direct'
```
[*](Intel and Nvidia only) Is AIGLX enabled?
```
grep AIGLX /var/log/Xorg.*.log
```
[*]Which version of Compiz am I running?
```
 sudo dpkg -l | egrep "decor|compiz"
```
[/LIST]

---

### Post by Tom B on 2007-09-03
I tried to install compiz following a few How-Tos. My window borders are gone, and none of the effects seem to work. I tried reinstalling, messing with the settings manager and window decorator, pretty much everything I could find on the forums, and came up with nothing. Before I started this mess, the desktop effects worked fine and I was using Avant Window Navigator. At this point, I would be happy just uninstalling it all and reinstalling desktop effects so I could use AWN (when I tried this, the window borders disappeared when I enabled desktop effects). Here's my output.
         

       Which graphics card are you using: ATI, Nvidia or Intel?
        egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"


        Is my OpenGL running?
       glxinfo | egrep 'OpenGL|direct'

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150 LE/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 96.31
OpenGL extensions:

         (Intel and Nvidia only) Is AIGLX enabled?
         grep AIGLX /var/log/Xorg.*.log
When I do this, there is no output and nothing seems to happen.

          Which version of Compiz am I running?
          sudo dpkg -l | egrep "decor|compiz"
        
Password:
ii  compiz                                     0.3.6-1ubuntu13                            OpenGL window and compositing manager
ii  compiz-core                                0.3.6-1ubuntu13                            OpenGL window and compositing manager
ii  compiz-gnome                               0.3.6-1ubuntu13                            OpenGL window and compositing manager - GNOM
ii  compiz-gtk                                 0.3.6-1ubuntu13                            OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.3.6-1ubuntu13                            OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070814-0ubuntu1~ppa1            Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1              Decorator for compiz-fusion
rc  gnome-compiz-manager                       0.10.3-0ubuntu1                            Compiz Gnome Manager
ii  libberyldecoration0                        0.2.1.dfsg+git20070318-0ubuntu2            Settings library for plugins - Beryl Project
ii  libcompizconfig0                           0.5.2-0ubuntu1~ppa2                        Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.2-0ubuntu3~ppa4                        Compiz window decoration library
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1              Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu1                            Compiz Gnome Manager
ii  python-compizconfig                        0.5.2-0ubuntu1~ppa1                        Compiz configuration system bindings

---

### Post by michael37 on 2007-09-03
Hello, let me guide you to a few how-tos that you may find very helpful.

[LIST=1]
[*]How to enable AIGLX and composite for your Nvidia video card. [https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy).  You need it in order to turn on most 3D effects.
[*]Remove old (and no longer supported) compiz version 0.3.6 that you are still running in order to prepare installing new CompizFusion.
```

sudo apt-get --purge remove compiz* libcompizconfig0 libdecoration0
sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev

```
[*]Install Compiz Fusion [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
[/LIST]

---

### Post by michael37 on 2007-09-03
Another quick comment.
> **Tom B said:**
> 
       Which graphics card are you using: ATI, Nvidia or Intel?
        egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"



I believe line **Option "AddARGBVisuals" "True"** should be in "Device" section, right under line **Driver         "nvidia"**, not in "Screen" section.

---

### Post by Tom B on 2007-09-03
Thanks so much for the quick replies. The first guide you linked about enabling AIGLX said to put Option "AddARGBVisuals" "True" in "Screen," like I already had it (according to some other guide). I tried it that way first, restarted X, removed everything, reinstalled it, ran compiz --replace and....no window borders, no effects. So then I ran ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
``` and restarted X, as suggested in the Troubleshooting section on the guide you linked about installing Compiz Fusion. Still didn't work. So I tried it all with Option "AddARGBVisuals" "True" in "Device" as you suggested. Still no borders, no effects. I checked the Window Decoration settings in Compiz Configuration, the command is "gtk-window-manager." I don't know why that shouldn't work. Grasping at straws, I ran compiz --replace in a terminal to see if it would throw any errors at me. This is what I got: "compiz (core) - Warn: Unable to parse XML metadata from file "core.xml" " I searched my filesystem for "core.xml" and found it in /usr/share/compiz. I opened it up in Firefox, it says "This XML file does not appear to have any style information associated with it. The document tree is shown below." followed by pages and pages of XML. And now I am stuck. Any ideas?

---

### Post by timposer on 2007-09-03
i just downloaded compiz-fusion on ubuntu studio. how do i use compiz rather than GNOME?

---

### Post by Tom B on 2007-09-03
You will still be using GNOME, the desktop environment. You will be replacing Metacity, the default window manager for GNOME. You can do this by typing ```
compiz --replace
``` into a terminal. If everything is configured correctly (unlike some of us), you should be running compiz. You can also run ```
ccsm
``` to run Compiz configuration (assuming you installed that as well).

---

### Post by timposer on 2007-09-03
hmm when i run compiz --replace i get, "Fatal: Compiz can't be ran using VESA or VGA divers."

---

### Post by michael37 on 2007-09-03
> **timposer said:**
> hmm when i run compiz --replace i get, "Fatal: Compiz can't be ran using VESA or VGA divers."

You need to update your video configuration before you are able to run Compiz.  The latter depends on which video card you use.  Please answer the questions from my initial threads in my post.

---

### Post by michael37 on 2007-09-03
> **Tom B said:**
> Thanks so much for the quick replies. The first guide you linked about enabling AIGLX said to put Option "AddARGBVisuals" "True" in "Screen," like I already had it (according to some other guide). I tried it that way first, restarted X, removed everything, reinstalled it, ran compiz --replace and....no window borders, no effects. So then I ran ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
``` and restarted X, as suggested in the Troubleshooting section on the guide you linked about installing Compiz Fusion. Still didn't work. So I tried it all with Option "AddARGBVisuals" "True" in "Device" as you suggested. Still no borders, no effects. I checked the Window Decoration settings in Compiz Configuration, the command is "gtk-window-manager." I don't know why that shouldn't work. Grasping at straws, I ran compiz --replace in a terminal to see if it would throw any errors at me. This is what I got: "compiz (core) - Warn: Unable to parse XML metadata from file "core.xml" " I searched my filesystem for "core.xml" and found it in /usr/share/compiz. I opened it up in Firefox, it says "This XML file does not appear to have any style information associated with it. The document tree is shown below." followed by pages and pages of XML. And now I am stuck. Any ideas?

My #1 question is does your AIGLX work?  The "AddARGBVisuals" parameter is but a small part of the puzzle :)

---

### Post by Tom B on 2007-09-03
When I run "grep AIGLX /var/log/Xorg.*.log", it now returns "(**) Option "AIGLX" "true"." Is that what you mean? I don't know how else to test if it works.

---

### Post by timposer on 2007-09-03
okay i have an ati radeon graphics card and i just fixed the driver, but now when i run the "compiz --replace" command i get "Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system." in return.

---

### Post by kshane on 2007-09-03
HI.  I have been trying to install compiz with no success.  I've used all the how to's with no success.  I've tried Xfce with XGL and Gnome with XGL.  My ATI drivers were installed using Envy.  Any insight you may have would be greatly appreciated...

Here's my info:

Which graphics card are you using: ATI, Nvidia or Intel?

```

Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver  "fglrx"
        Option  "VideoOverlay" "on"
        Option  "OpenGLOverlay" "off"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "1772ED"
        Option          "DPMS"
--
        Option "Composite" "Disable"
EndSection


```

Is my OpenGL running?

```

direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6747 (8.40.4)
OpenGL extensions:


```

Which version of Compiz am I running?

```

ii  compiz                                     0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20070828+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070828+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-unsupported          0.5.2~git20070822+3v1ubuntu3           Collection of plugins for Compiz - Unsupport
ii  compiz-gnome                               0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2~git20070827+3v1ubuntu0           Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.5.2~git20070821+3v1ubuntu0           GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070829+3v1ubuntu0           Settings library for plugins - Compiz Fusion
ii  libdecoration0                             0.5.5~git20070828+3v1ubuntu0           Compiz window decoration library
ii  python-compizconfig                        0.5.2~git20070824+3v1ubuntu0           Python bindings for the Compiz Configuration


```

As I said, any insight or help would be greatly appreciated.

Kevin

---

### Post by kshane on 2007-09-03
> **timposer said:**
> okay i have an ati radeon graphics card and i just fixed the driver, but now when i run the "compiz --replace" command i get "Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system." in return.

Exactly what I get with ATI Radeon X1650...

Kevin

---

### Post by timposer on 2007-09-03
i think it finally worked. im using beryl rather than compiz though.

---

### Post by kshane on 2007-09-03
> **timposer said:**
> i think it finally worked. im using beryl rather than compiz though.

Odd!  I was of the impression that Beryl was an absolute no go with ATIs...  

Which card do you have?

Kevin

---

### Post by crucial123 on 2007-09-03
here is my set of command outputs:  this is after purging compiz and re-installing as instructed by compiz fusion howto

bruce@bruce-desktop:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal,reverse"
        Option      "OverlayOnCRTC2" "1"
        Option      "PairModes" "1280x1024+1280x1024,1280x1024+1024x768,1024x768+1024x768,1280x1024+800x600,1024x768+800x600"
        Option          "DRI"                   "true"
        Option          "ColorTiling"           "on"
        Option          "EnablePageFlip"        "true"
        Option          "AccelMethod"           "EXA"
        Option          "XAANoOffscreenPixmaps"
--
        Option      "Composite" "disable"
EndSection

bruce@bruce-desktop:~$ glxinfo | egrep 'OpenGL|direct'
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 1.2 (2.0.6747 (8.40.4))
OpenGL extensions:
bruce@bruce-desktop:~$ grep AIGLX /var/log/Xorg.*.log
(**) Option "AIGLX" "off"
(**) AIGLX disabled
bruce@bruce-desktop:~$ sudo dpkg -l | egrep "decor|compiz"
ii  compiz                                     0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
rc  compiz-extra                               0.3.6.1-0ubuntu2                       extra third party plugins for compiz
ii  compiz-gnome                               0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
rc  gnome-compiz-manager                       0.10.3-1ubuntu1                        Compiz Gnome Manager
ii  libcompizconfig0                           0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.5~git20070828+3v1ubuntu0           Compiz window decoration library
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings
bruce@bruce-desktop:~$ 


when I get to this point I have a failure


bruce@bruce-desktop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070826 and actual version is 20070828
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'


help

---

### Post by crucial123 on 2007-09-03
Ok  i got past the failure part by reading the fine print in the how to, namely using alt-f2 to run compiz --replace

still need to get my open gl working

---

### Post by timposer on 2007-09-03
to tell you the truth i dont know how it worked. im fairly sure it had something to do with running it in xgl +gnome mode. try that.

---

### Post by michael37 on 2007-09-04
> **kshane said:**
> Exactly what I get with ATI Radeon X1650...

Kevin

Kshane: you are running ATI card.   Config for ATI cards is quite different from any other card.  Please refer to [thread=488385]this thread[/thread] dedicated to ATI cards.  That thread is rather lengthy, but the suggestions there are superb.

---

### Post by michael37 on 2007-09-04
> **timposer said:**
> to tell you the truth i dont know how it worked. im fairly sure it had something to do with running it in xgl +gnome mode. try that.

Second that, **if *and only if* you use ATI card**, you need to configure Xgl which is alpha software.  Xgl is quite tricky to configure.  If that works for you, great!

---

### Post by michael37 on 2007-09-04
> **crucial123 said:**
> Ok  i got past the failure part by reading the fine print in the how to, namely using alt-f2 to run compiz --replace

still need to get my open gl working

Your OpenGL is working perfectly.  I do not see why you are experiencing any issues.  In fact, what exactly are the issues that you are experiencing?  IMHO your compiz should be running perfectly.

---

### Post by michael37 on 2007-09-04
> **Tom B said:**
> When I run "grep AIGLX /var/log/Xorg.*.log", it now returns "(**) Option "AIGLX" "true"." Is that what you mean? I don't know how else to test if it works.

Tom B: Excellent!  Your AIGLX is working perfectly.

I think you are very close to getting your Compiz Fusion working.  Please perform a clean reinstall of Compiz Fusion now that your 3D graphic card is configured.

Instructions are in this post: [http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

---

### Post by crucial123 on 2007-09-04
using your purge list and this [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
I have managed to get compiz fusion working in all aspects except the cube feature.
I have an ati  x1550 agp card and it is not on the gentoo list of supported or tested cards.

If i turn the cube options on --rotate, anyway   I end up with four desktops that i can flip through like an old style score board, which is sort of cool, but no 3d effects.....
ring switcher works and I am still messing around with settings

thanks for your help

---

### Post by Tom B on 2007-09-04
> **michael37 said:**
> Tom B: Excellent!  Your AIGLX is working perfectly.

I think you are very close to getting your Compiz Fusion working.  Please perform a clean reinstall of Compiz Fusion now that your 3D graphic card is configured.

Instructions are in this post: [http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

I did that, and...my window borders disappeared again. I got the same error: " compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"", and none of the effects take place. I'm pretty frustrated at this point. Thanks for all your help, though. (I'm not being sarcastic. Seriously, thanks) Any idea what I could do now?

---

### Post by michael37 on 2007-09-04
> **crucial123 said:**
> using your purge list and this [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
I have managed to get compiz fusion working in all aspects except the cube feature.
I have an ati  x1550 agp card and it is not on the gentoo list of supported or tested cards.

If i turn the cube options on --rotate, anyway   I end up with four desktops that i can flip through like an old style score board, which is sort of cool, but no 3d effects.....
ring switcher works and I am still messing around with settings

thanks for your help

Awesome.  When you say "old style score board", can you drag a window from one to other desktop?  Can you have half a window on one desktop and another half on another desktop?

---

### Post by michael37 on 2007-09-04
> **Tom B said:**
> I did that, and...my window borders disappeared again. I got the same error: " compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"", and none of the effects take place. I'm pretty frustrated at this point. Thanks for all your help, though. (I'm not being sarcastic. Seriously, thanks) Any idea what I could do now?

Sorry you are having problems.  Try starting compiz by running
```

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz --replace

```

Could you do me a favor and re-run through the list of questions in my post #1?  I am sure a lot of info there has changed since you posted your answers originally.

---

### Post by Tom B on 2007-09-04
I tried that and got "```
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
```

Same result- window borders gone, no effects. Here goes.

Which graphics card are you using: ATI, Nvidia or Intel?

[INDENT]Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option  "XAANoOffscreenPixmaps" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
--
    Option         "Composite" "Enable"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier     "Default Layout" #otherwise will give an error and fail to load GDM
        Option         "AIGLX" "true"
EndSection
[/INDENT]

Is my OpenGL running?

[INDENT]direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150 LE/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 96.31
OpenGL extensions:[/INDENT]

(Intel and Nvidia only) Is AIGLX enabled?
[INDENT](**) Option "AIGLX" "true"[/INDENT]

Which version of Compiz am I running?
[INDENT]ii  compiz                                     0.5.2-0ubuntu3~ppa4                        OpenGL window and compositing manager
ii  compiz-core                                0.5.2-0ubuntu3~ppa4                        OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070817-0ubuntu1~ppa1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2-0ubuntu2~ppa1                        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.2-0ubuntu3~ppa4                        OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             0.5.2-0ubuntu3~ppa4                        OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070814-0ubuntu1~ppa1            Compiz configuration settings manager
rc  gnome-compiz-manager                       0.10.3-0ubuntu1                            Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20070813-0ubuntu1~ppa1            Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2-0ubuntu1~ppa2                        Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.2-0ubuntu3~ppa4                        Compiz window decoration library
ii  python-compizconfig                        0.5.2-0ubuntu1~ppa1                        Compiz configuration system bindings[/INDENT]

Update Manger is also telling me I should update compiz to the same version I already have. Not sure what that's about.

---

### Post by grdnwsl on 2007-09-04
Apparently Compiz-Fusion is undergoing a rewrite of the compiz-core module.  Apparently this has broken compiz-fusion on quite a few machines.  I'm having the same problem with the same error and this started happening after upgrading from a working installation to the latest packages.  Compiz-Fusion is still ALPHA software, so expect breakage as the developers work things out.

Here's a link to one of the developer's blogs:
[http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/](http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/)

---

### Post by crucial123 on 2007-09-05
> **michael37 said:**
> Awesome.  When you say "old style score board", can you drag a window from one to other desktop?  Can you have half a window on one desktop and another half on another desktop?

yeah thats right, the only drawbacks are notification popups  appear on both screens and both monitors (mine are two different sizes) should be the same resolution so that the top and bottom panels are both visable. 
 also when I right click on the bottom panel tabs there is no option to move the app window to another desktop, I can open windows on any desktop and move them by grabbing the header or using right click move.

---

### Post by daradib on 2007-09-05
> **Tom B said:**
> I did that, and...my window borders disappeared again. I got the same error: " compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"", and none of the effects take place. I'm pretty frustrated at this point. Thanks for all your help, though. (I'm not being sarcastic. Seriously, thanks) Any idea what I could do now?

> **grdnwsl said:**
> Apparently Compiz-Fusion is undergoing a rewrite of the compiz-core module.  Apparently this has broken compiz-fusion on quite a few machines.  I'm having the same problem with the same error and this started happening after upgrading from a working installation to the latest packages.  Compiz-Fusion is still ALPHA software, so expect breakage as the developers work things out.



Same problem here. Using ATI Radeon X800 with fglrx driver. I have been having this problem for about one-two weeks. Any ideas on what I should do? Use older version of Compiz Fusion (deb package)?

---

### Post by crucial123 on 2007-09-05
> **daradib said:**
> Same problem here. Using ATI Radeon X800 with fglrx driver. I have been having this problem for about one-two weeks. Any ideas on what I should do? Use older version of Compiz Fusion (deb package)?

uninstall compiz 

sudo apt-get --purge remove compiz* libcompizconfig0 libdecoration0

then

sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev

put this whole string in terminal , if it fails remove the filenames that it balks on and run it again untill it works

then follow this howto to install a backported "stable" compiz from gutsy

read the howto and do the setup stuff at the end carefully he covers the window frame problem

---

### Post by ortwein on 2007-09-05
I don't know the first thing about this....but I want to learn.  Here are my stats: (I'm running Kubuntu)

**video card (I have a radeon 9200 pro)**

bonehead@bonehead:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL E173FP"
        Option          "DPMS"
EndSection

bonehead@bonehead:~$

**Open GL settings**

bonehead@bonehead:~$ glxinfo | egrep 'OpenGL|direct'
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
bonehead@bonehead:~$

**Compis** (I thought I'd uninstalled it...guess not.

ic  compiz-extra                               0.3.6.1-0ubuntu2                       extra third party plugins for compiz
rc  compiz-gnome                               0.5.5~git20070905+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk
rc  emerald                                    0.3~git20070717-0ubuntu1~ppa1          Decorator for compiz-fusion
ii  kde-style-polyester                        1.0-1ubuntu2                           Polyester widget style and kwin decoration f
ii  kwin-style-crystal                         1.0.2-1ubuntu1                         semi transparant window decoration for KDE
rc  libberyldecoration0                        0.2.1.dfsg+git20070318-0ubuntu2        Settings library for plugins - Beryl Project
rc  libcompizconfig0                           0.5.2-0ubuntu1~ppa2                    Settings library for plugins - OpenCompositi
rc  libdecoration0                             0.5.5~git20070905+3v1ubuntu0           Compiz window decoration library
rc  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1          Decoration engines for compiz-fusion


[COLOR="Red"]Any help you can give me to get this thing going would be greatly appreciated![/COLOR]

---

### Post by crucial123 on 2007-09-06
sorry i forgot to add the how to link here it is
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

### Post by daradib on 2007-09-06
Thanks. It worked like a charm. (I had tried removing Compiz Fusion and installing Compiz from the Ubuntu official repository, but that didn't work).

---

### Post by Tom B on 2007-09-06
I tried it, and still no window borders; still the error about parsing XML. In the troubleshooting part of the guide, it says > Make sure you have the nvidia-glx driver installed as well as nvidia-xconfig I have nvidia-glx installed, but when I tried to install nvidia-xconfig it said it would have to remove nvidia-glx. Is this normal?

---

### Post by mikeize on 2007-09-11
Just put together a brand new computer, and am frustrated not to be able to run compiz-fusion.  I have tried many various fixes from this site and others to no avail.  Somebody help!  Here are the outputs from the commands at the beginning of the thread:

mike@desktop:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier      "nVidia Corporation NVIDIA Default Card"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60

mike@desktop:~$ glxinfo | egrep 'OpenGL|direct'
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
mike@desktop:~$ grep AIGLX /var/log/Xorg.*.log
/var/log/Xorg.20.log:(==) AIGLX enabled
/var/log/Xorg.20.log:(EE) AIGLX: Screen 0 is not DRI capable

mike@desktop:~$ sudo dpkg -l | egrep "decor|compiz"
Password:
ii  compiz                                     0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager
ii  compiz-core                                0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070829-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070829-0ubuntu1~ppa1        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
ii  libberyldecoration0                        0.2.1.dfsg+git20070318-0ubuntu2        Settings library for plugins - Beryl Project
ii  libcompizconfig-backend-gconf              0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.2+git20070829-0ubuntu1amaranth1    Compiz window decoration library
ii  libdivxdecore0-binary                      5.0.5-1duo1                            DivX MPEG-4 library (decoder)
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings
ii  ttf-larabie-uncommon                       20011216-1.1                           Special decorative fonts from [www.larabiefon](www.larabiefon)

---

### Post by michael37 on 2007-09-11
> **ortwein said:**
> I don't know the first thing about this....but I want to learn.  Here are my stats: (I'm running Kubuntu)

**video card (I have a radeon 9200 pro)**

bonehead@bonehead:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection


That's your problem, you are using "vesa" driver which has no 3D effects!  You got to use "fgrlx" driver.  See [How to enable Binary Driver from ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and then [How to enable Xgl, PAY ATTENTION TO ATI SECTION](https://help.ubuntu.com/community/CompositeManager/Xgl).

---

### Post by michael37 on 2007-09-11
> **mikeize said:**
> Just put together a brand new computer, and am frustrated not to be able to run compiz-fusion.  I have tried many various fixes from this site and others to no avail.  Somebody help!  Here are the outputs from the commands at the beginning of the thread:

mike@desktop:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier      "nVidia Corporation NVIDIA Default Card"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60

mike@desktop:~$ glxinfo | egrep 'OpenGL|direct'
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
mike@desktop:~$ grep AIGLX /var/log/Xorg.*.log
/var/log/Xorg.20.log:(==) AIGLX enabled
/var/log/Xorg.20.log:(EE) AIGLX: Screen 0 is not DRI capable


You problem is not fully configured Nvidia graphics driver.  This has nothing to do with CompizFusion -- you gotta get AIGLX working without "missing" errors. Read this howto: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by mikeize on 2007-09-11
Okay, so I got it solved thanks to this tutorial here:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)


But now, I can't access the CompizConfig Settings Menu.  It appears under System>Preferences, but when I click it nothing happens.  How can I fix this?

-mike


btw- Thanks Michael, it's working now:

mike@desktop:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8500 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11
OpenGL extensions:

---

### Post by michael37 on 2007-09-11
> **Tom B said:**
> I tried it, and still no window borders; still the error about parsing XML. In the troubleshooting part of the guide, it says  I have nvidia-glx installed, but when I tried to install nvidia-xconfig it said it would have to remove nvidia-glx. Is this normal?

Not sure where you found this quote.  I would definitely go with nvidia-glx if is indeed the driver for your hardware (details here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia))

---

### Post by Nistenf on 2007-09-11
Maybe you can help me with I problem I had when I installed Beryl after unistall Compiz Fusion.
[http://ubuntuforums.org/showthread.php?p=3347060](http://ubuntuforums.org/showthread.php?p=3347060)
Just take a look please, maybe you just know how to fix it, and I'll be very happy if you do so.

---

### Post by michael37 on 2007-09-11
> **mikeize said:**
> Okay, so I got it solved thanks to this tutorial here:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)


Ouch, you used Envy.  I've seen Envy (super-new untested binary drivers) cause as much problems as much good they add.  I wouldn't be surprised if the problem is in the Envy-installed driver.

> **mikeize said:**
> 
But now, I can't access the CompizConfig Settings Menu.  It appears under System>Preferences, but when I click it nothing happens.  How can I fix this?


I would fully uninstall Compiz (see the apt-get --purge remove command above in this thread) and then configure Trevino repositories [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/).  Despite occasional instability with Trevino latest code, it may be the only version of Compiz Fusion which can work on your driver.

---

### Post by michael37 on 2007-09-11
> **Nistenf said:**
> Maybe you can help me with I problem I had when I installed Beryl after unistall Compiz Fusion.
[http://ubuntuforums.org/showthread.php?p=3347060](http://ubuntuforums.org/showthread.php?p=3347060)
Just take a look please, maybe you just know how to fix it, and I'll be very happy if you do so.

I have never run Beryl, so no help here, sorry.

---

### Post by Tom B on 2007-09-11
I found it [here]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"). About halfway down the page it says > Additionally for Nvidia users:
Make sure you have a nvidia-glx driver installed (as well as nvidia-xconfig) and use the following command to configure your xorg.conf:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24



I did it with nvidia-glx installed, with the same problems. I think I'm gonna wait for a new version, or something.

---

### Post by mikeize on 2007-09-11
> **michael37 said:**
> Ouch, you used Envy.  I've seen Envy (super-new untested binary drivers) cause as much problems as much good they add.  I wouldn't be surprised if the problem is in the Envy-installed driver.



I would fully uninstall Compiz (see the apt-get --purge remove command above in this thread) and then configure Trevino repositories [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/).  Despite occasional instability with Trevino latest code, it may be the only version of Compiz Fusion which can work on your driver.


All I know is that it's working now.  If it gives me problems later... I just don't feel like fixing what's no longer broke right now!  As for the Compiz menu, I found that all that stuff is in the Beryl menu.  Still working on the "Cube" effect though!

-mike

---

### Post by michael37 on 2007-09-11
> **mikeize said:**
> All I know is that it's working now.  If it gives me problems later... I just don't feel like fixing what's no longer broke right now!  As for the Compiz menu, I found that all that stuff is in the Beryl menu.  Still working on the "Cube" effect though!

-mike

I predict that with Gutsy release nearly all of your problems will be fixed.  You will need, however, to uninstall Envy when installing Gutsy release so you can use Gutsy nvidia binary driver (as in "nvidia" and not "nv").

---

### Post by michael37 on 2007-09-11
> **Tom B said:**
> I found it [here]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"). About halfway down the page it says 

I did it with nvidia-glx installed, with the same problems. I think I'm gonna wait for a new version, or something.

I am sorry this appears to be your only option now.

---

### Post by nandotron on 2007-09-15
Hi there!,

I've been having problems with compiz fusion since the most recent update.  To try to fix it, i tried to install a newer version of fglrx and ended up installing the newest one through envy.  I gather from reading this thread that it may not have been the smartest idea, but when i try to install the fglrx from the ubuntu repositories, i can never get it to work - mesa always shows at the card in use when i run fglrxinfo.

Anyway, i'm not sure if the driver installed through envy is causing it, but when i try to run my xgl session, i get the messed up display that looks like fuzzy tv reception

**Graphics Card:**
Section "Device"
        Identifier  "Generic Video Card"
        Driver  "fglrx"
        Option  "VideoOverlay" "on"
        Option  "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
EndSection

**Open GL**
direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6747 (8.40.4)
OpenGL extensions:

**Compiz Version**
ii  compiz                                     0.5.5~git20070912+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070912+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20070912+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070912+3v1ubuntu1           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070909+3v1ubuntu0           Collection of UNOFFICIAL fusion plugins for 
ii  compiz-gnome                               0.5.5~git20070912+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070912+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20070912+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio
rc  gnome-compiz-manager                       0.10.3-0ubuntu1                        Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2~git20070909+3v1ubuntu0           GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070909+3v1ubuntu0           Settings library for plugins - Compiz Fusion
ii  libdecoration0                             0.5.5~git20070912+3v1ubuntu0           Compiz window decoration library
ii  libdivxdecore0-binary                      5.0.5-1duo1                            DivX MPEG-4 library (decoder)
ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0           Python bindings for the Compiz Configuration





Sorry if the above pieces are not formatted properly, i'm not sure how you guys do it the other way.  Any pointers on where i'm going wrong or how i can revert to the older driver if necessary would be greatly appreciated!

Thanks guys!

---

### Post by michael37 on 2007-09-16
> **nandotron said:**
> Hi there!,
Anyway, i'm not sure if the driver installed through envy is causing it, but when i try to run my xgl session, i get the messed up display that looks like fuzzy tv reception


I have two troubleshooting hints for you.  Number one is bad driver.  Number two is slightly misconfigured xorg.conf.

On the part about fuzzy TV reception -- could you please clarify whether you use a CRT or LCD monitor?  That makes a difference.

Also, I recommend going through [thread=488385]this thread[/thread].  It has lots of details, but it's totally dedicated to ATI fglrx driver which is, in general, hard to configure correctly with 3D acceleration.

For the record, my perfectly working Xgl on fgrlx displays "Direct Rendering = No".  Newer driver might behave differently.  I recommend attaching the output of the most recent /var/log/X*log file to a post in the ATI thread.

---

### Post by baysbenj on 2007-09-29
> **michael37 said:**
> 


Thank you very much for looking at this.  I'm running an ATI X1650 Pro AGP 512MB.  I realize that OpenGL is not enabled, but I'm not certain how to enable it.  I'm running Ubuntu 7.10 Beta.  When I click to enabled Desktop apperance, I get an error saying that "Desktop Effects could not be enabled".  Any advice would be greatly appreciated.

Thanks,
- Ben (new to Linux but liking it so far)


[LIST]
[*]Which graphics card are you using: ATI, Nvidia or Intel?
> Section "Device"
        Identifier      "Generic Video Card"
        Boardname       "ati"
        Busid           "PCI:3:0:0"
        Driver          "fglrx"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Vendorname      "Samsung"
--
        Option          "Composite"     "1"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "VESA driver (generic)"
        Busid           "PCI:3:0:1"
        Driver          "vesa"
        Screen  0
EndSection
Section "screen" # 
        Identifier      "screen1"


[*]Is my OpenGL running?

[quote]
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:



[*]Which version of Compiz am I running?

> 
ii  compiz                                     1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager
ii  compiz-core                                1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1      Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu1      Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13               OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager - plug
ii  libcompizconfig-backend-gconf              0.5.2+git20070918-0ubuntu1      Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2      Settings library for plugins - OpenCompositi
ii  libdecoration0                             1:0.5.2+git20070928-0ubuntu1    Compiz window decoration library



[/LIST]

---

### Post by X-dark on 2007-09-30
I'm running gutsy and doesn't succeed to make compiz work

[LIST]
[*]Which graphics card are you using: ATI, Nvidia or Intel?
```
Section "Device"
        Identifier      "ATI Mobility RADEON X1600"
        Driver          "fglrx"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
        BusID           "PCI:1:0:0"
EndSection

Section "Extensions"
        Option          "Composite"     "1"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"

```
[*]Is my OpenGL running?
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 1.2 (2.0.6747 (8.40.4))
OpenGL extensions:

```

[*]Which version of Compiz am I running?
```
ii  compiz                                        1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager
ii  compiz-core                                   1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                   0.5.2+git20070928-0ubuntu1      Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                    0.5.2+git20070928-0ubuntu1      Collection of plugins from OpenCompositing f
ii  compiz-gnome                                  1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                    1:0.3.6-1ubuntu13               OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                                1:0.5.2+git20070928-0ubuntu1    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager                 0.5.2+git20070912-0ubuntu1      Compiz configuration settings manager
ii  emerald                                       0.3~git20070717-0ubuntu1        Decorator for compiz-fusion
ii  gnome-compiz-manager                          0.10.3-0ubuntu2                 Compiz Gnome Manager
ii  libcompizconfig-backend-gconf                 0.5.2+git20070918-0ubuntu1      Settings library for plugins - OpenCompositi
ii  libcompizconfig0                              0.5.2+git20070919-0ubuntu2      Settings library for plugins - OpenCompositi
ii  libdecoration0                                1:0.5.5~git20070921+3v1ubuntu0  Compiz window decoration library
ii  libemeraldengine0                             0.3~git20070717-0ubuntu1        Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                      0.10.3-0ubuntu2                 Compiz Gnome Manager
ii  python-compizconfig                           0.5.2+git20070912-0ubuntu1      Compiz configuration system bindings

```
[/LIST]

---

### Post by michael37 on 2007-09-30
> **X-dark said:**
> I'm running gutsy and doesn't succeed to make compiz work


Try turning off composite:  in the xorg.conf, change composite "1" to "0"

---

### Post by michael37 on 2007-09-30
> **baysbenj said:**
> [QUOTE=michael37;3274270]


Thank you very much for looking at this.  I'm running an ATI X1650 Pro AGP 512MB.  I realize that OpenGL is not enabled, but I'm not certain how to enable it.  I'm running Ubuntu 7.10 Beta.  When I click to enabled Desktop apperance, I get an error saying that "Desktop Effects could not be enabled".  Any advice would be greatly appreciated.

Thanks,
- Ben (new to Linux but liking it so far)


Good job with Linux so far!  You need to enable restricted driver for your ATI video card.   Go to System->Administration->Restricted Drivers Manager.
More information is in [this HOWTO](https://help.ubuntu.com/community/BinaryDriverHowto/ATI).  You should be able to enable the restricted driver "fglrx" for your ATI card instead of your current "ati" driver.  Let us know how your computer works after that.

Warning:  if you search the web for a ATI driver manager package called Envy, please stay away from it.  It's a great package, but it often does more harm than good for a less experienced users.

---

### Post by michael37 on 2007-09-30
Baysbenj, I TOTALLY blew it!!! You are already running fglrx driver.

Edit your xorg.conf file 
```

sudo nano /etc/X11/xorg.conf

```

and disable Composite extension.  This driver doesn't support this extension.  In your file, you should change to:
```

Option          "Composite"     "0"

```

---

### Post by X-dark on 2007-10-01
> **michael37 said:**
> Try turning off composite:  in the xorg.conf, change composite "1" to "0"

I've just tried this but everything stays identical

---

### Post by X-dark on 2007-10-01
If i do glxinfo on display :0 I get this :
```
 glxinfo -display :0| egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6849 Release
OpenGL extensions:
```
Note that I have updated driver to 8.41.7 in between

---

### Post by jon9314 on 2007-10-01
it dosn't seem to work for me here is my output.

jon@jon-desktop:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "vpr Matrix"
    DefaultDepth    24
    SubSection     "Display"
--
    Option         "Composite" "Enable"
EndSection

jon@jon-desktop:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6200/AGP/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.09
OpenGL extensions:
jon@jon-desktop:~$ grep AIGLX /var/log/Xorg.*.log
jon@jon-desktop:~$ grep AIGLX /var/log/Xorg.*.log
jon@jon-desktop:~$  sudo dpkg -l | egrep "decor|compiz"
[sudo] password for jon:
ii  compiz-core                                1:0.5.5~git20070905+3v1ubuntu0        OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu1            Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070902+3v1ubuntu0          Collection of UNOFFICIAL fusion plugins for 
ii  compiz-fusion-plugins-unsupported          0.5.2~git20070905+3v1ubuntu0          Collection of plugins for Compiz - Unsupport
rc  compiz-gnome                               1:0.5.5~git20070905+3v1ubuntu0        OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                     OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             1:0.5.5~git20070905+3v1ubuntu0        OpenGL window and compositing manager - plug
ii  compiz-settings                            0.07-1~3v1ubuntu0                     Compiz Configuration tool
ii  compizconfig-settings-manager              0.6.99~git20070905+3v1ubuntu0         Plugin and configuration tool - Compiz Fusio
rc  gnome-compiz-manager                       0.10.3-1~3v1ubuntu1                   Compiz Gnome Manager
ii  libberyldecoration0                        0.3.0+git20070324~3v1ubuntu4          Settings library for plugins - Beryl Project
ii  libcompizconfig-backend-gconf              0.5.2+git20070918-0ubuntu1            Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2            Settings library for plugins - OpenCompositi
ii  libdecoration0                             1:0.5.5~git20070905+3v1ubuntu0        Compiz window decoration library
ii  libdivxdecore0-binary                      5.0.5-1duo1                           DivX MPEG-4 library (decoder)
rc  libgnome-compiz-manager0                   0.10.3-1~3v1ubuntu1                   Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1            Compiz configuration system bindings
ii  ttf-larabie-uncommon                       1:20011216-1.1                        Special decorative fonts from [www.larabiefon](www.larabiefon)
jon@jon-desktop:~$

---

### Post by michael37 on 2007-10-01
> **X-dark said:**
> If i do glxinfo on display :0 I get this :
```
 glxinfo -display :0| egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6849 Release
OpenGL extensions:
```
Note that I have updated driver to 8.41.7 in between

Aren't you using Xgl?  ATI card with fgrlx driver does not run with Xorg.  To configure Xgl, go to [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)  and ***carefully*** follow the ATI section.

Your Xgl will work on display :1 not :0.

---

### Post by michael37 on 2007-10-01
> **jon9314 said:**
> it dosn't seem to work for me here is my output.

jon@jon-desktop:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "vpr Matrix"
    DefaultDepth    24
    SubSection     "Display"
--
    Option         "Composite" "Enable"
EndSection

jon@jon-desktop:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6200/AGP/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.09
OpenGL extensions:
jon@jon-desktop:~$ grep AIGLX /var/log/Xorg.*.log
jon@jon-desktop:~$ grep AIGLX /var/log/Xorg.*.log
jon@jon-desktop:~$

Something is seriously strange with your config.  Please attach complete xorg.conf (from /etc/X11) and all files that show as the result of 
```

ls -1 /var/log/Xorg.*.log

```

---

### Post by Nessa on 2007-10-01
When using another user account, do I have to reinstall compiz-fusion?

---

### Post by michael37 on 2007-10-01
> **Nessa said:**
> When using another user account, do I have to reinstall compiz-fusion?

No.

---

### Post by sitelseth on 2007-10-01
I've gone through many guides to try and get compiz working so I can get the cube and wobbly windows, nothing is working though not sure what I did wrong, I've installed fresh several times. Here is my information. 

Which graphics card are you using: ATI, Nvidia or Intel?
Section "Device"

        Identifier      "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"

        Driver          "fglrx"

        Busid           "PCI:1:5:0"



Section "Monitor"

        Identifier      "Generic Monitor"

        Option          "DPMS"




        Option          "Composite"     "0"

Is my OpenGL running?
direct rendering: Yes

OpenGL vendor string: ATI Technologies Inc.

OpenGL renderer string: RADEON XPRESS Series

OpenGL version string: 2.0.6334 (8.34.8)

OpenGL extensions:


Which version of Compiz am I running?
ii  compiz                                     0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager

ii  compiz-core                                0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager

ii  compiz-fusion-plugins-extra                0.5.2~git20070928+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp

ii  compiz-fusion-plugins-main                 0.5.2~git20070928+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp

ii  compiz-gnome                               0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager - GNOM

rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 

ii  compiz-plugins                             0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager - plug

ii  compizconfig-settings-manager              0.6.99~git20070926+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio

ii  libcompizconfig0                           0.5.2~git20070909+3v1ubuntu3           Settings library for plugins - Compiz Fusion

ii  libdecoration0                             0.5.5~git20070928+3v1ubuntu0           Compiz window decoration library

ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0           Python bindings for the Compiz Configuration

Thanks for any and all help, let me know anything I can do.

---

### Post by Nessa on 2007-10-01
Where do I go to to make compiz start after about 20 secs?

---

### Post by BLTicklemonster on 2007-10-01
I gots wobbly windows and all, but I can't enable the cube or anything else in ccsm.

Even sudo ccsm doesn't allow me to make changes.

```
Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "NVIDIA GeForce FX (generic)"
        Busid           "PCI:2:0:0"
        Driver          "nvidia"
        Screen  0
        Vendorname      "NVIDIA"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "XAANoOffscreenPixmaps" "True"
        Option          "NoLogo"                "False"

```
Even though it says failsafe, I got glxgears and nvidia-glx-new is installed.

```

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.19
OpenGL extensions:
```

```
**) Option "AIGLX" "true"
```

```
ii  compiz                                     1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager
ii  compiz-core                                1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1         Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu1         Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1         Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1           Decorator for compiz-fusion
ii  kdeartwork-theme-window                    4:3.5.7-1ubuntu3                   window decoration themes released with KDE
ii  libcompizconfig-backend-gconf              0.5.2+git20070918-0ubuntu1         Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2         Settings library for plugins - OpenCompositi
ii  libdecoration0                             1:0.5.2+git20070928-0ubuntu1       Compiz window decoration library
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1           Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1         Compiz configuration system bindings

```

---

### Post by michael37 on 2007-10-02
> **Nessa said:**
> Where do I go to to make compiz start after about 20 secs?

Could you please clarify your question?  Compiz should start automatically.  If it doesn't, go to System->Preferences->Sessions, select Startup Programs tab and add "compiz --replace" as a new startup program.

---

### Post by michael37 on 2007-10-02
> **BLTicklemonster said:**
> I gots wobbly windows and all, but I can't enable the cube or anything else in ccsm.

Even sudo ccsm doesn't allow me to make changes.


It looks to me that your system (driver, card, Xorg, etc) are perfectly capable.  The problem is compiz itself.

First, do a complete uninstall (with -purge) -- see [this post](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217) and then reinstall of compiz from Trevino repositories.  I went back and force between several repositories, and I currently consider Trevino repositories the best.  More info [here](http://3v1n0.tuxfamily.org/), select the eyecandy (or eyecandy-amd64 if applicable).  

Second, try restarting compiz using command
compiz --replace --sm-disable ccp

---

### Post by michael37 on 2007-10-02
> **sitelseth said:**
> I've gone through many guides to try and get compiz working so I can get the cube and wobbly windows, nothing is working though not sure what I did wrong, I've installed fresh several times. Here is my information. 


Well, you are using Envy driver for your ATI graphics card, which is really problematic for some people.  This thread has lots of people using this driver.  My recommendation is to uninstall Envy and its driver and revert back to the good old restricted driver supported by Fiesty:  apt package org-driver-fglrx.  

Also, I am not clear whether your Xgl is configured correctly.  Are you using :1 display?  I don't think you are.  Check the [Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) guide esp the sections for ATI driver.

---

### Post by BLTicklemonster on 2007-10-02
> **michael37 said:**
> It looks to me that your system (driver, card, Xorg, etc) are perfectly capable.  The problem is compiz itself.

First, do a complete uninstall (with -purge) -- see [this post](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217) and then reinstall of compiz from Trevino repositories.  I went back and force between several repositories, and I currently consider Trevino repositories the best.  More info [here](http://3v1n0.tuxfamily.org/), select the eyecandy (or eyecandy-amd64 if applicable).  

Second, try restarting compiz using command
compiz --replace --sm-disable ccp

I already did the first link you posted, and it doesn't do any good.

The second one doesn't show any repos for gutsy.

doing the command gives me compiz effects, but there's no using the ccsm to change settings. It will show up, but I can't change any settings at all. I click and nothing happens.

Okay, in appearance, if I go to custom settings, it appears I have compiz going, because I get my emerald theme, but I go to the advance settings and of course still can't make changes. I close appearances, open it again, and I'm at the extra setting in visual effects, not custom. it's like it doesn't accept me chosing custom. Therefore, I think there's something really wrong with my ccsm.

---

### Post by BLTicklemonster on 2007-10-02
> **BLTicklemonster said:**
> I gots wobbly windows and all, but I can't enable the cube or anything else in ccsm.

Even sudo ccsm doesn't allow me to make changes.

```
Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "NVIDIA GeForce FX (generic)"
        Busid           "PCI:2:0:0"
        Driver          "nvidia"
        Screen  0
        Vendorname      "NVIDIA"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "XAANoOffscreenPixmaps" "True"
        Option          "NoLogo"                "False"

```
Even though it says failsafe, I got glxgears and nvidia-glx-new is installed.

```

direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.19
OpenGL extensions:
```

```
**) Option "AIGLX" "true"
```

```
ii  compiz                                     1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager
ii  compiz-core                                1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1         Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu1         Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.5.2+git20070928-0ubuntu1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1         Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1           Decorator for compiz-fusion
ii  kdeartwork-theme-window                    4:3.5.7-1ubuntu3                   window decoration themes released with KDE
ii  libcompizconfig-backend-gconf              0.5.2+git20070918-0ubuntu1         Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2         Settings library for plugins - OpenCompositi
ii  libdecoration0                             1:0.5.2+git20070928-0ubuntu1       Compiz window decoration library
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1           Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1         Compiz configuration system bindings

```

??? all of a sudden I get this:

bill@bill-desktop:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 1.2 (2.1.1 NVIDIA 100.14.19)
OpenGL extensions:
bill@bill-desktop:~$ 

(after installing xserver-xgl. I guess I remove it?)

---

### Post by Smaf on 2007-10-04
Ok, I may have screwed something up. "ccsm" won't let me enable/disable plugins. However, "gksu ccsm" will.... but they won't affect my session.

---

### Post by Dwiman89 on 2007-10-05
I dont Have any windows borders. and the cube wont rotate.

```
derrick@Hambone:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
--
    Option         "Composite" "Enable"
EndSection

derrick@Hambone:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.11
OpenGL extensions:
derrick@Hambone:~$ grep AIGLX /var/log/Xorg.*.log
derrick@Hambone:~$  sudo dpkg -l | egrep "decor|compiz"
Password:
ii  compiz                                     0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20070928+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070928+3v1ubuntu0           Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070921+3v1ubuntu0           Collection of UNOFFICIAL fusion plugins for 
ii  compiz-gnome                               0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070928+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20070926+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.5.2~git20070918+3v1ubuntu0           GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070909+3v1ubuntu3           Settings library for plugins - Compiz Fusion
ii  libdecoration0                             0.5.5~git20070928+3v1ubuntu0           Compiz window decoration library
ii  python-compizconfig                        0.5.2~git20070903+3v1ubuntu0           Python bindings for the Compiz Configuration
derrick@Hambone:~$ 


```

I dont Get any results fom th AIGLX test.

This is what i get when i run it through terminal

```
derrick@Hambone:~$ compiz --replace
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format



```

I hope that info help you help me. Please help? i really want this to work.

---

### Post by Rupertronco on 2007-10-05
You're not getting any results from the aiglx because you don't have it, and you don't need it. Check your other post for the solution I provided.

---

### Post by michael37 on 2007-10-05
> **Smaf said:**
> Ok, I may have screwed something up. "ccsm" won't let me enable/disable plugins. However, "gksu ccsm" will.... but they won't affect my session.

How did you install compiz fusion?  

In any case, restart compiz as yourself (NOT as root) using this command:

```

compiz --replace --sm-disable ccp

```
and try ccsm again.

---

### Post by michael37 on 2007-10-05
> **Rupertronco said:**
> You're not getting any results from the aiglx because you don't have it, and you don't need it. Check your other post for the solution I provided.

Rupert, please clarify which post you are replying and please provide a link to your other reply.

---

### Post by michael37 on 2007-10-05
> **BLTicklemonster said:**
> ??? all of a sudden I get this:

bill@bill-desktop:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/AGP/SSE/3DNOW!
OpenGL version string: 1.2 (2.1.1 NVIDIA 100.14.19)
OpenGL extensions:
bill@bill-desktop:~$ 

(after installing xserver-xgl. I guess I remove it?)

Your problem is Gutsy, which is beta.  I don't run Gutsy and I have no idea how to use it.  I know that most posted HOWTOs will NOT work for Gutsy, and will, in fact, seriously damage your installation.  If you wish to proceed with Gutsy, please use the beta feedback forums.  Otherwise, consider installing Fiesty.
 
I edited the original post and requested that people asking for help in this thread stay with Fiesty, which is a released version  and supports full functionality of Compiz Fusion.  Older versions have issues with incomplete support for CF.

---

### Post by Smaf on 2007-10-05
> **michael37 said:**
> How did you install compiz fusion?  

In any case, restart compiz as yourself (NOT as root) using this command:

```

compiz --replace --sm-disable ccp

```
and try ccsm again.

No change. Still can't enable/disable anything. I installed compiz as detailed in the howto here on ubuntu forums.
I could enable/disable the options before. I must have, at some point, changed them with "sudo ccsm" without realising it, and it locked the permissions or something.
(actually I should probably post this after I've had coffee and wake up so I actually make sense...)

---

### Post by xi0nic on 2007-10-07
Hey all. Trying to run Compiz 0.5.2 on a Thinkpad R60, using the "intel" driver with my 945gm graphics chipset. When I run "compiz --replace", I get the following...
```

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0 

```

I've tried both i810 and intel drivers. I had it working at one point using the CF shell script found here on the forums, but for some reason it just stopped working, and I have no clue what I did wrong. Now installing from Amaranth's Repos. Any help would be appreciated.

* Which version of Ubuntu am I running? Fiesty is recommended as a stable version where Compiz Fusion can be enabled.
```

      DISTRIB_ID=Ubuntu
      DISTRIB_RELEASE=7.04
      DISTRIB_CODENAME=feisty
      DISTRIB_DESCRIPTION="Ubuntu 7.04"
      i686

```

    * Which graphics card are you using: ATI, Nvidia or Intel?

 ```
     
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
--
        Option          "Composite" "Enable"
EndSection

```
    * Is my OpenGL running?

```

direct rendering: Yes
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:

```

    * (Intel and Nvidia only) Is AIGLX enabled?

```

(**) Option "AIGLX" "true"
(**) AIGLX enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
```


    * Which version of Compiz am I running?

```
       
ii  compiz                                     0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager
ii  compiz-core                                0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070917-0ubuntu1~ppa1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070917-0ubuntu3~ppa1            Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                            OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1            Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1              Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20070918-0ubuntu1~ppa1            Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2~ppa1            Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.2+git20070918-0ubuntu5~ppa1            Compiz window decoration library
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1              Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1            Compiz configuration system bindings
```

---

### Post by BLTicklemonster on 2007-10-08
Got mine working, now I'm back to IceWM, so I don't use it any more. :)

---

### Post by gunhippy on 2007-10-08
> **Smaf said:**
> No change. Still can't enable/disable anything. I installed compiz as detailed in the howto here on ubuntu forums.
I could enable/disable the options before. I must have, at some point, changed them with "sudo ccsm" without realising it, and it locked the permissions or something.
(actually I should probably post this after I've had coffee and wake up so I actually make sense...)

The exact same has happened to me, was working yesterday (installed yesterday), got on again today and every check box is greyed out. 

If anybody knows what to do i'd also be glad to hear.

---

### Post by michael37 on 2007-10-08
> **gunhippy said:**
> The exact same has happened to me, was working yesterday (installed yesterday), got on again today and every check box is greyed out. 

If anybody knows what to do i'd also be glad to hear.

I have something to try out for you and for Smaf.

```

cd ~
sudo chown -R `id -u`:`id -g` .gconf
sudo chown -R `id -u`:`id -g` .gnome
sudo chown -R `id -u`:`id -g` .gnome2
sudo chown -R `id -u`:`id -g` .config

```

---

### Post by michael37 on 2007-10-08
> **xi0nic said:**
> Hey all. Trying to run Compiz 0.5.2 on a Thinkpad R60, using the "intel" driver with my 945gm graphics chipset. When I run "compiz --replace", I get the following...
```

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0 

```

I've tried both i810 and intel drivers. I had it working at one point using the CF shell script found here on the forums, but for some reason it just stopped working, and I have no clue what I did wrong. Now installing from Amaranth's Repos. Any help would be appreciated.


I've seen a problem like that before, but I can't find a thread where the person resolved this problem.  I believe the trick was complete uninstall and reinstall of Compiz.

Try this:

sudo apt-get --purge remove compiz* libcompizconfig*

and follow the rest of the instructions from [Amaranth's post](http://forum.compiz-fusion.org/showthread.php?t=3153)

An alternative is waiting for Gutsy which provides a major update to the Intel graphics driver.

---

### Post by xi0nic on 2007-10-08
> **michael37 said:**
> I've seen a problem like that before, but I can't find a thread where the person resolved this problem.  I believe the trick was complete uninstall and reinstall of Compiz.

Try this:

sudo apt-get --purge remove compiz* libcompizconfig*

and follow the rest of the instructions from [Amaranth's post](http://forum.compiz-fusion.org/showthread.php?t=3153)

An alternative is waiting for Gutsy which provides a major update to the Intel graphics driver.

Well oddly enough, I got Gutsy installed today using the Alternate Install CD. Compiz worked, but it was the built-in version which I didn't like. Trying to install an external version, from the git repos using one of the many scripts causes it to not work. I tried full uninstalls of the pre-installed and git versions, reinstalling from apt, couldn't get it working again.

Reinstalling Gutsy again right now, we'll see what happens.

---

### Post by michael37 on 2007-10-08
> **xi0nic said:**
> Well oddly enough, I got Gutsy installed today using the Alternate Install CD. Compiz worked, but it was the built-in version which I didn't like. Trying to install an external version, from the git repos using one of the many scripts causes it to not work. I tried full uninstalls of the pre-installed and git versions, reinstalling from apt, couldn't get it working again.

Reinstalling Gutsy again right now, we'll see what happens.

Really?  The build-in version in Gutsy is 0.6 which is brand new.  Works great for me.

Some plugins are missing, but that's about it.

---

### Post by gunhippy on 2007-10-08
> **michael37 said:**
> I have something to try out for you and for Smaf.

```

cd ~
sudo chown -R `id -u`:`id -g` .gconf
sudo chown -R `id -u`:`id -g` .gnome
sudo chown -R `id -u`:`id -g` .gnome2
sudo chown -R `id -u`:`id -g` .config

```

It didn't work for me =(

I'm really out of my depth here, total linux newbie, so i don't know what other info i could provide that might help but i'm willing to if you can think of anything. I appreciate the reply, any other ideas?

-andy

p.s. just out of interest if it's not too much hassle, what did those commands do?

EDIT:

In the settings manager, Preferances > plugin list, and checking "automatic plugin sorting" fixed it for me.

---

### Post by michael37 on 2007-10-09
> **gunhippy said:**
> It didn't work for me =(

I'm really out of my depth here, total linux newbie, so i don't know what other info i could provide that might help but i'm willing to if you can think of anything. I appreciate the reply, any other ideas?

-andy

p.s. just out of interest if it's not too much hassle, what did those commands do?

EDIT:

In the settings manager, Preferances > plugin list, and checking "automatic plugin sorting" fixed it for me.

Thanks for sharing!  It's awesome that you found a way to fix the problem.

My commands reset permissions on your files back to yourself.  I was going by what Smaf said: he ran ccsm (settings manager) as a superuser and I thought he might have locked himself out on compiz configuration files.   Linux has very strong security system, so a user needs to have permissions to read/write files (especially the config files!).

---

### Post by luisjorge on 2007-10-09
Hello everyone!

I installed CompizFusion on Feisty, and everything works perfectly, except at startup. I added a new program to the Startup programs in Sessions, with the command "compiz --replace", but it doesn't load at startup, no matter what I try. Also, gDesklets (which were installed before compiz, and have always loaded at startup) don't load anymore.

Any ideas on how to fix this?

Thanks in advance!!!

---

### Post by damonius on 2007-10-09
I posted this in the wrong place earlier. It appears this would be a better place to post it:
---

Hey all. This is my first time posting in the Ubuntu Forums.
I'm new to linux and, in turn, Ubuntu. I'm running the Gutsy 7.10 beta.

**PROBLEM: I have enabled Compiz Fusion and it works wonderfully. For a bit. Then it decides it wants to go back to having no desktop effects and changes over to the basic Ubuntu window theme, disables the effects, etc.**

It doesn't look like it happens upon any action on my part. It just seems like it's had enough with me and wants to stop.

Is anyone else experiencing this?

My graphics card is new (today) and is a PNY Verto 512mb GeForce 7600 GS with AGP interface. I got this card to replace my year-old ATi card that was just hell to work with Ubuntu.

Any help you can give me would be much appreciated!

---

### Post by michael37 on 2007-10-09
> **damonius said:**
> I posted this in the wrong place earlier. It appears this would be a better place to post it:
---

Hey all. This is my first time posting in the Ubuntu Forums.
I'm new to linux and, in turn, Ubuntu. I'm running the Gutsy 7.10 beta.

**PROBLEM: I have enabled Compiz Fusion and it works wonderfully. For a bit. Then it decides it wants to go back to having no desktop effects and changes over to the basic Ubuntu window theme, disables the effects, etc.**

It doesn't look like it happens upon any action on my part. It just seems like it's had enough with me and wants to stop.

Is anyone else experiencing this?

My graphics card is new (today) and is a PNY Verto 512mb GeForce 7600 GS with AGP interface. I got this card to replace my year-old ATi card that was just hell to work with Ubuntu.

Any help you can give me would be much appreciated!

Sound like your compiz crashes.    Kinda normal behaviour for beta software :-) you didn't have to run beta software did you :)    When compiz crashes, Ubuntu is smart enough to start a failsafe windows manager called metacity.

When compiz crashes, then apport should notice the crash and report it to the developers.  I wage the problem is in the nvidia driver you are using.  Wait till Gusty becomes released -- that will update a version of your nvidia driver.

To check if apport is installed, run command
```

dpkg -l apport

```

---

### Post by michael37 on 2007-10-09
> **luisjorge said:**
> Hello everyone!

I installed CompizFusion on Feisty, and everything works perfectly, except at startup. I added a new program to the Startup programs in Sessions, with the command "compiz --replace", but it doesn't load at startup, no matter what I try. Also, gDesklets (which were installed before compiz, and have always loaded at startup) don't load anymore.

Any ideas on how to fix this?

Thanks in advance!!!

Run in terminal
```

gconftool-2 -g /desktop/gnome/applications/window_manager/default

```

If it says anything but /usr/bin/compiz, then run the following command:
```

gconftool-2 -s /desktop/gnome/applications/window_manager/default /usr/bin/compiz --type string

```


Log out and log back in.

---

### Post by BuddMan on 2007-10-11
I'm having the same issue.  I can open up a terminal and run compiz just fine, but when placing it in startup sessions, it never will load when I log into gnome.  Michael, I tried your solution and that did not work.

---

### Post by michael37 on 2007-10-11
> **BuddMan said:**
> I'm having the same issue.  I can open up a terminal and run compiz just fine, but when placing it in startup sessions, it never will load when I log into gnome.  Michael, I tried your solution and that did not work.

Are you running Kubuntu instead of Ubuntu?  

If Ubuntu, try this (DO NOT TRY THIS IF YOU HAVE NOT TRIED SUGGESTION IN MY COMMENT 90)

```

gksudo gedit /usr/bin/gnome-wm

```

On the very top of the file, you will find a section like this:
```

# sm-client-id value
SMID=
# default-wm value
DEFWM=

```

Substitute with 

```

DEFWM=compiz

```

Save, exit gedit and reboot.

---

### Post by jdogzilla on 2007-10-14
Hello all, I am running Kubuntu and Feisty.  Compiz has stopped working for me, and I can no longer see the top bar on the window.  When running 'compiz --replace' in a shell window, this is the error that I get ....

A handler is already registered for the path starting with path[0] = "org"

Anybody have any clue as to what may be causing this?

Part of the problem is with setting the correct flags in xorg.conf ... I have a dual screen setup, and the different options are tearing this down.  
So what are the right options/flags to turn on/off for this to work correctly in TwinView?

Thanks

---

### Post by FurryNemesis on 2007-10-15
Me too - however, I do have all my bars working.

---

### Post by michael37 on 2007-10-15
> **jdogzilla said:**
> Hello all, I am running Kubuntu and Feisty.  Compiz has stopped working for me, and I can no longer see the top bar on the window.  When running 'compiz --replace' in a shell window, this is the error that I get ....

A handler is already registered for the path starting with path[0] = "org"

Anybody have any clue as to what may be causing this?

Part of the problem is with setting the correct flags in xorg.conf ... I have a dual screen setup, and the different options are tearing this down.  
So what are the right options/flags to turn on/off for this to work correctly in TwinView?

Thanks

I can't help you don't tell me what your system is.  Please refer to the original post and reply to the questions there.

---

### Post by Arghesis on 2007-10-17
I'm having problem with Compiz Fusion also ... please help me if you can. I'm not using Linux for such a long time. I got just a little familiar with the Konsole.

This is the output from all the commands at the beginning of the thread :

pavel@pom:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
        Driver          "nv"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

pavel@pom:~$ glxinfo | egrep 'OpenGL|direct'
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

pavel@pom:~$ cat /etc/lsb-release && uname -m
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
i686

pavel@pom:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
        Driver          "nv"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

pavel@pom:~$ glxinfo | egrep 'OpenGL|direct'
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

pavel@pom:~$ grep AIGLX /var/log/Xorg.*.log
(==) AIGLX enabled
(EE) AIGLX: Screen 0 is not DRI capable
pavel@pom:~$ sudo dpkg -l | egrep "decor|compiz"
ii  compiz                                     0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070917-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070917-0ubuntu3~ppa1        Collection of plugins from OpenCompositing f
ii  compiz-kde                                 0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager - KDE
ii  compiz-plugins                             0.5.5~git20071006+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.6.99~git20071005+3v1ubuntu0          Plugin and configuration tool - Compiz Fusio
ii  kde-style-polyester                        1.0-1ubuntu2                           Polyester widget style and kwin decoration f
ii  kwin-style-crystal                         1.0.2-1ubuntu1                         semi transparant window decoration for KDE
ii  libcompizconfig-backend-kconfig            0.5.2~git20070920+3v1ubuntu0           KDE Backend for the Compiz Configuration Sys
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2~ppa1        Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.5~git20071006+3v1ubuntu0           Compiz window decoration library
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings

I think there is a problem with OpenGL ...

Do you have any ideea ?

---

### Post by michael37 on 2007-10-17
> **Arghesis said:**
> I'm having problem with Compiz Fusion also ... please help me if you can. I'm not using Linux for such a long time. I got just a little familiar with the Konsole.
...
Do you have any ideea ?

You need to use the restricted Nvidia driver (see Kubuntu 7.04 section).  According to support matrix, you need the "nvidia-glx-new" driver.  Follow instructions at this link: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by michael37 on 2007-10-17
> **Arghesis said:**
> ...
Do you have any ideea ?

Once you run xconfig to enable nvidia driver, don't forget this command from [this howto](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
```

sudo nvidia-xconfig --add-argb-glx-visuals -d 24 

```

---

### Post by Eudaimonia on 2007-10-17
Can't use GL desktop. Haven't tried Compiz, because I can't find the Compiz manager even though Synaptic says it's installed. ATI is enabled.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
i686


Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:5:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
--
        Option      "Composite" "0"
EndSection

direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)
OpenGL extensions:

direct rendering: Yes
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6334 (8.34.8)
OpenGL extensions:
v@vidars:~$ grep AIGLX /var/log/Xorg.*.log
(==) AIGLX enabled
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

---

### Post by michael37 on 2007-10-17
> **Eudaimonia said:**
> Can't use GL desktop. Haven't tried Compiz, because I can't find the Compiz manager even though Synaptic says it's installed. ATI is enabled.



Do you have Xgl installed? You need Xgl to run Compiz with ATI graphics card.

dpkg -l xserver-xgl
fglrxinfo -display :0
fglrxinfo -display :1

---

### Post by Eudaimonia on 2007-10-18
> **michael37 said:**
> Do you have Xgl installed? You need Xgl to run Compiz with ATI graphics card.

dpkg -l xserver-xgl
fglrxinfo -display :0
fglrxinfo -display :1

Seems like it:confused:

v@vidars:~$ sudo dpkg -l xserver-xgl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Navn           Versjon        Beskrivelse
+++-==============-==============-============================================
ii  xserver-xgl    1:1.1.99.1~git GL-based X server
v@vidars:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)

v@vidars:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

---

### Post by michael37 on 2007-10-19
> **Eudaimonia said:**
> Seems like it:confused:

v@vidars:~$ sudo dpkg -l xserver-xgl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Navn           Versjon        Beskrivelse
+++-==============-==============-============================================
ii  xserver-xgl    1:1.1.99.1~git GL-based X server
v@vidars:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)

v@vidars:~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))

Your Xgl is working fine and so it your fgrlx driver.

I recommend upgrading to Gutsy and then running through [thread=569654]my upgrade howto[/thread].  Once you are done with that, Xgl and Compiz on ATI driver are just easier to manage in Gutsy.

---

### Post by Eudaimonia on 2007-10-20
> **michael37 said:**
> Your Xgl is working fine and so it your fgrlx driver.

I recommend upgrading to Gutsy and then running through [thread=569654]my upgrade howto[/thread].  Once you are done with that, Xgl and Compiz on ATI driver are just easier to manage in Gutsy.

Thnaks for great howto. I however mysteriously managed to get it working...

BUT I have another problem, I can't get CAtalyst Control Center working. Despite the fact that Fusion's working, it says that I either don't have the ATI drivers installed Or that they're not properly configured.

I want to use my TV-out (on ATI X1600Pro 512 PCI-e).

---

### Post by michael37 on 2007-10-22
> **Eudaimonia said:**
> Thnaks for great howto. I however mysteriously managed to get it working...

BUT I have another problem, I can't get CAtalyst Control Center working. Despite the fact that Fusion's working, it says that I either don't have the ATI drivers installed Or that they're not properly configured.

I want to use my TV-out (on ATI X1600Pro 512 PCI-e).

I had nothing but trouble with 3D and alternative outputs like TV. Some people have gotten that combination working, but it wasn't me.

---

