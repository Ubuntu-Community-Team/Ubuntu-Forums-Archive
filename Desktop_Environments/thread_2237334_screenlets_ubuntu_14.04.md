---
title: "screenlets ubuntu 14.04"
date: 2014-08-01
forum: Desktop Environments
---

### Post by frankyboynl on 2014-08-01
hello, i installed the screenlets-themepack, but none of the screenlets seemed to be working..


grtz, Frank

---

### Post by Frogs Hair on 2014-08-01
Can you provide a link to what you installed ? Unfortunately many Screenlets have not been maintained for years and won't work on newer versions of Ubuntu so if installing from Gnome Look or other sources it is important to check when the Screenlet was last updated. I am seeing the screenlets-pack-all in the 14.04 software center and that would be the safest way to install.

---

### Post by frankyboynl on 2014-08-01
that was the one i installed, but when i click a screenlet, it doesnt work...



grtz, Frank

---

### Post by Frogs Hair on 2014-08-01
I will install the package and get back to you asap.

Edit: I installed screenlets and the screenlets-package-all . To get them working open the screenlets manager select the screenlet you would like to use and  check the start/stop box on the bottom left  and add the ones you want one by one . The install tab is for adding screenlets downloaded from other sources.

---

### Post by frankyboynl on 2014-08-01
I tried the following: 
sudo add-apt-repository ppa:noobslab/screenlets/


but it fails to load this repository


grtz, Frank

---

### Post by Frogs Hair on 2014-08-01
I installed from the 14.04 software center . I did notice a ppa @ Noobs Lab , but it is generally better to stick to the software center to avoid problems.

Install from the terminal : 

```
sudo apt-get install screenlets
``````
sudo apt-get install screenlets-pack-all
```

---

### Post by frankyboynl on 2014-08-01
that is exactly what I did, but they still dont work...


grtz, Frank

---

### Post by Frogs Hair on 2014-08-01
If you are checking start/stop box on the bottom left of the screenlets manager as I stated I don't what the problem would be. It is possible that if you are using the gnome flashback session with metacity the screenlets might not work but, I can't check that without installing the session.

---

### Post by frankyboynl on 2014-08-01
That is the problem, the start/stop checkbox is not available to choose, its grey and turned off.


grtz, Frank

---

### Post by Frogs Hair on 2014-08-01
The box only becomes active after a screenlet is selected. Select a screenlet and see if the box becomes active. If you have any stored configuration the reset screenlet config will be active and if not it will be inactive or grayed out. You can  try reseting the config if you have any stored from your attempts to getting the screenlets running.

---

### Post by frankyboynl on 2014-08-02
ok, I can select the start/stop box now, but I still am unable to start any screenlet...


grtz, Frank

---

### Post by Frogs Hair on 2014-08-02
Do you still have Plexydesk installed ? I'm thinking there might be a conflict if you do because both are widget managers.

---

### Post by frankyboynl on 2014-08-02
and where can I find this config file??

grtz, Frank

---

### Post by Frogs Hair on 2014-08-02
In many cases configuration files are stored in home/hidden folders . Open the home folder and press Ctrl +H . Screenlets is located in .config as for Plexydesk I have no idea.

---

### Post by frankyboynl on 2014-08-02
I deleted the .config directory, but still no go...


grtn, Frank

---

### Post by Frogs Hair on 2014-08-02
I hope you didn't delete the entire .config directory because it includes many folders. What graphics card/chip are you using?   

```
 lspci -v 
```

---

### Post by frankyboynl on 2014-08-02
```
frank@frank-K70IJ:~$  lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1862
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at dc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device 1862
    Flags: bus master, fast devsel, latency 0
    Memory at fe800000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at d800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fe9fbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Santa Cruz Operation Device 1043
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000bde00000-00000000bdffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe9fb800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 1867
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=8]
    I/O ports at c480 [size=4]
    I/O ports at c400 [size=32]
    Memory at fe9fb000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k

03:00.0 Ethernet controller: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device 14f5
    Physical Slot: 0
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ATL1E

frank@frank-K70IJ:~$
```

---

### Post by Frogs Hair on 2014-08-02
We have similar graphics with the same driver so I don't think that's a problem. Do you have the ccsm ( Compiz Configuration Settings Manager) installed ? I don't and I ask because it has widget settings. When I used Screenlets there was never a conflict with the ccsm  but that was back on 9.10 . ;)

---

### Post by frankyboynl on 2014-08-02
I uninstalled compiz settings manager, but I still get the same message...



grtz, Frank

---

### Post by Frogs Hair on 2014-08-02
> I still get the same message

What is the complete message ?  I found that some of the screenlets were incomparable, the ones i tried that worked were system monitor, Google Calendar, and clear weather.

---

### Post by frankyboynl on 2014-08-03
I typed message, what I meant was that still none of the screenlets are working..


grtz, Frank

ok I managed to install the newest version of screenlets, 1.7, but there are no screenlets to choose from. how do I download and install them?



thnx frank

finally I got it to work! when enabling my hdmi output with disper -c, suddenly the screenlets where working..


grtz and thanx, Frank

---

### Post by Dave_Carr on 2015-04-12
I've got Ubuntu 14.10 & have done every thing in this post & still no screenlets appear. :'(

My desktop environment is the default Unity desktop environment that installs with Ubuntu, My graphics card is an AMD Radeon HD6800 using the stock drivers that ships with Ubuntu 14.10.

Where am I going wrong here?

This is what happens when I run screenlets in a terminal session & try to get a screenlet to run:

```
dave@ASUS-P5GC-MX-PC:~$ screenlets
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:18: Unable to locate image file in pixmap_path: "images/panel/panel-normal.svg"
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:21: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:27: Unable to locate image file in pixmap_path: "images/panel/panel-active.svg"
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:30: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:61: error: invalid string constant "button", expected valid string constant
No GNOME keyring, there will be problems with account options
True
Starter already exists.
DAEMON FOUND!
True
True
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:18: Unable to locate image file in pixmap_path: "images/panel/panel-normal.svg"
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:21: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:27: Unable to locate image file in pixmap_path: "images/panel/panel-active.svg"
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:30: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:61: error: invalid string constant "button", expected valid string constant
REGISTER screenlet: DigitalClockScreenlet
True
Traceback (most recent call last):
  File "/usr/share/screenlets/screenlets-pack-all/DigitalClock/DigitalClockScreenlet.py", line 226, in <module>
    screenlets.session.create_session(DigitalClockScreenlet)
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 480, in create_session
    session.start()
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 254, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "/usr/share/screenlets/screenlets-pack-all/DigitalClock/DigitalClockScreenlet.py", line 71, in __init__
    screenlets.Screenlet.__init__(self, width=250, height=100, **keyword_args)
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 837, in __init__
    self.load_buttons(None)
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 1302, in load_buttons
    self.closeb = self.gtk_icon_theme.load_icon ("gtk-close", 16, 0)
glib.GError: Icon 'gtk-close' not present in theme
Logging output goes to: /home/dave/.config/screenlets/DigitalClockScreenlet.log
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:18: Unable to locate image file in pixmap_path: "images/panel/panel-normal.svg"
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:21: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:27: Unable to locate image file in pixmap_path: "images/panel/panel-active.svg"
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:30: Background image options specified without filename
/usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/widgets/panel.rc:61: error: invalid string constant "button", expected valid string constant
REGISTER screenlet: DigitalClockScreenlet
True
Traceback (most recent call last):
  File "/usr/share/screenlets/screenlets-pack-all/DigitalClock/DigitalClockScreenlet.py", line 226, in <module>
    screenlets.session.create_session(DigitalClockScreenlet)
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 480, in create_session
    session.start()
  File "/usr/lib/pymodules/python2.7/screenlets/session.py", line 254, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "/usr/share/screenlets/screenlets-pack-all/DigitalClock/DigitalClockScreenlet.py", line 71, in __init__
    screenlets.Screenlet.__init__(self, width=250, height=100, **keyword_args)
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 837, in __init__
    self.load_buttons(None)
  File "/usr/lib/pymodules/python2.7/screenlets/__init__.py", line 1302, in load_buttons
    self.closeb = self.gtk_icon_theme.load_icon ("gtk-close", 16, 0)
glib.GError: Icon 'gtk-close' not present in theme
```

---

### Post by luisgulo on 2015-07-14
To solve the problems of the images ( .svg ) you must create the necessary directory :
# cd /usr/share/themes/MBuntu-Y-For-Unity/gtk-2.0/
# mkdir -p images/panel

And then copied within 2 images needed from anywhere.
( For example you can download them from : [https://github.com/linuxmint/mint-themes/tree/master/usr/share/themes/Mint-X/gtk-2.0/images/panel](https://github.com/linuxmint/mint-themes/tree/master/usr/share/themes/Mint-X/gtk-2.0/images/panel) )

NOTE: Just in case I leave the 2 images included as attachments to the message


NOTE : Do it all as "root " to avoid permission problems .
------

The problem of error: panel.rc:61: error: invalid string constant "button"
I have not yet been solved :-(
-----------
Signed: Luis GuLo

:-D

The error line 61 ( and 62 ) is solved by changing the last 2 lines , it should look like:

# Panel Buttons
#widget_class " * Panel * GtkToggleButton " style : highest "button"
#widget_class " * Panel * GtkButton " style : highest "button"
widget_class " * Panel * GtkToggleButton " style : highest "panel"
widget_class " * Panel * GtkButton " style : highest "panel"

---

