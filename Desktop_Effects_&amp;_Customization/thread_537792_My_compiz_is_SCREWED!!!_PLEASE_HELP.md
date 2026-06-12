---
title: "My compiz is SCREWED!!! PLEASE HELP"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by Holder on 2007-08-29
Now, I know it will take us a long time to make my compiz work well, but here we goes:

First, I can't even lunch the compiz:

> holder@holder-laptop:~$ compiz --replace
Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.


PLEASE HELP!!!

Thanks,
~Holder.

---

### Post by cudaman73 on 2007-08-29
Before you go off spamming up our forum here, I suggest you do a few things.

Firstly, you need to read what I posted in your other thread.

Secondly, that output there means that you do not have a composite extension in your X session. This means that compositing is not enabled, and therefore, compiz cannot run.

Now, I'm going to need more information than just that error message if you want to get it to work.

What video card are you using?

Have you made sure that you're running the latest video driver for your card (and that 3d acceleration is working?)

What is the output of "glxinfo | grep direct"?

What is the output of "cat /etc/X11/xorg.conf |grep Composite"?

---

### Post by Holder on 2007-08-29
Sorry for kinda spamming =\ this is just driving me insane..

About my video card: i have no idea, how can i check?

This is the output:

> holder@holder-laptop:~$ glxinfo | grep direct
direct rendering: Yes
holder@holder-laptop:~$ cat /etc/X11/xorg.conf |grep Composite
        Option "Composite" "Disable"


What's now?

---

### Post by michael37 on 2007-08-29
You sound like a perfect tester for my new howto on troubleshooting:
[http://ubuntuforums.org/showthread.php?t=537836](http://ubuntuforums.org/showthread.php?t=537836)

---

### Post by cudaman73 on 2007-08-29
Try editing your xorg.conf.

find the extensions section, and change Disable to "Enable"

Should fix the composite problem. Try running compiz again after that and lemme know if that worked.

---

### Post by FuturePilot on 2007-08-29
After editing your xorg.conf you need to restart X for the changes to take effect. Log out and presst Ctrl+Alt+Backspace.

---

### Post by Holder on 2007-08-29
Okay Thanks guys,

Now it's working but with A LOT of problems,

There aren't any effects + no cube (1 desktop) + no window borders.

When i wrote in terminal "compiz --replace":

> holder@holder-laptop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070828
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'


** I write "emerald --replace" and nothing happend (when the "Window Diraction" in the Compiz Config is enabled)

What do you suggest to do now?

---

### Post by AriciU on 2007-08-29
Reinstall compiz...

How in the hell can you not know what video card you have in your system? :confused::confused::lolflag:

---

### Post by Holder on 2007-08-29
I had reinstall it.. but i have those same problems.

BTW, I have figured it out:

My card is: PCI 0:2:0 Generic Intel video card

---

### Post by michael37 on 2007-08-29
> **Holder said:**
> I had reinstall it.. but i have those same problems.

BTW, I have figured it out:

My card is: PCI 0:2:0 Generic Intel video card

I don't think your reinstall succeeded.  Try a reinstall again using [this guide](http://ubuntuforums.org/showthread.php?t=533201).

Please post the versions of your software using this command:
```

 sudo dpkg -l | egrep "decor|compiz"

```

---

### Post by Holder on 2007-08-29
I have reinstaller (again) from this guides: [1, ]("http://ubuntuforums.org/showthread.php?t=533201") (uninstall), and [2]("http://ubuntuforums.org/showthread.php?t=499368") (install)

and about the command:
> holder@holder-laptop:~$  sudo dpkg -l | egrep "decor|compiz"
ii  compiz                                     0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070817-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2-0ubuntu2~ppa1                    Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070828+3v1ubuntu0           Collection of UNOFFICIAL fusion plugins for 
ii  compiz-gnome                               0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070814-0ubuntu1~ppa1        Compiz configuration settings manager
ii  libberyldecoration0                        0.3.0+git20070324~3v1ubuntu4           Settings library for plugins - Beryl Project
ii  libcompizconfig-backend-gconf              0.5.2+git20070813-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2-0ubuntu1~ppa2                    Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.5~git20070828+3v1ubuntu0           Compiz window decoration library
ii  python-compizconfig                        0.5.2-0ubuntu1~ppa1                    Compiz configuration system bindings



Any ideas?

---

### Post by michael37 on 2007-08-29
> **Holder said:**
> I have reinstaller (again) from this guides: [1, ]("http://ubuntuforums.org/showthread.php?t=533201") (uninstall), and [2]("http://ubuntuforums.org/showthread.php?t=499368") (install)

Any ideas?

OK, I think we should have fixed one of your problems.  The compiz --replace command should no longer complain about ccp plugin.  

Let's proceed with your AIGLX settings.  
Run these three commands:
```

egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
glxinfo | egrep 'OpenGL|direct'
grep AIGLX /var/log/Xorg.*.log

```

---

### Post by Holder on 2007-08-29
egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10:

> holder@holder-laptop:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "intel"
        BusID           "PCI:0:2:0"
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51


glxinfo | egrep 'OpenGL|direct':

> holder@holder-laptop:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:


grep AIGLX /var/log/Xorg.*.log:

> holder@holder-laptop:~$ grep AIGLX /var/log/Xorg.*.log
(==) AIGLX enabled
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


What now? O.o

---

### Post by michael37 on 2007-08-29
> **Holder said:**
> 
What now? O.o

Actually, better question for you: What now :)

Start compiz.  Does it start?  If yes, does Cube work?  If not, go to System/Preferences/Desktop Effects.  Is Cube selected?  Start CCSM. Does it start? Is "Window Decoration" Plugin selected?  Is the decorator field says "gtk-window-decorator"?

---

### Post by Holder on 2007-08-29
does it stat? Yes it does.
does the Cube work? No it doesn't
If not, go to System/Preferences/Desktop Effects. Is Cube selected? I don't have it in the menu.
Start CCSM. Does it start? Yes it does
Is "Window Decoration" Plugin selected? Yup
Is the decorator field says "gtk-window-decorator"? Nope.

I have no border or cube, got any ideas? ^^

---

### Post by Holder on 2007-08-29
Oh, Now i got the "desktop effects" after i've installed it (sudo apt-get install desktop-effects).

when i click on "Enable" it freezes my computer and after 30 seconds returnes to the previous settings.

---

### Post by michael37 on 2007-08-29
> **Holder said:**
> does it stat? Yes it does.
does the Cube work? No it doesn't
If not, go to System/Preferences/Desktop Effects. Is Cube selected? I don't have it in the menu.
Start CCSM. Does it start? Yes it does
Is "Window Decoration" Plugin selected? Yup
Is the decorator field says "gtk-window-decorator"? Nope.

I have no border or cube, got any ideas? ^^

Start CCSM.  Go to Preferences, The profile should say "Default".  The Backend should say "Flat file".  Click on "Reset to default".

Go to "Window Decoration" plugin.  Does it say decorator "gtk-window-decorator" now?  If not, just type in gtk-window-decorator in the Command field.

Go to "General Options". Select "Desktop Size".  Change "Horizontal Virtual Size" to 4.

Save, exit, and restart compiz.

---

### Post by Holder on 2007-08-29
> **michael37 said:**
> Start CCSM.  Go to Preferences, The profile should say "Default".  The Backend should say "Flat file".  Click on "Reset to default".

Go to "Window Decoration" plugin.  Does it say decorator "gtk-window-decorator" now?  If not, just type in gtk-window-decorator in the Command field.

I did the "Restore to deafults" and the command line wasn't there, i add it.

> Go to "General Options". Select "Desktop Size".  Change "Horizontal Virtual Size" to 4.

Save, exit, and restart compiz.

Did it (the defualt was 2).


------------------------------------------------------

Window borderas - Doesn't work (X)
Cube - Doesn't work (X)
Effects - Doesn't work (X)
Cpp Plugin - Works (V)


Got any ideas what to do now? =\

---

### Post by michael37 on 2007-08-29
> **Holder said:**
> I did the "Restore to deafults" and the command line wasn't there, i add it.
Got any ideas what to do now? =\

Open "sudo gedit /usr/bin/compiz", scroll down to line

# Set to yes to enable verbose (-v) by default.
VERBOSE="no"

and replace to 

VERBOSE="yes"

Then, restart compiz (compiz --replace).

---

### Post by Holder on 2007-08-30
Did it and nothing changed =/

---

### Post by michael37 on 2007-08-30
> **Holder said:**
> Did it and nothing changed =/

Erm.  When your computer starts, open a terminal and type "compiz --replace".

See what it says in the terminal.

---

### Post by Holder on 2007-08-30
> **michael37 said:**
> Erm.  When your computer starts, open a terminal and type "compiz --replace".

See what it says in the terminal.

here is goes:
> holder@holder-laptop:~$ compiz --replace
Adding compiz option --replace to command line
Checking for Unsupported sessions: not present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 
Checking for FBConfig: present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for copy texture support: present. 
Checking for Intel: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for XDamage extension: present. 
Checking for XSync extension: present. 
Detected 1 screen(s)
Checks indicate compiz should work on your system
Found GNOME desktop environment running...
Found running windows manager: metacity
Setting fallback windows manager to metacity 
Loading the ccp settings interface
Exporting:  LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 WINDOW_MANAGER=/usr/bin/compiz 
Executing: /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-disable ccp 
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070828
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'


well, i guess this fuc*ing cpp plugin is still missing :S

Thanks for having so much attention :]

---

### Post by michael37 on 2007-08-30
> **Holder said:**
> here is goes:


well, i guess this fuc*ing cpp plugin is still missing :S

Thanks for having so much attention :]

Try  set of suggestions from [thread]537385[/thread]

> 
Yeah, that should be /home/-here-goes-your-usernaname-/.compizconfig directory.

Sorry to take you through that again, but I think your best choice is to
1. uninstall compiz (you know the drill)
2. move configs out of all three locations (move, not copy)
[quote]
Nevermind, I figured out. I just did a search and removed everything that contained Compiz. I know that next time I can use make uninstall, but I deleted the source folder already. Now I am going to try a fresh install.

At last! Compiz Fusion is now working! All I had to do was wipe EVERYTHING. 

3. install compiz
4. start compiz

The sequence does matter, and I suspect you did it in a different sequence last time.

Hope it's great for you after that procedure.

[/quote]

---

### Post by michael37 on 2007-08-30
Another suggestion from this thread; [thread]530858[/thread]

I recommend reading this thread -- same problem as yours.

During the remove stage, do this:

```
sudo apt-get --purge remove compiz* libcompizconfig*
```

---

### Post by michael37 on 2007-08-30
> **Holder said:**
> 


well, i guess this fuc*ing ccp plugin is still missing :S

Thanks for having so much attention :]

Run ```
locate ccp
``` to find your broken libccp.so

I get 
```

$ locate libccp
/usr/lib/compiz/libccp.so

```

---

### Post by Holder on 2007-08-30
> **michael37 said:**
> Run ```
locate ccp
``` to find your broken libccp.so

I get 
```

$ locate libccp
/usr/lib/compiz/libccp.so

```


I ran it and:

> holder@holder-laptop:~$ locate ccp
/lib/iptables/libipt_dccp.so
/lib/modules/2.6.20-16-generic/kernel/net/dccp
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_ipv6.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/dccp_ccid2.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/lib
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/lib/dccp_tfrc_lib.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/ccids/dccp_ccid3.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_diag.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_probe.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp_ipv4.ko
/lib/modules/2.6.20-16-generic/kernel/net/dccp/dccp.ko
/lib/modules/2.6.20-16-generic/kernel/net/netfilter/xt_dccp.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp
/lib/modules/2.6.20-15-generic/kernel/net/dccp/dccp_ipv6.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp/ccids
/lib/modules/2.6.20-15-generic/kernel/net/dccp/ccids/dccp_ccid2.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp/ccids/lib
/lib/modules/2.6.20-15-generic/kernel/net/dccp/ccids/lib/dccp_tfrc_lib.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp/ccids/dccp_ccid3.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp/dccp_diag.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp/dccp_probe.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp/dccp_ipv4.ko
/lib/modules/2.6.20-15-generic/kernel/net/dccp/dccp.ko
/lib/modules/2.6.20-15-generic/kernel/net/netfilter/xt_dccp.ko
/home/holder/wine-src/wine-0.9.41~winehq0~ubuntu~7.04/dlls/odbccp32
/home/holder/wine-src/wine-0.9.41~winehq0~ubuntu~7.04/dlls/odbccp32/tests
/home/holder/wine-src/wine-0.9.41~winehq0~ubuntu~7.04/dlls/odbccp32/tests/Makefile.in
/home/holder/wine-src/wine-0.9.41~winehq0~ubuntu~7.04/dlls/odbccp32/tests/misc.c
/home/holder/wine-src/wine-0.9.41~winehq0~ubuntu~7.04/dlls/odbccp32/odbccp32.spec
/home/holder/wine-src/wine-0.9.41~winehq0~ubuntu~7.04/dlls/odbccp32/Makefile.in
/home/holder/wine-src/wine-0.9.41~winehq0~ubuntu~7.04/dlls/odbccp32/odbccp32.c
/usr/src/linux-headers-2.6.20-16/net/dccp
/usr/src/linux-headers-2.6.20-16/net/dccp/ccids
/usr/src/linux-headers-2.6.20-16/net/dccp/ccids/lib
/usr/src/linux-headers-2.6.20-16/net/dccp/ccids/lib/Makefile
/usr/src/linux-headers-2.6.20-16/net/dccp/ccids/Kconfig
/usr/src/linux-headers-2.6.20-16/net/dccp/ccids/Makefile
/usr/src/linux-headers-2.6.20-16/net/dccp/Kconfig
/usr/src/linux-headers-2.6.20-16/net/dccp/Makefile
/usr/src/linux-headers-2.6.20-16/include/linux/netfilter_ipv4/ipt_dccp.h
/usr/src/linux-headers-2.6.20-16/include/linux/dccp.h
/usr/src/linux-headers-2.6.20-16/include/linux/netfilter/xt_dccp.h
/usr/src/linux-headers-2.6.20-15/net/dccp
/usr/src/linux-headers-2.6.20-15/net/dccp/ccids
/usr/src/linux-headers-2.6.20-15/net/dccp/ccids/lib
/usr/src/linux-headers-2.6.20-15/net/dccp/ccids/lib/Makefile
/usr/src/linux-headers-2.6.20-15/net/dccp/ccids/Kconfig
/usr/src/linux-headers-2.6.20-15/net/dccp/ccids/Makefile
/usr/src/linux-headers-2.6.20-15/net/dccp/Kconfig
/usr/src/linux-headers-2.6.20-15/net/dccp/Makefile
/usr/src/linux-headers-2.6.20-15/include/linux/netfilter_ipv4/ipt_dccp.h
/usr/src/linux-headers-2.6.20-15/include/linux/dccp.h
/usr/src/linux-headers-2.6.20-15/include/linux/netfilter/xt_dccp.h
/usr/src/linux-2.6.16ck12/net/dccp
/usr/src/linux-2.6.16ck12/net/dccp/built-in.o
/usr/src/linux-2.6.16ck12/net/dccp/output.c
/usr/src/linux-2.6.16ck12/net/dccp/dccp.h
/usr/src/linux-2.6.16ck12/net/dccp/input.c
/usr/src/linux-2.6.16ck12/net/dccp/minisocks.c
/usr/src/linux-2.6.16ck12/net/dccp/ccids
/usr/src/linux-2.6.16ck12/net/dccp/ccids/built-in.o
/usr/src/linux-2.6.16ck12/net/dccp/ccids/.built-in.o.cmd
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/packet_history.h
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/built-in.o
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/packet_history.c
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/.built-in.o.cmd
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/tfrc_equation.c
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/tfrc.h
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/loss_interval.h
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/Makefile
/usr/src/linux-2.6.16ck12/net/dccp/ccids/lib/loss_interval.c
/usr/src/linux-2.6.16ck12/net/dccp/ccids/ccid3.c
/usr/src/linux-2.6.16ck12/net/dccp/ccids/ccid3.h
/usr/src/linux-2.6.16ck12/net/dccp/ccids/Kconfig
/usr/src/linux-2.6.16ck12/net/dccp/ccids/Makefile
/usr/src/linux-2.6.16ck12/net/dccp/.built-in.o.cmd
/usr/src/linux-2.6.16ck12/net/dccp/options.c
/usr/src/linux-2.6.16ck12/net/dccp/proto.c
/usr/src/linux-2.6.16ck12/net/dccp/ackvec.h
/usr/src/linux-2.6.16ck12/net/dccp/timer.c
/usr/src/linux-2.6.16ck12/net/dccp/ipv6.h
/usr/src/linux-2.6.16ck12/net/dccp/ipv6.c
/usr/src/linux-2.6.16ck12/net/dccp/ackvec.c
/usr/src/linux-2.6.16ck12/net/dccp/Kconfig
/usr/src/linux-2.6.16ck12/net/dccp/ccid.c
/usr/src/linux-2.6.16ck12/net/dccp/diag.c
/usr/src/linux-2.6.16ck12/net/dccp/ccid.h
/usr/src/linux-2.6.16ck12/net/dccp/ipv4.c
/usr/src/linux-2.6.16ck12/net/dccp/Makefile
/usr/src/linux-2.6.16ck12/net/netfilter/xt_dccp.c
/usr/src/linux-2.6.16ck12/Documentation/networking/dccp.txt
/usr/src/linux-2.6.16ck12/include/config/netfilter/xt/match/dccp
/usr/src/linux-2.6.16ck12/include/config/netfilter/xt/match/dccp/module.h
/usr/src/linux-2.6.16ck12/include/config/ip/dccp
/usr/src/linux-2.6.16ck12/include/config/ip/dccp/module.h
/usr/src/linux-2.6.16ck12/include/config/ip/dccp/tfrc
/usr/src/linux-2.6.16ck12/include/config/ip/dccp/tfrc/lib
/usr/src/linux-2.6.16ck12/include/config/ip/dccp/tfrc/lib/module.h
/usr/src/linux-2.6.16ck12/include/config/ip/dccp/ccid3
/usr/src/linux-2.6.16ck12/include/config/ip/dccp/ccid3/module.h
/usr/src/linux-2.6.16ck12/include/config/inet/dccp
/usr/src/linux-2.6.16ck12/include/config/inet/dccp/diag
/usr/src/linux-2.6.16ck12/include/config/inet/dccp/diag/module.h
/usr/src/linux-2.6.16ck12/include/linux/netfilter_ipv4/ipt_dccp.h
/usr/src/linux-2.6.16ck12/include/linux/dccp.h
/usr/src/linux-2.6.16ck12/include/linux/netfilter/xt_dccp.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/net/dccpprobe.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/netfilter/xt/match/dccp.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp/ccid2.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp/tfrc
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp/tfrc/lib.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp/ackvec.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp/ccid3
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp/ccid3/rto.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ip/dccp/ccid3.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/inet/dccp
/usr/src/linux-headers-2.6.20-16-generic/include/config/inet/dccp/diag.h
/usr/src/linux-headers-2.6.20-16-generic/include/linux/dccp.h
/usr/src/linux-2.6.22/net/dccp
/usr/src/linux-2.6.22/net/dccp/probe.c
/usr/src/linux-2.6.22/net/dccp/output.c
/usr/src/linux-2.6.22/net/dccp/dccp.h
/usr/src/linux-2.6.22/net/dccp/input.c
/usr/src/linux-2.6.22/net/dccp/minisocks.c
/usr/src/linux-2.6.22/net/dccp/ccids
/usr/src/linux-2.6.22/net/dccp/ccids/ccid2.h
/usr/src/linux-2.6.22/net/dccp/ccids/lib
/usr/src/linux-2.6.22/net/dccp/ccids/lib/packet_history.h
/usr/src/linux-2.6.22/net/dccp/ccids/lib/packet_history.c
/usr/src/linux-2.6.22/net/dccp/ccids/lib/tfrc_equation.c
/usr/src/linux-2.6.22/net/dccp/ccids/lib/tfrc.h
/usr/src/linux-2.6.22/net/dccp/ccids/lib/loss_interval.h
/usr/src/linux-2.6.22/net/dccp/ccids/lib/Makefile
/usr/src/linux-2.6.22/net/dccp/ccids/lib/loss_interval.c
/usr/src/linux-2.6.22/net/dccp/ccids/ccid3.c
/usr/src/linux-2.6.22/net/dccp/ccids/ccid3.h
/usr/src/linux-2.6.22/net/dccp/ccids/ccid2.c
/usr/src/linux-2.6.22/net/dccp/ccids/Kconfig
/usr/src/linux-2.6.22/net/dccp/ccids/Makefile
/usr/src/linux-2.6.22/net/dccp/feat.c
/usr/src/linux-2.6.22/net/dccp/options.c
/usr/src/linux-2.6.22/net/dccp/proto.c
/usr/src/linux-2.6.22/net/dccp/ackvec.h
/usr/src/linux-2.6.22/net/dccp/timer.c
/usr/src/linux-2.6.22/net/dccp/ipv6.h
/usr/src/linux-2.6.22/net/dccp/sysctl.c
/usr/src/linux-2.6.22/net/dccp/ipv6.c
/usr/src/linux-2.6.22/net/dccp/ackvec.c
/usr/src/linux-2.6.22/net/dccp/feat.h
/usr/src/linux-2.6.22/net/dccp/Kconfig
/usr/src/linux-2.6.22/net/dccp/ccid.c
/usr/src/linux-2.6.22/net/dccp/diag.c
/usr/src/linux-2.6.22/net/dccp/ccid.h
/usr/src/linux-2.6.22/net/dccp/ipv4.c
/usr/src/linux-2.6.22/net/dccp/Makefile
/usr/src/linux-2.6.22/net/netfilter/xt_dccp.c
/usr/src/linux-2.6.22/Documentation/networking/dccp.txt
/usr/src/linux-2.6.22/include/linux/netfilter_ipv4/ipt_dccp.h
/usr/src/linux-2.6.22/include/linux/dccp.h
/usr/src/linux-2.6.22/include/linux/netfilter/xt_dccp.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/net/dccpprobe.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/netfilter/xt/match/dccp.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp/ccid2.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp/tfrc
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp/tfrc/lib.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp/ackvec.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp/ccid3
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp/ccid3/rto.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ip/dccp/ccid3.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/inet/dccp
/usr/src/linux-headers-2.6.20-15-generic/include/config/inet/dccp/diag.h
/usr/src/linux-headers-2.6.20-15-generic/include/linux/dccp.h
/usr/lib/aspell/ccpp.amf
/usr/lib/libgccpp.so.1.0.2
/usr/lib/libgccpp.so.1
/usr/lib/wine/libodbccp32.def
/usr/lib/wine/odbccp32.dll.so
/usr/include/linux/netfilter_ipv4/ipt_dccp.h
/usr/include/linux/dccp.h
/usr/include/linux/netfilter/xt_dccp.h
/usr/share/texmf-tetex/fonts/map/dvips/cc-pl/ccpl.map
/usr/share/pixmaps/gnome-ccperiph.png


:S

---

### Post by michael37 on 2007-08-31
> **Holder said:**
> I ran it and:



:S

I no longer understand what compiz you are running and what you (tried to) uninstall and install.  Could you please run 

```

ls -l /usr/lib/compiz/
sudo dpkg -l | egrep "decor|compiz"

```

---

### Post by Holder on 2007-08-31
> **michael37 said:**
> I no longer understand what compiz you are running and what you (tried to) uninstall and install.  Could you please run 

```

ls -l /usr/lib/compiz/
sudo dpkg -l | egrep "decor|compiz"

```

=\

> holder@holder-laptop:~$ ls -l /usr/lib/compiz/
total 4216
-rw-r--r-- 1 root root  22560 2007-08-28 20:36 lib3d.so
-rw-r--r-- 1 root root  11406 2007-08-22 00:09 libaddhelper.a
-rw-r--r-- 1 root root    988 2007-08-22 00:08 libaddhelper.la
-rw-r--r-- 1 root root  10856 2007-08-22 00:09 libaddhelper.so
-rw-r--r-- 1 root root 156320 2007-08-22 00:02 libanimation.a
-rw-r--r-- 1 root root    988 2007-08-22 00:02 libanimation.la
-rw-r--r-- 1 root root 122056 2007-08-22 00:02 libanimation.so
-rw-r--r-- 1 root root  14848 2007-08-28 20:21 libannotate.so
-rw-r--r-- 1 root root  81900 2007-08-28 20:36 libatlantis.so
-rw-r--r-- 1 root root 562432 2007-08-22 00:09 libbench.a
-rw-r--r-- 1 root root    960 2007-08-22 00:08 libbench.la
-rw-r--r-- 1 root root 561924 2007-08-22 00:09 libbench.so
-rw-r--r-- 1 root root  35680 2007-08-28 20:21 libblur.so
-rw-r--r-- 1 root root  11184 2007-08-21 23:12 libccp.so
-rw-r--r-- 1 root root  16224 2007-08-28 20:36 libcheatsheet.so
-rw-r--r-- 1 root root  11232 2007-08-28 20:21 libclone.so
-rw-r--r-- 1 root root  24102 2007-08-22 00:02 libcolorfilter.a
-rw-r--r-- 1 root root   1002 2007-08-22 00:02 libcolorfilter.la
-rw-r--r-- 1 root root  22636 2007-08-22 00:02 libcolorfilter.so
-rw-r--r-- 1 root root   9038 2007-08-22 00:09 libcrashhandler.a
-rw-r--r-- 1 root root   1009 2007-08-22 00:08 libcrashhandler.la
-rw-r--r-- 1 root root   9036 2007-08-22 00:09 libcrashhandler.so
-rw-r--r-- 1 root root  26268 2007-08-22 00:09 libcubecaps.a
-rw-r--r-- 1 root root    981 2007-08-22 00:08 libcubecaps.la
-rw-r--r-- 1 root root  24776 2007-08-22 00:09 libcubecaps.so
-rw-r--r-- 1 root root  20702 2007-08-22 00:09 libcubereflex.a
-rw-r--r-- 1 root root    995 2007-08-22 00:08 libcubereflex.la
-rw-r--r-- 1 root root  19340 2007-08-22 00:09 libcubereflex.so
-rw-r--r-- 1 root root  31200 2007-08-28 20:21 libcube.so
-rw-r--r-- 1 root root  27200 2007-08-28 20:21 libdbus.so
-rw-r--r-- 1 root root  16192 2007-08-28 20:21 libdecoration.so
-rw-r--r-- 1 root root  28716 2007-08-22 00:02 libexpo.a
-rw-r--r-- 1 root root    959 2007-08-22 00:02 libexpo.la
-rw-r--r-- 1 root root  28324 2007-08-22 00:02 libexpo.so
-rw-r--r-- 1 root root  11032 2007-08-22 00:09 libextrawm.a
-rw-r--r-- 1 root root    974 2007-08-22 00:08 libextrawm.la
-rw-r--r-- 1 root root  10888 2007-08-22 00:09 libextrawm.so
-rw-r--r-- 1 root root  25122 2007-08-22 00:02 libezoom.a
-rw-r--r-- 1 root root    966 2007-08-22 00:02 libezoom.la
-rw-r--r-- 1 root root  25764 2007-08-22 00:02 libezoom.so
-rw-r--r-- 1 root root  10590 2007-08-22 00:09 libfadedesktop.a
-rw-r--r-- 1 root root   1002 2007-08-22 00:08 libfadedesktop.la
-rw-r--r-- 1 root root  10092 2007-08-22 00:09 libfadedesktop.so
-rw-r--r-- 1 root root  10752 2007-08-28 20:21 libfade.so
-rw-r--r-- 1 root root  25486 2007-08-22 00:09 libfirepaint.a
-rw-r--r-- 1 root root    988 2007-08-22 00:08 libfirepaint.la
-rw-r--r-- 1 root root  24680 2007-08-22 00:09 libfirepaint.so
-rw-r--r-- 1 root root  16736 2007-08-28 20:36 libflash.so
-rw-r--r-- 1 root root  16556 2007-08-28 20:21 libfs.so
-rw-r--r-- 1 root root  14120 2007-08-28 20:21 libgconf.so
-rw-r--r-- 1 root root  12070 2007-08-22 00:09 libgears.a
-rw-r--r-- 1 root root    960 2007-08-22 00:08 libgears.la
-rw-r--r-- 1 root root  12528 2007-08-22 00:09 libgears.so
-rw-r--r-- 1 root root   5672 2007-08-28 20:21 libglib.so
-rw-r--r-- 1 root root 145850 2007-08-22 00:09 libgroup.a
-rw-r--r-- 1 root root   1171 2007-08-22 00:08 libgroup.la
-rw-r--r-- 1 root root 131300 2007-08-22 00:09 libgroup.so
-rw-r--r-- 1 root root   9892 2007-08-22 00:02 libimgjpeg.a
-rw-r--r-- 1 root root    994 2007-08-22 00:02 libimgjpeg.la
-rw-r--r-- 1 root root  10536 2007-08-22 00:02 libimgjpeg.so
-rw-r--r-- 1 root root  15208 2007-08-28 20:21 libini.so
-rw-r--r-- 1 root root   5672 2007-08-28 20:21 libinotify.so
-rw-r--r-- 1 root root  13370 2007-08-22 00:09 libmblur.a
-rw-r--r-- 1 root root    960 2007-08-22 00:08 libmblur.la
-rw-r--r-- 1 root root  14308 2007-08-22 00:09 libmblur.so
-rw-r--r-- 1 root root  13184 2007-08-28 20:21 libminimize.so
-rw-r--r-- 1 root root  10080 2007-08-28 20:36 libmousegestures.so
-rw-r--r-- 1 root root  12576 2007-08-28 20:21 libmove.so
-rw-r--r-- 1 root root  17138 2007-08-22 00:02 libneg.a
-rw-r--r-- 1 root root    946 2007-08-22 00:02 libneg.la
-rw-r--r-- 1 root root  16868 2007-08-22 00:02 libneg.so
-rw-r--r-- 1 root root   7488 2007-08-28 20:36 libnotification.so
-rw-r--r-- 1 root root  17134 2007-08-22 00:02 libopacify.a
-rw-r--r-- 1 root root    974 2007-08-22 00:02 libopacify.la
-rw-r--r-- 1 root root  16392 2007-08-22 00:02 libopacify.so
-rw-r--r-- 1 root root  12416 2007-08-28 20:21 libplace.so
-rw-r--r-- 1 root root  10336 2007-08-28 20:21 libplane.so
-rw-r--r-- 1 root root   9896 2007-08-28 20:21 libpng.so
-rw-r--r-- 1 root root  46076 2007-08-22 00:02 libput.a
-rw-r--r-- 1 root root    946 2007-08-22 00:02 libput.la
-rw-r--r-- 1 root root  43748 2007-08-22 00:02 libput.so
-rw-r--r-- 1 root root  14250 2007-08-22 00:09 libreflex.a
-rw-r--r-- 1 root root    967 2007-08-22 00:08 libreflex.la
-rw-r--r-- 1 root root  14376 2007-08-22 00:09 libreflex.so
-rw-r--r-- 1 root root   7840 2007-08-28 20:21 libregex.so
-rw-r--r-- 1 root root  20580 2007-08-22 00:02 libresizeinfo.a
-rw-r--r-- 1 root root   1206 2007-08-22 00:02 libresizeinfo.la
-rw-r--r-- 1 root root  21132 2007-08-22 00:02 libresizeinfo.so
-rw-r--r-- 1 root root  18560 2007-08-28 20:21 libresize.so
-rw-r--r-- 1 root root  43004 2007-08-22 00:02 libring.a
-rw-r--r-- 1 root root    953 2007-08-22 00:02 libring.la
-rw-r--r-- 1 root root  41764 2007-08-22 00:02 libring.so
-rw-r--r-- 1 root root  23424 2007-08-28 20:21 librotate.so
-rw-r--r-- 1 root root  31430 2007-08-22 00:02 libscaleaddon.a
-rw-r--r-- 1 root root    995 2007-08-22 00:02 libscaleaddon.la
-rw-r--r-- 1 root root  31020 2007-08-22 00:02 libscaleaddon.so
-rw-r--r-- 1 root root  24246 2007-08-22 00:09 libscalefilter.a
-rw-r--r-- 1 root root   1002 2007-08-22 00:08 libscalefilter.la
-rw-r--r-- 1 root root  23692 2007-08-22 00:09 libscalefilter.so
-rw-r--r-- 1 root root  26816 2007-08-28 20:21 libscale.so
-rw-r--r-- 1 root root  68756 2007-08-28 20:36 libscreensaver.so
-rw-r--r-- 1 root root  10400 2007-08-28 20:21 libscreenshot.so
-rw-r--r-- 1 root root  57026 2007-08-22 00:02 libshift.a
-rw-r--r-- 1 root root    960 2007-08-22 00:02 libshift.la
-rw-r--r-- 1 root root  54116 2007-08-22 00:02 libshift.so
-rw-r--r-- 1 root root  17388 2007-08-22 00:09 libshowdesktop.a
-rw-r--r-- 1 root root   1002 2007-08-22 00:08 libshowdesktop.la
-rw-r--r-- 1 root root  16300 2007-08-22 00:09 libshowdesktop.so
-rw-r--r-- 1 root root  16350 2007-08-22 00:02 libsnap.a
-rw-r--r-- 1 root root    953 2007-08-22 00:02 libsnap.la
-rw-r--r-- 1 root root  16068 2007-08-22 00:02 libsnap.so
-rw-r--r-- 1 root root  17950 2007-08-22 00:09 libsplash.a
-rw-r--r-- 1 root root    967 2007-08-22 00:08 libsplash.la
-rw-r--r-- 1 root root  18504 2007-08-22 00:09 libsplash.so
-rw-r--r-- 1 root root  14144 2007-08-28 20:21 libsvg.so
-rw-r--r-- 1 root root  24992 2007-08-28 20:21 libswitcher.so
-rw-r--r-- 1 root root   6626 2007-08-22 00:02 libtext.a
-rw-r--r-- 1 root root   1164 2007-08-22 00:02 libtext.la
-rw-r--r-- 1 root root   9136 2007-08-22 00:02 libtext.so
-rw-r--r-- 1 root root  39290 2007-08-22 00:02 libthumbnail.a
-rw-r--r-- 1 root root    988 2007-08-22 00:02 libthumbnail.la
-rw-r--r-- 1 root root  39208 2007-08-22 00:02 libthumbnail.so
-rw-r--r-- 1 root root  16550 2007-08-22 00:09 libtrailfocus.a
-rw-r--r-- 1 root root    995 2007-08-22 00:08 libtrailfocus.la
-rw-r--r-- 1 root root  15308 2007-08-22 00:09 libtrailfocus.so
-rw-r--r-- 1 root root  15328 2007-08-28 20:21 libvideo.so
-rw-r--r-- 1 root root  35680 2007-08-28 20:36 libvisualevent.so
-rw-r--r-- 1 root root  14972 2007-08-22 00:02 libvpswitch.a
-rw-r--r-- 1 root root    981 2007-08-22 00:02 libvpswitch.la
-rw-r--r-- 1 root root  14664 2007-08-22 00:02 libvpswitch.so
-rw-r--r-- 1 root root  64230 2007-08-22 00:02 libwall.a
-rw-r--r-- 1 root root   1026 2007-08-22 00:02 libwall.la
-rw-r--r-- 1 root root  18432 2007-08-28 20:36 libwallpaper.so
-rw-r--r-- 1 root root  60516 2007-08-22 00:02 libwall.so
-rw-r--r-- 1 root root  22560 2007-08-28 20:21 libwater.so
-rw-r--r-- 1 root root  17856 2007-08-22 00:09 libwidget.a
-rw-r--r-- 1 root root    967 2007-08-22 00:08 libwidget.la
-rw-r--r-- 1 root root  17256 2007-08-22 00:09 libwidget.so
-rw-r--r-- 1 root root   9090 2007-08-22 00:02 libwinrules.a
-rw-r--r-- 1 root root    981 2007-08-22 00:02 libwinrules.la
-rw-r--r-- 1 root root  11016 2007-08-22 00:02 libwinrules.so
-rw-r--r-- 1 root root  25600 2007-08-28 20:21 libwobbly.so
-rw-r--r-- 1 root root  13676 2007-08-22 00:02 libworkarounds.a
-rw-r--r-- 1 root root   1002 2007-08-22 00:02 libworkarounds.la
-rw-r--r-- 1 root root  12844 2007-08-22 00:02 libworkarounds.so
-rw-r--r-- 1 root root  15200 2007-08-28 20:21 libzoom.so




> holder@holder-laptop:~$ sudo dpkg -l | egrep "decor|compiz"
Password:
ii  beryl                                      0.3.0+git20070324~3v1ubuntu4           Compositing window manager, decorator and th
ii  compiz                                     0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070817-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2-0ubuntu2~ppa1                    Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unofficial           0.0.2~git20070828+3v1ubuntu0           Collection of UNOFFICIAL fusion plugins for 
ii  compiz-gnome                               0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070828+3v1ubuntu0           OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070814-0ubuntu1~ppa1        Compiz configuration settings manager
ii  libberyldecoration0                        0.3.0+git20070324~3v1ubuntu4           Settings library for plugins - Beryl Project
ii  libcompizconfig-backend-gconf              0.5.2+git20070813-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2-0ubuntu1~ppa2                    Settings library for plugins - OpenCompositi
ii  libdecoration0                             0.5.5~git20070828+3v1ubuntu0           Compiz window decoration library
ii  python-compizconfig                        0.5.2-0ubuntu1~ppa1                    Compiz configuration system bindings




Really thanks for helping, I don't know what i could do without this forum.

---

### Post by michael37 on 2007-08-31
> **Holder said:**
> 
Really thanks for helping, I don't know what i could do without this forum.

From what I see, your compiz is configured perfectly, and ccp plugin should load.  If it still doesn't load (run compiz -v --replace), you gotta tell us what exactly you tried to do -- download compiz from source, tried to build it, etc.  It  seems that you have some rogue versions of compiz and/or compiz libraries that is interfering with your new repository install.  That rogue version didn't get uninstalled using apt-get remove -purge.

---

### Post by Holder on 2007-09-01
What i have trying to do is to put a shell on my desktop following this guide:
[http://ubuntuforums.org/showthread.php?t=535027](http://ubuntuforums.org/showthread.php?t=535027)

it scrwed me up.

---

### Post by michael37 on 2007-09-01
> **Holder said:**
> What i have trying to do is to put a shell on my desktop following this guide:
[http://ubuntuforums.org/showthread.php?t=535027](http://ubuntuforums.org/showthread.php?t=535027)

it scrwed me up.

Hmm. Perhaps you should ask in that thread since I have no idea how to uninstall the "shell on desktop" feature.  I don't use this option myself.

Meanwhile, my best recommendation is following instructions in this post:

[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)

---

### Post by Holder on 2007-09-02
T-H-A-N-K     Y-O-U!

After all, it worked out! Thank you dude, you saved me :-)

---

### Post by michael37 on 2007-09-02
Glad to help!  Please mark the thread SOLVED

:popcorn:

---

