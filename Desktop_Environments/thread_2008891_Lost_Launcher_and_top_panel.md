---
title: "Lost Launcher and top panel"
date: 2012-06-23
forum: Desktop Environments
---

### Post by robincarter on 2012-06-23
I'm running Ubuntu 12.04.  I've lost the Launcher and the narrow panel that used to be at the top of the display showing time etc. I've tried changing the display resolution without effect.

---

### Post by Frogs Hair on 2012-06-23
Hello and Welcome 

Login to Ubuntu and use Ctrl + Alt + F1 to enter TTY. Next, enter user name, password, and run the following command.

Code:
unity --reset

Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu and see what happens.

---

### Post by robincarter on 2012-06-23
It worked!  Thanks for your help!

---

### Post by Frogs Hair on 2012-06-23
Great ! Use the thread tools and mark as solved.

---

### Post by sebinbenjamin on 2012-06-25
Pls Help !!!

I got the same problem and I tried unity --reset

Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x26000b4

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2e00337

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
compiz (core) - Warn: unhandled ConfigureNotify on 0x1a00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x1a00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
Initializing animation options...done
Initializing annotate options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing cube options...done
Initializing decor options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing grid options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing mag options...done
Initializing neg options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing screenshot options...done
Initializing shift options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing thumbnail options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing water options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Setting Update "main_menu_key"
Setting Update "run_key"

I'm using Ubuntu 12.04....

---

### Post by zombifier25 on 2012-06-25
Reinstall Unity and see if it helps.
```
sudo apt-get install --reinstall unity
```

---

### Post by sebinbenjamin on 2012-06-25
I tried, but still not working......

---

### Post by sebinbenjamin on 2012-06-25
hopefully gnome classic works !
Something wrong with unity(also unity 2D).

---

### Post by Frogs Hair on 2012-06-25
You may have had a Compiz segmentation fault  which would have been listed at the and of the output  .  The reset should take about two minutes and not 5 hours. Try the following in TTY .```
sudo gconftool --recursive-unset /apps/compiz-1
```Here is another command to reset the Compiz configuration if the first fails . ```
sudo gconftool --recursive-unset /apps/compizconfig-1
```Unity 2D and 3D are not completely independent of each other.

---

### Post by sebinbenjamin on 2012-06-25
sudo gconftool --recursive-unset /apps/compiz-1  gave no output, cursor just blinked for a few seconds.

sudo gconftool --recursive-unset /apps/compizconfig-1 - This code was quick.

But I still have no launcher & top panels in unity

---

### Post by Frogs Hair on 2012-06-26
Try the unity reset command again , but check support for unity with the following first. ```
/usr/lib/nux/unity_support_test -p
```

---

### Post by sebinbenjamin on 2012-06-26
/usr/lib/nux/unity_support_test -p  gives the following errors....

/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

what does that mean ?

---

### Post by sebinbenjamin on 2012-06-26
[HTML]http://ubuntuforums.org/showthread.php?t=1974219[/HTML] looks similar......

---

### Post by zombifier25 on 2012-06-26
> **Frogs Hair said:**
> You may have had a Compiz segmentation fault  which would have been listed at the and of the output  .  The reset should take about two minutes and not 5 hours. Try the following in TTY .```
sudo gconftool --recursive-unset /apps/compiz-1
```Here is another command to reset the Compiz configuration if the first fails . ```
sudo gconftool --recursive-unset /apps/compizconfig-1
```Unity 2D and 3D are not completely independent of each other.

Doesn't running the command using sudo reset root's config and not your own's?

---

### Post by Frogs Hair on 2012-06-27
> **zombifier25 said:**
> Doesn't running the command using sudo reset root's config and not your own's?

The commands restore defaults just as unity --reset does in the Unity plugin. I don't know the cause of the error with the support test. What graphics card and driver are in use . ```
lspci
```

---

### Post by sebinbenjamin on 2012-06-27
zombifier25 : I am not sure about that. 

I have ATI Radeon 5670 and I use ATI/AMD proprietary FGLRX graphics driver. 

At the time this happened, I was using the Intel core i5 inbuilt graphics (I was just checking it out). I have not installed any driver for it.

---

### Post by sebinbenjamin on 2012-06-27
lspci gives this output 
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood [Radeon HD 5670]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
02:01.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```

---

### Post by sebinbenjamin on 2012-06-27
After reading the other post, I simply tried installing Linux kernel image for version 3.2.0-25( I had 3.2.0-24 earlier) and somehow I got back unity !!

I think Unity had actually been reset with unity--reset as I have launchers for many programs which I have not placed, and the settings are defaults.

Thanks for all the help and support...

---

### Post by nlneilson on 2012-07-04
I tried everything in this thread and several others, nothing worked.

I am dumping 12.04 and will reinstall.

---

### Post by jlapinski4 on 2012-07-11
I am having this same issue. Does unity --reset take a while to complete?

---

