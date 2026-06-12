---
title: "ubuntu GUI doesnt start on boot up"
date: 2009-05-27
forum: General Help
---

### Post by hyperion_X on 2009-05-27
hey,
whenever i boot up ubuntu, the login screen doesnt appear. the cursor that is supposed to be present at login screen appears with a busy sign, but the screen is black. i pressed alt+ctr+F4 and could login to text mode. please, could anyone tell me how to login to the graphical mode?

In reference to [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=1152800&highlight=login+screen]("http://ubuntuforums.org/showthread.php?t=1152800&highlight=login+screen")[/COLOR]

INFO: I was messing with the users access control and other log in methods along with adding a user and deleting one, when inadvertently after a reboot I got the same problem that person had... After following through on all 4 pages, Im not sure as to what else can be done to fix the problem?

---

### Post by utnubuuser on 2009-05-27
Login recovery mode and select xfix.

Can you have a look at /var/log/Xorg.0.log to see if any errors are posted?> less   /var/log/Xorg.0.log

---

### Post by hyperion_X on 2009-05-28
> **utnubuuser said:**
> Login recovery mode and select xfix.

Not to sure what the xfix is? I went into the boot screen and found 3 different recovery modes, none of them listed the xfix, and then tried it in terminal but got bash didnt recognize it returned?:confused:

---

### Post by gradinaruvasile on 2009-05-28
In the terminal the command is 

You could try doing a disk check from the recovery menu and reboot.

In the terminal the command to reconfigure the x server is
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by hyperion_X on 2009-05-29
> **gradinaruvasile said:**
> In the terminal the command is 

You could try doing a disk check from the recovery menu and reboot.

In the terminal the command to reconfigure the x server is
sudo dpkg-reconfigure -phigh xserver-xorg

Thank you mexican sombrero hat :p 

In order to fully try this I need to identify my gaphics card

As the argail1980 stated ```
sudo lshw
``` does the trick, however its going across my screen so fast I cant read any of it and haven't had any luck with using something such as **break sudo lshw**, Im confused as to what command I use in order to break the page?

---

### Post by utnubuuser on 2009-05-29
xfix is accessed by rebooting, selecting recovery.  A options window should open offering several actions, xfix is the fourth or fifth option.

---

### Post by hyperion_X on 2009-05-29
> **utnubuuser said:**
> xfix is accessed by rebooting, selecting recovery.  A options window should open offering several actions, xfix is the fourth or fifth option.

not sure if im in the right spot or not? [IMG]http://e.deviantart.com/emoticons/a/animesweat.gif[/IMG]
 

[IMG]http://i245.photobucket.com/albums/gg54/BM55_2003/IMG_1120.jpg?t=1243653798[/IMG]

---

### Post by wanderingtux on 2009-05-29
Yep, you are in the right place - select recovery mode and follow the screen prompts. One of the options that will come up is xfix. 

Keep a note of the file that xfix backs up your current xorg.conf to. It should be saved as  /etc/X11/xorg.conf.<date>

When the login screen is showing the busy cursor, on an alternate tty type the following

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start

Let me know what happens.

If the above fails, could you post the contents of your xorg.conf here?

---

### Post by hyperion_X on 2009-06-02
> **utnubuuser said:**
> Login recovery mode and select xfix.

Can you have a look at /var/log/Xorg.0.log to see if any errors are posted?

```
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!


```

---

### Post by hyperion_X on 2009-06-02
> **wanderingtux said:**
> Yep, you are in the right place - select recovery mode and follow the screen prompts. One of the options that will come up is xfix. 

Keep a note of the file that xfix backs up your current xorg.conf to. It should be saved as  /etc/X11/xorg.conf.<date>

This is what happens when i select the recovery

[[IMG]http://i245.photobucket.com/albums/gg54/BM55_2003/th_MVI_1124.jpg[/IMG]](http://s245.photobucket.com/albums/gg54/BM55_2003/?action=view&current=MVI_1124.flv)

> **wanderingtux said:**
> When the login screen is showing the busy cursor, on an alternate tty type the following
[B]
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start[/B]

```
@blackmagic:~$ sudo /etc/init.d/gdm stop
Password:
 * Stopping GNOME Display Manager...                                     [ OK ]
@blackmagic:~$ sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
@blackmagic:~$ sudo /etc/init.d/gdm start
 * Starting GNOME Display Manager...                                     [ OK ]
@blackmagic:~$


```

> **wanderingtux said:**
> Let me know what happens.

If the above fails, could you post the contents of your xorg.conf here?

will update you on the /etc/X11/xorg.conf file in a few EDIT: next page

---

### Post by hyperion_X on 2009-06-02
> **hyperion_X said:**
> 

will update you on the /etc/X11/xorg.conf file in a few

```
:/etc/X11$ sudo more xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by wanderingtux on 2009-06-03
BTW - do you really have a stylus attached to the system or is the entry about "wacom" spurious?

To find the hardware on your system use 

$sudo lshw | less

This should allow you to scroll through the listing.

Your video card does not seem to be recognized here - so the output of lshw is important

Also, check the existence of 

/usr/share/fonts/* and the permissions of the directories underneath

What permissions did you change when you were trying out the steps mentioned in the earlier post? Did you change permissions or install any programs as suggested by the earlier post?

What you might also want to do is compare the Xorg.0.log with the oldest Xorg log available - that might give you some pointers given that you had a working system earlier.

---

### Post by hyperion_X on 2009-06-08
> **wanderingtux said:**
> BTW - do you really have a stylus attached to the system or is the entry about "wacom" spurious?

To find the hardware on your system use 

$sudo lshw | less

This should allow you to scroll through the listing.

Your video card does not seem to be recognized here - so the output of lshw is important

Also, check the existence of 

/usr/share/fonts/* and the permissions of the directories underneath

What permissions did you change when you were trying out the steps mentioned in the earlier post? Did you change permissions or install any programs as suggested by the earlier post?

What you might also want to do is compare the Xorg.0.log with the oldest Xorg log available - that might give you some pointers given that you had a working system earlier.

lshw | less output

```
@blackmagic:~$ lshw | less
blackmagic
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 1
          size: 446MB
     *-cpu
          product: AMD Sempron(tm) Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 6
          bus info: cpu@0
          version: 15.15.0
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x
86-64 3dnowext 3dnow up lahf_lm ts fid vid ttp cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
 vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
   bus info: pci@00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@00:03.0
      version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: C51G [GeForce 6100]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          size: 256MB
          width: 64 bits
          clock: 66MHz
          capabilities: vga bus_master cap_list
          configuration: latency=0
          resources: iomemory:fb000000-fbffffff iomemory:d0000000-dfffffff iomemory:fc000000-fcffffff irq:10
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
    vendor: nVidia Corporation
          physical id: a
          bus info: pci@00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: ioport:1c00-1c3f ioport:1c40-1c7f irq:10
       product: OHCI Host Controller
             vendor: Linux 2.6.20-17-generic ohci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 2.06
             capabilities: usb-1.10
             configuration: driver=hub maxpower=0mA slots=8 speed=12.0MB/s
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fe02e000-fe02e0ff irq:19
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 2.6.20-17-generic ehci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 2.06
             capabilities: usb-2.00
             configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3
          resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:f400-f40f
        *-ide:0
             description: IDE Channel 0
   physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-disk
                product: WDC WD800JB-00JJC0
                vendor: Western Digital
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                capacity: 74GB
        *-ide:1
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-cdrom
                product: ATAPI-CD ROM-DRIVE-56MAX
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                capabilities: packet
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@00:0e.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list scsi-host
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: ioport:9f0-9f7 ioport:bf0-bf3 ioport:970-977 ioport:b70-b73 ioport:e000-e00f iomemory:fe02d000-fe02dfff irq:17
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@00:10.0

     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@00:0a.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: iomemory:fe02f000-fe02ffff irq:16
        *-usbhost
   version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
     *-multimedia
          description: Multimedia audio controller
          product: MCP51 AC97 Audio Controller
          vendor: nVidia Corporation
          physical id: 10.2
          bus info: pci@00:10.2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
          resources: ioport:dc00-dcff ioport:d800-d8ff iomemory:fe02c000-fe02cfff irq:16
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@00:14.0
          logical name: eth0
          version: a1
          serial: 00:e0:4c:eb:ad:82
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=192.168.1.106 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: iomemory:fe02b000-fe02bfff ioport:d400-d407 irq:18
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
 version: a1
          serial: 00:e0:4c:eb:ad:82
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=forcedeth driverversion=0.59 ip=192.168.1.106 latency=0 maxlatency=20 mingnt=1 multicast=yes
          resources: iomemory:fe02b000-fe02bfff ioport:d400-d407 irq:18
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz




```

FILE PERMISSIONS 
/usr/share/fonts/*

```
@blackmagic:/usr/share/fonts$ ls -l
total 12
drwxr-xr-x 23 root root 4096 2007-04-15 06:53 truetype
drwxr-xr-x  3 root root 4096 2007-04-15 06:51 type1
drwxr-xr-x  8 root root 4096 2007-04-15 06:53 X11

```

Here is what I was messing with when I Killed linux :(

[IMG]http://d.yimg.com/kq/groups/22888687/hr/311462/name/oh+crap.jpg[/IMG]

I was adding another user, but then ended up getting into stuff I didnt know much about, or So I thought I did, I do recall messing with something about a remote login feature.

---

### Post by wanderingtux on 2009-06-09
ok...when you get the ubuntu timer on the blank login screen try this

Press ALT+F2
Login
$sudo /etc/init.d/gdm stop
$ startx

Does this bring up an X Session? If yes, then go into System > Administration > Login Window

If remote login is enabled on the "Remote" tab, disable it.

Go to the "Users" tab and click on "Include all users from /etc/passwd" if not already checked.

Uncheck "Enable Automatic Login" and "Enable Timed Login" on the "Security" tab.

Does that make any difference?

Another thing you could try is edit the following lines in your Xorg.conf 

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:5:0"
EndSection

TO

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
EndSection

and restart X.

---

### Post by hyperion_X on 2009-06-11
> **wanderingtux said:**
> ok...when you get the ubuntu timer on the blank login screen try this

Press ALT+F2
Login
$sudo /etc/init.d/gdm stop
$ startx

Does this bring up an X Session? If yes, then go into System > Administration > Login Window

If remote login is enabled on the "Remote" tab, disable it.

Go to the "Users" tab and click on "Include all users from /etc/passwd" if not already checked.

Uncheck "Enable Automatic Login" and "Enable Timed Login" on the "Security" tab.

Does that make any difference?

Another thing you could try is edit the following lines in your Xorg.conf 

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:5:0"
EndSection

TO

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
EndSection

and restart X.

 ```
@blackmagic:/etc/init.d$ sudo startx
xauth:  creating new authority file /home/username/.serverauth.5746

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux blackmagic 2.6.20-17-generic #2 SMP Wed Aug 20 16:47:34 UTC 2008 i686
Build Date: 13 June 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 11 12:31:02 2009
(==) Using config file: "/etc/X11/xorg.conf"

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

The previous thread I mentioned did this, this was my fear, but I wasnt exactly sure how to check this out, By the way I have no idea what the wacom stuff is, I may have installed it a while back trying to experiment with things, but who knows :). 

Im going to say that this *is* the problem, I guess my next step should be looking at ways to restore the driver.....

(thanks for everyones help BTW)

---

### Post by wanderingtux on 2009-06-12
You might want to check this link out

[http://www.x.org/wiki/FAQErrorMessages](http://www.x.org/wiki/FAQErrorMessages)

Replace the original lines in the xorg.conf before you try out the above.

I believe you have the wrong lines for the fixed fonts in xorg.conf

---

### Post by hyperion_X on 2009-06-21
> **wanderingtux said:**
> You might want to check this link out

[http://www.x.org/wiki/FAQErrorMessages](http://www.x.org/wiki/FAQErrorMessages)

Replace the original lines in the xorg.conf before you try out the above.

I believe you have the wrong lines for the fixed fonts in xorg.conf

This may take some time, ill go through each check list and get back with you.

thanks

---

### Post by hyperion_X on 2009-07-23
> **wanderingtux said:**
> You might want to check this link out

[http://www.x.org/wiki/FAQErrorMessages](http://www.x.org/wiki/FAQErrorMessages)

Replace the original lines in the xorg.conf before you try out the above.

I believe you have the wrong lines for the fixed fonts in xorg.conf


Whoa **** it started! :D:D:D:D:D

good news first: I ran this ```
sudo startx -- :1
```

this took me to some what of a default desktop

bad news: the GUI still doesnt boot when starting up :( (still reading the x.org wiki)

---

