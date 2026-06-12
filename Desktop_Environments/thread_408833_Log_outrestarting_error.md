---
title: "Log out/restarting error?"
date: 2007-04-13
forum: Desktop Environments
---

### Post by Vuddha on 2007-04-13
I've been using Ubuntu 6.10 for a couple of months now and really enjoying everything about it and open source.  (LyX word processor is the ultimate).

Over the past few days, my computer has been logging me out without warning.  I'll be browsing the internet with Firefox, and all of a sudden, the screen will go black and I'll be back at the login screen.  (I don't think it's restarting, just logging out).  

What's going on?  Why has this problem only occurred recently?  Is it a problem with Firefox?

Thanks for the help,

---

### Post by amohanty on 2007-04-13
Seems your xserver (the program that manages your GUI environment) is crashing. Next time that happens and you login, in a terminal type the following:

cat /var/log/Xorg.0.log | grep EE

and post the output here.

also post the output of the following:

dmesg | tail -n 100

AM

---

### Post by Zwalther on 2007-04-13
It sounds like your X-server is crashing. It might for instance be a bug in your graphics drivers. What are you doing in your browser? Is there any other pattern to it? Like websites with flash or movies? Did you install something new recently? Usually your X-server shouldn't crash while browsing the internet. 

If it's related to a specific version of your graphics drivers, browser of some browser-plugin, you could just wait a couple of days and upgrade to Feisty. That could solve the problem.

---

### Post by Vuddha on 2007-04-13
Wow, thanks for the detailed explanations.  I'm very proud to be a part of such a helpful community of computer users.  

I'm not doing anything specific in Firefox.  This last time I was reading the news (cbc.ca), but I had multiple tabs open (gmail, university website).  It usually occurs almost immediately  after logging in the first time (like today); however, it'll probably not occur again for the rest of the day.  (Maybe I should keep better track of this).  No flash or video, though.

I'm using a Dell D600.  Recently, I installed LyX, Opera, Pybliographer, gPhoto (and uninstalled it).  

Could it be due to Firefox?  If so, can I reinstall it?  Why would the xserver crash if I'm using Firefox?

Thanks for the help.

---

### Post by amohanty on 2007-04-14
Technically it should never crash because of firefox or because any of the apps you mention. 

Post the output of the commands the next time it behaves that way and we can know what might be going on.

AM

---

### Post by kalyp on 2007-04-18
I have exactly the same problem: logout without warning, usually when I click somewhere, not necessary while working on firefox.
Here is what I get, if this can give you any idea I'm interested ;-)
thank you!

cat /var/log/Xorg.0.log | grep EE

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): DRIScreenInit failed!
(EE) AIGLX: Screen 0 is not DRI capable

dmesg | tail -n 100

[   29.141410] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d5651c173cb]
[   29.728820] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   29.905326] usb 4-1: configuration #1 chosen from 1 choice
[   30.144522] usb 4-2: new low speed USB device using uhci_hcd and address 3
[   30.324023] usb 4-2: configuration #1 chosen from 1 choice
[   38.981430] ieee80211_crypt: registered algorithm 'NULL'
[   38.985243] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   38.985250] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   39.029534] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.033568] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.187667] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[   39.187674] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   39.187681] Driver 'ipw2200' needs updating - please use bus_type methods
[   39.187814] GSI 21 sharing vector 0x32 and IRQ 21
[   39.187821] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 50
[   39.188299] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   40.860113] usbcore: registered new driver hiddev
[   40.994240] input: PC Speaker as /class/input/input1
[   41.188526] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[   41.188595] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.3-1
[   41.205506] input: Logitech Logitech USB Keyboard as /class/input/input3
[   41.205524] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:10.3-2
[   41.250684] input: Logitech Logitech USB Keyboard as /class/input/input4
[   41.250763] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:10.3-2
[   41.250787] usbcore: registered new driver usbhid
[   41.250794] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   41.566206] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa0b1, caps: 0xa04713/0x20040a
[   41.607572] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   42.296242] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   42.296275] r8169 Gigabit Ethernet driver 2.2LK loaded
[   42.296319] GSI 22 sharing vector 0x3A and IRQ 22
[   42.296326] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 58
[   42.296473] eth1: Identified chip type is 'RTL8169s/8110s'.
[   42.296483] eth1: RTL8169 at 0xffffc20000078400, 00:03:0d:42:93:99, IRQ 58
[   42.297107] GSI 23 sharing vector 0x42 and IRQ 23
[   42.297113] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 66
[   42.297122] PCI: Via IRQ fixup for 0000:00:11.6, from 3 to 2
[   42.300428] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   42.349290] ts: Compaq touchscreen protocol output
[   42.809795] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 66
[   42.809808] PCI: Via IRQ fixup for 0000:00:11.5, from 3 to 2
[   42.809961] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   43.831288] lp: driver loaded but no devices found
[   43.907291] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   43.907299] ieee1394: sbp2: Try serialize_io=0 for better performance
[   43.941641] fuse init (API version 7.6)
[   44.038419] Adding 3911788k swap on /dev/hda5.  Priority:-1 extents:1 across:3911788k
[   44.095429] EXT3 FS on hda3, internal journal
[   44.468616] kjournald starting.  Commit interval 5 seconds
[   44.474957] EXT3 FS on hda2, internal journal
[   44.474967] EXT3-fs: mounted filesystem with ordered data mode.
[   44.478222] kjournald starting.  Commit interval 5 seconds
[   44.483046] EXT3 FS on hda7, internal journal
[   44.483055] EXT3-fs: mounted filesystem with ordered data mode.
[   44.485990] kjournald starting.  Commit interval 5 seconds
[   44.490984] EXT3 FS on hda6, internal journal
[   44.490993] EXT3-fs: mounted filesystem with ordered data mode.
[   44.754632] NET: Registered protocol family 17
[   49.310427] ACPI: AC Adapter [AC0] (on-line)
[   49.395549] ACPI: Battery Slot [BAT1] (battery present)
[   49.425889] ACPI: Power Button (FF) [PWRF]
[   49.425931] ACPI: Lid Switch [LID]
[   49.425944] ACPI: Sleep Button (CM) [SLPB]
[   49.425954] ACPI: Power Button (CM) [PWRB]
[   49.615526] ibm_acpi: ec object not found
[   49.659822] pcc_acpi: loading...
[   49.863680] ACPI: Video Device [PEG] (multi-head: yes  rom: no  post: no)
[   50.241460] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   50.242076] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[   50.242084] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
[   50.242091] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[   50.242291] cpu_init done, current fid 0x0, vid 0x16
[   62.016585] mtrr: no more MTRRs available
[   62.017110] mtrr: no more MTRRs available
[   62.017455] mtrr: no more MTRRs available
[   70.948639] r8169: eth0: link up
[   72.727666] NET: Registered protocol family 10
[   72.727914] lo: Disabled Privacy Extensions
[   72.728333] IPv6 over IPv4 tunneling driver
[   73.436054] Bluetooth: Core ver 2.8
[   73.436066] NET: Registered protocol family 31
[   73.436071] Bluetooth: HCI device and connection manager initialized
[   73.436106] Bluetooth: HCI socket layer initialized
[   73.521601] Bluetooth: L2CAP ver 2.8
[   73.521610] Bluetooth: L2CAP socket layer initialized
[   73.563158] Bluetooth: RFCOMM socket layer initialized
[   73.563198] Bluetooth: RFCOMM TTY layer initialized
[   73.563203] Bluetooth: RFCOMM ver 1.7
[   85.561351] eth1: no IPv6 routers present
[   94.259427] eth0: no IPv6 routers present
[21793.584314] hdc: irq timeout: status=0xd0 { Busy }
[21793.584330] ide: failed opcode was: unknown
[21793.584343] hdc: DMA disabled
[21793.692251] hdc: ATAPI reset complete
[38164.874913] mtrr: no more MTRRs available
[38164.875205] mtrr: no more MTRRs available
[38164.875383] mtrr: no more MTRRs available
[39274.510380] mtrr: no more MTRRs available
[39274.510670] mtrr: no more MTRRs available
[39274.510850] mtrr: no more MTRRs available

---

### Post by Zwalther on 2007-04-18
That error in your xorg log seems to suggest a problem with your videocard drivers. Apparently some program wants to use a 3D feature.
Can you try running glxgears and see if it crashes when you start that up?

You could try reconfiguring you xserver (type 'sudo dpkg-reconfigure xserver-xorg' but it might ask you some tough questions :) or look in the xorg log in the neighbourhood of those errors to see if more information shows up.

If you don't need 3D you can probably switch to an open source driver.

---

### Post by amohanty on 2007-04-19
In addition to Zwalther's suggestions also port the contents of your ~/.xsession-errors

AM

---

### Post by kalyp on 2007-04-19
thanks for your help!!

Zwalther: 
glxgears works but Xorg uses almost 100% CPU and I don't know if it's related, but my computer logged me out again soon after that (can't remember if I closed it or if is was still running).
Maybe I can try reconfiguring my xserver but I'm quite new in Linux so I'll have to find someone to help me ;-)
I don't think I need 3D, maybe an open source driver would be better, which one should I use?

amohanty:
cat .xsession-errors 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "monique"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/poisson:/tmp/.ICE-unix/13843
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Initializing nautilus-open-terminal extension
evolution-alarm-notify-Message: Setting timeout for 47109 1177052400 1177005291
evolution-alarm-notify-Message:  Fri Apr 20 00:00:00 2007

evolution-alarm-notify-Message:  Thu Apr 19 10:54:51 2007


(gnome-panel:13913): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 45
CalDAV Eplugin starting up ...

(evolution-2.8:14021): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.8:14021): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.8:14021): DEBUG: mailto URL command: evolution %s
** (evolution-2.8:14021): DEBUG: mailto URL program: evolution

(evolution-2.8:14021): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertion `GTK_IS_CHECK_MENU_ITEM (check_menu_item)' failed
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong ELF class: ELFCLASS32]
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong ELF class: ELFCLASS32]

---

### Post by amohanty on 2007-04-19
> LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong ELF class: ELFCLASS32]

Try uninstalling adobe acrobat and see if the logouts stop. If they do, uninstall mozilla-acroread completely

HTH
AM

---

### Post by kalyp on 2007-04-20
> **amohanty said:**
> Try uninstalling adobe acrobat and see if the logouts stop. If they do, uninstall mozilla-acroread completely

HTH
AM

hum ok I will try that... but when I go to 'applications' and 'add/remove', the adobe box is gray so I cannot unstall it this way. Is there another way? just remove or move /usr/lib/Adobe?
sorry I'm a beginner in linux (at least as root)...
thanks

---

### Post by amohanty on 2007-04-20
System->Administration->Synaptic

That is the main application repository. Think of it as the one place to download and install everything.
Enter your password when prompted for it. 

Then use the Search button to search for **mozilla-acroread**

Then right click on the entry and select Remove Completely.

Click on Apply and you are done.

HTH
AM

---

### Post by kalyp on 2007-04-20
thanks for your explanation!

well... Seems that mozilla-acoread is not installed on my computer???
I did exactly what you said and the search returns nothing.
adobe acrobat returns gpdf, libpdf-fdf-simple-perl, xpdf and a lot of related (xpdf-reader, xpdf-utils etc).

Should I try to uninstall all that?

---

### Post by amohanty on 2007-04-21
How about searching for **acro** when the selection underneath the text field if **Name**

AM

---

### Post by kalyp on 2007-04-23
only returns anacron, libapache2-mod-macro and xmacro...
PDF files open with Evince 0.6.1 so I'm not even sure acroread is installed on my computer.

---

### Post by amohanty on 2007-04-23
> LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: wrong ELF class: ELFCLASS32]


This tells me it is somewhere on your system. Try the following and post the output:

sudo locate -u
locate Acro*

Also:
> LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong ELF class: ELFCLASS32]

you may be having some trouble with your realplayer plugin. Did you install it by hand using the binary on real's website or did you use synaptic to install real player??

AM

---

### Post by kalyp on 2007-04-23
> **amohanty said:**
> This tells me it is somewhere on your system. Try the following and post the output:

sudo locate -u
locate Acro*



to summarize there are 2 directories: .adobe/Acrobat/7.0 in my home and /usr/lib/Adobe/Acrobat7.0.

locate Acro*
/home/mm/.adobe/Acrobat
/home/mm/.adobe/Acrobat/7.0
/home/mm/.adobe/Acrobat/7.0/UserCache.bin
/home/mm/.adobe/Acrobat/7.0/Preferences
/home/mm/.adobe/Acrobat/7.0/Preferences/Collab
/home/mm/.adobe/Acrobat/7.0/Preferences/Collab/Temp
/home/mm/.adobe/Acrobat/7.0/Preferences/Collab/Temp/CollabPROTOCOL_A_TO_B
/home/mm/.adobe/Acrobat/7.0/Preferences/Collab/Temp/CollabPROTOCOL_B_TO_A
/home/mm/.adobe/Acrobat/7.0/Preferences/Collab/Temp/TrackerPROTOCOL_A_TO_B
/home/mm/.adobe/Acrobat/7.0/Preferences/Collab/Temp/TrackerPROTOCOL_B_TO_A
/home/mm/.adobe/Acrobat/7.0/Preferences/Collab/RSS
/home/mm/.adobe/Acrobat/7.0/Preferences/reader_prefs
/home/mm/.adobe/Acrobat/7.0/Cache
/home/mm/.adobe/Acrobat/7.0/Cache/cookies.txt
/home/mm/.adobe/Acrobat/7.0/Cache/AcroFnt07.lst
/home/mm/.adobe/Acrobat/7.0/Cache/Search70
/home/mm/.adobe/Acrobat/7.0/Cert
/home/mm/.adobe/Acrobat/7.0/Cert/curl-ca-bundle.crt
/home/mm/.adobe/Acrobat/7.0/JavaScripts
/home/mm/.adobe/Acrobat/7.0/JavaScripts/glob.settings.js
/home/mm/.adobe/Acrobat/7.0/Dictionaries
/usr/lib/Adobe/Acrobat7.0
/usr/lib/Adobe/Acrobat7.0/Reader
/usr/lib/Adobe/Acrobat7.0/Reader/Messages
/usr/lib/Adobe/Acrobat7.0/Reader/Messages/ENU
/usr/lib/Adobe/Acrobat7.0/Reader/Messages/ENU/RdrMsgENU.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/Messages/RdrMsgSplash.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/help
/usr/lib/Adobe/Acrobat7.0/Reader/help/ENU
/usr/lib/Adobe/Acrobat7.0/Reader/help/ENU/ReadMe.htm
/usr/lib/Adobe/Acrobat7.0/Reader/help/ENU/Reader.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/AcroVersion
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Forms01.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Forms.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Forms02.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Hanko.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Hanko01.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Hanko02.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Hanko03.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Hanko04.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Hanko05.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo00.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo01.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo02.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo03.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo04.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo05.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo07.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/HowTo08.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review01.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review02.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review03.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review04.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review05.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review06.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review07.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review08.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review09.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review10.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review11.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review12.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review13.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review14.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review16.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review17.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review18.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review19.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review20.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review21.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review22.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review23.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Review28.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign02.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign04.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign06.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign07.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign09.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign11.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign13.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Sign05.html
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/addfile.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/1.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/2.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/3.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/4.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/5.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/6.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/7.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/8.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/attach_comment.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/areatool.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/arrow_nxt.ai
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/arrow_prev.ai
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/bkgrnd_art.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/attach.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/crossouttxt.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/bullet.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/distance.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/callout.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/touchupobj.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/tip.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/dimensionlinetool.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/distancetool.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/ebookonline.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/forms.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/handtool.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/highlighter.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/layerisvisible.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/listview.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/measure_loop.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/notes.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/obj_data.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/office_convert.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/office_email.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/office_review.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/perimeter.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/readebook.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/rectangle.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/replycomments.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/selecttext.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/sendemailreview.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/showmenu.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/snapshot.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/stamp.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/thumbnailview.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/C_UpOneLevel_Lg_N.png
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/underlinetxt.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/zoomintool.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/C_HelpGreenButton_Lg_N.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/Images/C_MoreTopics_Lg_N.gif
/usr/lib/Adobe/Acrobat7.0/Reader/HowTo/ENU/images
/usr/lib/Adobe/Acrobat7.0/Reader/Legal
/usr/lib/Adobe/Acrobat7.0/Reader/Legal/ENU
/usr/lib/Adobe/Acrobat7.0/Reader/Legal/ENU/license_ENU_uc.txt
/usr/lib/Adobe/Acrobat7.0/Reader/Legal/ENU/LGPL.html
/usr/lib/Adobe/Acrobat7.0/Reader/Legal/ENU/License.html
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Accessibility.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/SearchFind.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/EScript.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/AcroForm.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/AcroForm
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/AcroForm/acrobat7.xdc
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/checkers.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annotations
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annotations/Stamps
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annotations/Stamps/Words.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annotations/Stamps/ENU
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annotations/Stamps/ENU/SignHere.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annotations/Stamps/ENU/Dynamic.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annotations/Stamps/ENU/StandardBusiness.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Annots.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/LegalPDF.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/DigSig.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/EFS.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/MakeAccessible.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/PDDom.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/PPKLite.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/SaveAsRTF.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/SendMail.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/SOAP.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/Spelling.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/wwwlink.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/ewh.api
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/bin
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/bin/acroread
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libCoolType.so.5.01
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libACE.so.2.07
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libAGM.so.4.14
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libBIB.so.1.1
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libResAccess.so.0.1
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libJP2K.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libAXSLE.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/librt3d.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libAXE16SharedExpat.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libAXE8SharedExpat.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libadobelinguistic.so.2.0.0
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libcurl.so.2.0.2
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libssl.so.0.9.6
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libcrypto.so.0.9.6
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libaglcnv.so.28.0
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagli18n.so.28.0
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagluc.so.28.0
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagldata.so.28.0
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libWRServices.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libCoolType.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libACE.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libAGM.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libBIB.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagli18n.so.28
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libResAccess.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libcurl.so.2
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libcurl.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libssl.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libssl.so.0
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libcrypto.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libcrypto.so.0
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libaglcnv.so.28
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libaglcnv.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagldata.so.28
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagli18n.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagluc.so.28
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagluc.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libadobelinguistic.so.2
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libagldata.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/libldap.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/lib/liblber.so
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins3d
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins3d/3difr.x3d
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins3d/2d.x3d
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins3d/tesselate.x3d
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins3d/drvSOFT.x3d
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins3d/drvOpenGL.x3d
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/SPPlugins
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/SPPlugins/ADMPlugin.apl
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/res
/usr/lib/Adobe/Acrobat7.0/Reader/Cert
/usr/lib/Adobe/Acrobat7.0/Reader/Cert/curl-ca-bundle.crt
/usr/lib/Adobe/Acrobat7.0/Reader/JavaScripts
/usr/lib/Adobe/Acrobat7.0/Reader/JavaScripts/JSByteCodeLin.bin
/usr/lib/Adobe/Acrobat7.0/Reader/JavaScripts/WebSearch.js
/usr/lib/Adobe/Acrobat7.0/Reader/WebSearch
/usr/lib/Adobe/Acrobat7.0/Reader/WebSearch/WebSearchENU.pdf
/usr/lib/Adobe/Acrobat7.0/Reader/Patch
/usr/lib/Adobe/Acrobat7.0/Reader/Patch/selinux_patch
/usr/lib/Adobe/Acrobat7.0/Reader/GlobalPrefs
/usr/lib/Adobe/Acrobat7.0/Reader/GlobalPrefs/reader_prefs
/usr/lib/Adobe/Acrobat7.0/bin
/usr/lib/Adobe/Acrobat7.0/bin/acroread
/usr/lib/Adobe/Acrobat7.0/Resource
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/LanguageNames
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/LanguageNames/DisplayLanguageNames.en_US.txt
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/brt04.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/brt0401.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/brt0402.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/brt32.clx
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/brtphon.env
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/can129.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/can32.clx
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/canphon.env
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/eng32.clx
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/engphon.env
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/usa86.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/usa03.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/usa8601.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/usa8602.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/usa8603.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Linguistics/Providers/Proximity/usa8604.lex
/usr/lib/Adobe/Acrobat7.0/Resource/Font
/usr/lib/Adobe/Acrobat7.0/Resource/Font/CourierStd-Bold.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/CourierStd.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/AdobePiStd.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/PFM
/usr/lib/Adobe/Acrobat7.0/Resource/Font/PFM/SY______.PFM
/usr/lib/Adobe/Acrobat7.0/Resource/Font/PFM/zx______.pfm
/usr/lib/Adobe/Acrobat7.0/Resource/Font/PFM/zy______.pfm
/usr/lib/Adobe/Acrobat7.0/Resource/Font/CourierStd-BoldOblique.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/CourierStd-Oblique.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/SY______.PFB
/usr/lib/Adobe/Acrobat7.0/Resource/Font/ZX______.PFB
/usr/lib/Adobe/Acrobat7.0/Resource/Font/ZY______.PFB
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MinionPro-BoldIt.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MinionPro-Bold.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MinionPro-Regular.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MinionPro-It.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MyriadPro-BoldIt.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MyriadPro-Bold.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MyriadPro-Regular.otf
/usr/lib/Adobe/Acrobat7.0/Resource/Font/MyriadPro-It.otf
/usr/lib/Adobe/Acrobat7.0/Resource/CMap
/usr/lib/Adobe/Acrobat7.0/Resource/CMap/Identity-H
/usr/lib/Adobe/Acrobat7.0/Resource/CMap/Identity-V
/usr/lib/Adobe/Acrobat7.0/Resource/Icons
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/16x16
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/16x16/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/16x16/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/16x16/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/16x16/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/16x16/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/20x20
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/20x20/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/20x20/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/20x20/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/20x20/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/20x20/xdp.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/24x24
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/24x24/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/24x24/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/24x24/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/24x24/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/24x24/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/32x32
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/32x32/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/32x32/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/32x32/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/32x32/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/32x32/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/36x36
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/36x36/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/36x36/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/36x36/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/36x36/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/36x36/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/48x48
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/48x48/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/48x48/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/48x48/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/48x48/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/48x48/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/64x64
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/64x64/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/64x64/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/64x64/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/64x64/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/64x64/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/96x96
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/96x96/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/96x96/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/96x96/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/96x96/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/96x96/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/128x128
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/128x128/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/128x128/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/128x128/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/128x128/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/128x128/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/192x192
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/192x192/vnd.adobe.pdx.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/192x192/AdobeReader.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/192x192/vnd.adobe.xfdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/192x192/vnd.fdf.png
/usr/lib/Adobe/Acrobat7.0/Resource/Icons/192x192/vnd.adobe.xdp+xml.png
/usr/lib/Adobe/Acrobat7.0/Resource/Support
/usr/lib/Adobe/Acrobat7.0/Resource/Support/vnd.adobe.pdx.desktop
/usr/lib/Adobe/Acrobat7.0/Resource/Support/AdobeReader.xml
/usr/lib/Adobe/Acrobat7.0/Resource/Support/vnd.fdf.desktop
/usr/lib/Adobe/Acrobat7.0/Resource/Support/vnd.adobe.xdp+xml.desktop
/usr/lib/Adobe/Acrobat7.0/Resource/Support/vnd.adobe.xfdf.desktop
/usr/lib/Adobe/Acrobat7.0/Browser
/usr/lib/Adobe/Acrobat7.0/Browser/intellinux
/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so


> **amohanty said:**
> Also:


you may be having some trouble with your realplayer plugin. Did you install it by hand using the binary on real's website or did you use synaptic to install real player??



I didn't install it. The computer is from "linux certified" and almost everything was installed when I received it.
Should I try to reinstall it? I can see it in Synaptic and seems to be installed.

---

### Post by amohanty on 2007-04-24
Lets try and remove the offending applications ans see if it works:
IN a terminal try:

sudo rm -rf $(locate Acro*)

Then fire up synaptic and look for realplayer or real or helix and uninstall it if its installed. 

See if that helps.

AM

---

### Post by kalyp on 2007-04-24
ok done, thanks.
realplayer, real and helix returned nothing installed.
Now I'm waiting for the next bug and if it occurs again, I'll tell you...
thanks a lot!

---

### Post by amohanty on 2007-04-24
If real did not return anything, it may be the same problem as acrobat, its there but not installed properly. so do a :

locate helix
and if all of them are helix (its the open source version - so to speak of real), the go ahead and do the:

sudo rm -rf $(locate helix)

HTH
AM

---

### Post by kalyp on 2007-04-24
ok... just did it (uninstall helix, adobe already uninstalled, locate helix and locate Acro* returns nothing).
... and there was another logout 5 mins ago...

Here is the xsession-errors:

cat ~/.xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "monique"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/poisson:/tmp/.ICE-unix/9623
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Initializing nautilus-open-terminal extension
evolution-alarm-notify-Message: Setting timeout for 53671 1177484400 1177430729
evolution-alarm-notify-Message:  Wed Apr 25 00:00:00 2007

evolution-alarm-notify-Message:  Tue Apr 24 09:05:29 2007


(gnome-panel:9694): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 45
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

xEmbed supported in this Mozilla version
Gtk2+ supported in this Mozilla version
NewStream: The full URL is [http://mail.google.com/mail/im/sound.swf](http://mail.google.com/mail/im/sound.swf)
Starting process: /usr/bin/gnash -v -x 46139236 -j 1 -k 1 -u [http://mail.google.com/mail/im/sound.swf](http://mail.google.com/mail/im/sound.swf) -U [http://mail.google.com/mail/?view=page&name=gp&ver=sh3fib53pgpk&auto=1](http://mail.google.com/mail/?view=page&name=gp&ver=sh3fib53pgpk&auto=1) -P id=bzfsh -P pluginspage=http://www.macromedia.com/go/getflashplayer -P quality=high -P src=im/sound.swf -P style=position: absolute; top: 1px; left: 1px; height: 1px; width: 1px; -P type=application/x-shockwave-flash - 
Forked sucessfully, child process PID is 9830
09:05:41: Verbose output turned on
09:05:41: Setting width to: 1
09:05:41: Setting height to: 1
09:05:41: Setting root URL to: [http://mail.google.com/mail/im/sound.swf](http://mail.google.com/mail/im/sound.swf)
09:05:41: Setting base URL to: [http://mail.google.com/mail/?view=page&name=gp&ver=sh3fib53pgpk&auto=1](http://mail.google.com/mail/?view=page&name=gp&ver=sh3fib53pgpk&auto=1)
09:05:41: no rendering flags specified, using rcfile
09:05:41: OpenGL extension version - 1.2
09:05:41: Got double-buffered visual.
09:05:41: Created XEmbedded window
09:05:41: Couldn't find pixmap file: gnash_128_96.ico

** (gnash:9830): WARNING **: Couldn't find pixmap file: gnash_128_96.ico
09:05:41: WARNING: Resize request received while there's still no movie loaded, can't correctly set movie scale
09:05:41: WARNING: Resize request received while there's still no movie loaded, can't correctly set movie scale
09:05:41: Base url set to: [http://mail.google.com/mail/?view=page&name=gp&ver=sh3fib53pgpk&auto=1](http://mail.google.com/mail/?view=page&name=gp&ver=sh3fib53pgpk&auto=1)
09:05:41: WARNING: SWF8 is not fully supported, trying anyway but don't expect it to work
09:05:41: ERROR:   FIXME: tagtype = 69
09:05:41: Add sound sample 1

---

### Post by amohanty on 2007-04-24
Post the output of 

dmesg | tail -n 100 

the enxt time you get logged out. X may not be the reason here.

AM

---

### Post by kalyp on 2007-04-24
Well it wasn't long...
Here is what I get:

dmesg | tail -n 100 

[   43.151796] EXT3 FS on hda2, internal journal
[   43.151805] EXT3-fs: mounted filesystem with ordered data mode.
[   43.155171] kjournald starting.  Commit interval 5 seconds
[   43.161430] EXT3 FS on hda7, internal journal
[   43.161439] EXT3-fs: mounted filesystem with ordered data mode.
[   43.164337] kjournald starting.  Commit interval 5 seconds
[   43.169461] EXT3 FS on hda6, internal journal
[   43.169472] EXT3-fs: mounted filesystem with ordered data mode.
[   44.140577] usb 4-2: new low speed USB device using uhci_hcd and address 3
[   44.320527] usb 4-2: configuration #1 chosen from 1 choice
[   44.340551] input: Logitech Logitech USB Keyboard as /class/input/input4
[   44.340602] input: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:10.3-2
[   44.384566] input: Logitech Logitech USB Keyboard as /class/input/input5
[   44.384693] input: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:10.3-2
[   45.404141] NET: Registered protocol family 10
[   45.404321] lo: Disabled Privacy Extensions
[   45.404585] IPv6 over IPv4 tunneling driver
[   48.454372] ACPI: AC Adapter [AC0] (on-line)
[   48.535557] ACPI: Battery Slot [BAT1] (battery present)
[   48.566135] ACPI: Power Button (FF) [PWRF]
[   48.566177] ACPI: Lid Switch [LID]
[   48.566188] ACPI: Sleep Button (CM) [SLPB]
[   48.566198] ACPI: Power Button (CM) [PWRB]
[   48.751563] ibm_acpi: ec object not found
[   48.798609] pcc_acpi: loading...
[   48.990380] ACPI: Video Device [PEG] (multi-head: yes  rom: no  post: no)
[   49.376659] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   49.377324] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[   49.377332] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
[   49.377339] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[   49.377541] cpu_init done, current fid 0x0, vid 0x16
[   61.002364] mtrr: no more MTRRs available
[   61.002922] mtrr: no more MTRRs available
[   61.003282] mtrr: no more MTRRs available
[   64.956551] eth0: no IPv6 routers present
[   71.936498] Bluetooth: Core ver 2.8
[   71.936509] NET: Registered protocol family 31
[   71.936514] Bluetooth: HCI device and connection manager initialized
[   71.936550] Bluetooth: HCI socket layer initialized
[   72.021964] Bluetooth: L2CAP ver 2.8
[   72.021974] Bluetooth: L2CAP socket layer initialized
[   72.064002] Bluetooth: RFCOMM socket layer initialized
[   72.064042] Bluetooth: RFCOMM TTY layer initialized
[   72.064047] Bluetooth: RFCOMM ver 1.7
[   91.861119] eth0: no IPv6 routers present
[ 3847.583570] mtrr: no more MTRRs available
[ 3847.583948] mtrr: no more MTRRs available
[ 3847.584136] mtrr: no more MTRRs available
[ 4841.005922] mtrr: no more MTRRs available
[ 4841.006213] mtrr: no more MTRRs available
[ 4841.006397] mtrr: no more MTRRs available
[ 5342.984482] mtrr: no more MTRRs available
[ 5342.984789] mtrr: no more MTRRs available
[ 5342.984974] mtrr: no more MTRRs available
[28334.110877] usb 5-3: new high speed USB device using ehci_hcd and address 4
[28334.412412] usb 5-3: configuration #1 chosen from 1 choice
[28334.639898] usbcore: registered new driver libusual
[28334.696402] Initializing USB Mass Storage driver...
[28334.697290] scsi2 : SCSI emulation for USB Mass Storage devices
[28334.697672] usb-storage: device found at 4
[28334.697677] usb-storage: waiting for device to settle before scanning
[28334.697700] usbcore: registered new driver usb-storage
[28334.697707] USB Mass Storage support registered.
[28345.938273] usb-storage: device scan complete
[28346.018730]   Vendor: MAXTOR 6  Model: L040J2            Rev: A93.
[28346.018759]   Type:   Direct-Access                      ANSI SCSI revision: 00
[28346.197833] SCSI device sda: 78177791 512-byte hdwr sectors (40027 MB)
[28346.200159] sda: Write Protect is off
[28346.200166] sda: Mode Sense: 03 00 00 00
[28346.200171] sda: assuming drive cache: write through
[28346.205589] SCSI device sda: 78177791 512-byte hdwr sectors (40027 MB)
[28346.207984] sda: Write Protect is off
[28346.207993] sda: Mode Sense: 03 00 00 00
[28346.208009] sda: assuming drive cache: write through
[28346.208306]  sda: sda1
[28346.236408] sd 2:0:0:0: Attached scsi disk sda
[28346.278253] sd 2:0:0:0: Attached scsi generic sg0 type 0
[35405.104159] usb 5-3: USB disconnect, address 4
[35534.830720] usb 5-3: new high speed USB device using ehci_hcd and address 5
[35535.134389] usb 5-3: configuration #1 chosen from 1 choice
[35535.135273] scsi3 : SCSI emulation for USB Mass Storage devices
[35535.135492] usb-storage: device found at 5
[35535.135497] usb-storage: waiting for device to settle before scanning
[35548.069357] usb-storage: device scan complete
[35549.229831]   Vendor: LaCie     Model: BigDisk           Rev:     
[35549.229870]   Type:   Direct-Access                      ANSI SCSI revision: 00
[35549.265833] SCSI device sda: 1953546336 512-byte hdwr sectors (1000216 MB)
[35549.268150] sda: Write Protect is off
[35549.268161] sda: Mode Sense: 10 00 00 00
[35549.268167] sda: assuming drive cache: write through
[35549.272626] SCSI device sda: 1953546336 512-byte hdwr sectors (1000216 MB)
[35549.274860] sda: Write Protect is off
[35549.274871] sda: Mode Sense: 10 00 00 00
[35549.274877] sda: assuming drive cache: write through
[35549.274890]  sda: sda1
[35549.338018] sd 3:0:0:0: Attached scsi disk sda
[35549.338133] sd 3:0:0:0: Attached scsi generic sg0 type 0
[40374.005100] mtrr: no more MTRRs available
[40374.005391] mtrr: no more MTRRs available
[40374.005577] mtrr: no more MTRRs available

---

### Post by amohanty on 2007-04-24
Everything looks good here. 
Sorry man, that's pretty much the end of my knowledge pool. I would suggest re-installing on the system, but since you bought it as a linux certified system, you could try contacting the vendor.

AM

---

### Post by kalyp on 2007-04-24
ok...
thanks for your efforts anyway!!
It really seems to be linked to firefox and maybe Xorg (not sure but I think these logout only occur when firefox is running, and I often see Xorg reaching more than 50% CPU in that case), I may try another web browser instead or just limit its use...
If I find something, I'll tell you!

thanks again....

---

### Post by amohanty on 2007-04-24
Look at the help.ubuntu.org site. Reinstalling is not all that hard :)

AM

---

### Post by kalyp on 2007-04-30
Hi amohanty,

Just in case you're interested in knowing how it ended: I wrote to linux certified and they told me to install linux-restricted-modules-2.6.17-11-generic to use the ATi fglrx video driver module as the open source driver doesn't fully support the video card on my computer... (I think there was no way to guess it!!)
Now it seems to work, no more logout so far...

thanks again for your help.

---

### Post by amohanty on 2007-04-30
Aaah! That ones a really hard one to catch, I think because everybody assumes that if you are usign fglrx, you already have the restricted modules installed. Good to know for next time.

Thanks.
AM

---

