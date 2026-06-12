---
title: "Epson 3200 Scanner and Compro TV Card"
date: 2009-05-12
forum: General Help
---

### Post by Mad_Max_1412 on 2009-05-12
Guys,

My system has a Compro TV Card installed and I also have a Epson 3200 Scanner attached.

Prior to upgrading to 9.04, whenever I went to run the Xsane image scanning program, it used to bring up a dialogue box asking which of the 3 inputs I was using for scanning.  None really said anything close to "Epson Scanner", and one usually was the TV Card, but I could guess which one out of the other two options to select.  The point was that I was able to scan.  As for using the TV card, using Kaffiene etc, it was a nightmare and I never really got it working, even after following heaps of different thread suggestions.

Anyway, I've now upgraded to 9.04 and I went to use XSane for the first time and it didn't offer me any input choice. It does bring up a window for a brief time saying it's scanning for devices and then this dialogue box disappears. It then just says something along the lines of the Compro TV card in the title bar of the preview window.

I went to the help pull down menu of the Xsane program and chose "Available Backends" and it brings up a web browser window with the address of "file:///usr/share/doc/xsane-common/html/sane-backends-doc.html" which reads "File “/usr/share/doc/xsane-common/html/sane-backends-doc.html” not found.  Check the location of the file and try again."

I've done a reboot with the scanner turned on and now it just says (in the title bar of the preview window of Xsane) "UNKNOWN/GENERIC:video 0".

How do I get Ubuntu to re-scan all devices?  Is this what I have to do?  I would love the scanner program to just see the scanner.  BTW, when I open Kaffiene, it doesn't even give me the option of TV so it doesn't see the Compro TV tuner.

**** The following is not required for the above fault, just me expressing my frustration ******

I would love to get both the TV Tuner and Scanner working, but the scanner is more important at the moment.  I really would like to migrate over to Ubuntu totally without needing to rely on Windows, but sometimes it's things like this that make it hard for a beginner.  I'm not wanting to start a flame war about Windows vs Ubuntu, but I have to say that I usually don't have much problem installing peripherals in a Windows system and getting them running.

I like Epson's scanner software for the part that allows me to use the negative holders and scan up to 12 negatives at once, but I can't seem to find anything like this for Ubuntu.  I have written to Epson saying they should offer more support to users other than Windows and Macs.

As for the TV card, I know that makers of the card have drivers and the application programs which makes using it in Windows easy.  I would just love to see the day when I can install a TV card into a Ubuntu system, drivers are either automatically installed or the makers offer a Ubuntu driver, and a front end application for recording shows recognises the appropriate card.

**** End of rant  ****

Any help in getting the scanner working would be great.

---

### Post by Mad_Max_1412 on 2009-05-14
Bump

---

### Post by dandnsmith on 2009-05-14
When you 'upgraded to 9.04' did you re-install all the software (including the Xsane package) or just do some upgrade-in-place?

When I started using SANE, some years back, I remember using command-line stuff to work out what devices could be seen by the sane processes, and then putting in place a configuration set of options to use my scanner - is it possible that this has been done for yours, and the upgrade is using info which is hindering the process?

I think I found out quite a bit of the detail from Man and Info pages, together with the sane modules documents.

---

### Post by Mad_Max_1412 on 2009-05-16
I just did the upgrade in place. ie just used the Update Manager and accepted the defaults to the questions

---

### Post by Mad_Max_1412 on 2009-05-21
Guys,

I un-installed XSane and reinstalled it and it still sees the only peripheral as being the Compro TV card.

How can I get it to see my scanner again?

---

### Post by AlexDudko on 2009-05-21
Try to start xsane as a root user.

---

### Post by Mad_Max_1412 on 2009-05-22
Thank you.  I am a newbie so I had to do a little research to find out how to do this, but worked out that I needed to type "sudo xsane" in a terminal window and accept the warning message.

This bought up the dialogue box saying it had 3 devices.  These were:

Noname  Compro Videomate Virtual Device [v4l:/dev/video0]
Epson   GT-9800   Flatbed Scanner   [epson2:/dev/sg2]
Epson   GT-9800   Flatbed Scanner   [epson:/dev/sg2]

Selecting either of the last 2 made the scanner work.

I then closed XSane and then re-opened it from the menu (ie not as Root) thinking that it now knows about the scanner, but it only opened straight up thinking the TV card was the only device.

Am I now forced to always start Xsane from a terminal as root, or is there some configuration file I can change so it only sees the scanner?

Thanks

---

### Post by AlexDudko on 2009-05-22
Now as a sudo open in your favorite text editor (gedit, for instance) > /lib/udev/rules.d/50-udev-default.rules
just type in terminal:
> sudo gedit /lib/udev/rules.d/50-udev-default.rules
and edit the section:
> # libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0664"
there you should change > MODE="0664"
to
> MODE="0666"
so that the section would look like:
> # libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"
After that save the file and restart the system. I hope then you'll be able to use your scanner as any user.

---

### Post by Mad_Max_1412 on 2009-05-24
Hi,

Thanks for your reply. Unfortunately changing this to 0666 and a reboot hasn't changed anything.  (I wonder if the 666 is an omen :-)  )

Anyway, here's the entire document in case there is something else that needs to be modified:

[QUOTE]
# do not edit this file, it will be overwritten on update
# initramfs:default

SUBSYSTEM=="block", SYMLINK+="block/%M:%m"
SUBSYSTEM!="block", SYMLINK+="char/%M:%m"

KERNEL=="pty[pqrstuvwxyzabcdef][0123456789abcdef]", GROUP="tty", MODE="0660"
KERNEL=="tty[pqrstuvwxyzabcdef][0123456789abcdef]", GROUP="tty", MODE="0660"
KERNEL=="ptmx",			GROUP="tty", MODE="0666"
KERNEL=="tty",			GROUP="tty", MODE="0666"
KERNEL=="tty[0-9]*",		GROUP="tty", MODE="0620"
KERNEL=="vcs|vcs[0-9]*|vcsa|vcsa[0-9]*", GROUP="tty"
KERNEL=="console",		MODE="0600"

# serial
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*", GROUP="dialout"
KERNEL=="ppp",			MODE="0600"
KERNEL=="mwave",		NAME="modems/mwave", GROUP="dialout"
KERNEL=="hvc*|hvsi*",		GROUP="dialout"

# mem
KERNEL=="null|zero|full|random|urandom", MODE="0666"
KERNEL=="mem|kmem|port|nvram",	GROUP="kmem", MODE="0640"

# input
KERNEL=="mouse*|mice|event*",	NAME="input/%k", MODE="0640"
KERNEL=="ts[0-9]*|uinput",	NAME="input/%k", MODE="0640"
KERNEL=="js[0-9]*",		NAME="input/%k", MODE="0644"

# video4linux
SUBSYSTEM=="video4linux",	GROUP="video"
KERNEL=="vttuner*",		GROUP="video"
KERNEL=="vtx*|vbi*",		GROUP="video"
KERNEL=="winradio*",		GROUP="video"

# graphics
KERNEL=="agpgart",		MODE="0600", GROUP="video"
KERNEL=="card[0-9]*",		NAME="dri/%k"
KERNEL=="pmu",			GROUP="video"
KERNEL=="nvidia*|nvidiactl*",	GROUP="video"
SUBSYSTEM=="graphics",		GROUP="video"
SUBSYSTEM=="drm",		GROUP="video"

# DVB (video)
SUBSYSTEM=="dvb", ENV{DVB_ADAPTER_NUM}=="?*", NAME="dvb/adapter$env{DVB_ADAPTER_NUM}/$env{DVB_DEVICE_TYPE}$env{DVB_DEVICE_NUM}", GROUP="video"
SUBSYSTEM=="dvb", ENV{DVB_ADAPTER_NUM}=="", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter%%i/%%s $${K%%%%.*} $${K#*.}'", NAME="%c", GROUP="video"

# Firewire
KERNEL=="dv1394[0-9]*",		NAME="dv1394/%n", GROUP="video"
KERNEL=="video1394[0-9]*",	NAME="video1394/%n", GROUP="video"

# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"

# printer
KERNEL=="parport[0-9]*",	GROUP="lp"
SUBSYSTEM=="printer",		KERNEL=="lp*", GROUP="lp"
SUBSYSTEM=="ppdev",		GROUP="lp"
SUBSYSTEM=="usb",		KERNEL=="lp*", NAME="usb/%k", SYMLINK+="usb%k", GROUP="lp"
KERNEL=="lp[0-9]*",		GROUP="lp"
KERNEL=="irlpt[0-9]*",		GROUP="lp"

# block
SUBSYSTEM=="block", GROUP="disk"

# floppy
KERNEL=="fd[0-9]", GROUP="floppy"
KERNEL=="fd[0-9]", ACTION=="add", ATTRS{cmos}=="?*", RUN+="create_floppy_devices -c -t $attr{cmos} -m %M -M 0640 -G floppy $root/%k"
KERNEL=="hd*", SUBSYSTEMS=="ide", ATTRS{media}=="floppy", OPTIONS+="all_partitions"

# cdrom
SUBSYSTEM=="block", KERNEL=="sr[0-9]*", SYMLINK+="scd%n", GROUP="cdrom"
SUBSYSTEM=="block", KERNEL=="hd*", SUBSYSTEMS=="ide", ATTRS{media}=="cdrom", GROUP="cdrom"
SUBSYSTEMS=="scsi", ATTRS{type}=="4|5", GROUP="cdrom"
KERNEL=="pktcdvd[0-9]*", NAME="pktcdvd/%k", GROUP="cdrom"
KERNEL=="pktcdvd", NAME="pktcdvd/control", GROUP="cdrom"

# tape
KERNEL=="ht[0-9]*|nht[0-9]*", GROUP="tape"
KERNEL=="pt[0-9]*|npt[0-9]*|pht[0-9]*", GROUP="tape"
SUBSYSTEMS=="scsi", ATTRS{type}=="1|8", GROUP="tape"

# block-releated
KERNEL=="sch[0-9]*", GROUP="disk"
SUBSYSTEMS=="scsi", ATTRS{type}=="0", GROUP="disk"
KERNEL=="pg[0-9]*", GROUP="disk"
KERNEL=="qft[0-9]*|nqft[0-9]*|zqft[0-9]*|nzqft[0-9]*|rawqft[0-9]*|nrawqft[0-9]*", GROUP="disk"
KERNEL=="rawctl", NAME="raw/rawctl", GROUP="disk"
SUBSYSTEM=="raw", KERNEL=="raw[0-9]*", NAME="raw/%k", GROUP="disk"
SUBSYSTEM=="bsg", NAME="bsg/%k"
SUBSYSTEM=="aoe", NAME="etherd/%k", GROUP="disk", MODE="0220"
SUBSYSTEM=="aoe", KERNEL=="err", MODE="0440"

# network
KERNEL=="tun",			NAME="net/%k", MODE="0666"

# CPU
KERNEL=="cpu[0-9]*",		NAME="cpu/%n/cpuid"
KERNEL=="msr[0-9]*",		NAME="cpu/%n/msr"
KERNEL=="microcode",		NAME="cpu/microcode", MODE="0600"

# miscellaneous
KERNEL=="fuse",			MODE="0666"
SUBSYSTEM=="rtc", DRIVERS=="rtc_cmos", SYMLINK+="rtc"
KERNEL=="auer[0-9]*",		NAME="usb/%k"
KERNEL=="hw_random",		NAME="hwrng"
KERNEL=="mmtimer",		MODE="0644"
KERNEL=="rflash[0-9]*",		MODE="0400"
KERNEL=="rrom[0-9]*",		MODE="0400"
KERNEL=="sxctl",		NAME="specialix_sxctl"
KERNEL=="rioctl",		NAME="specialix_rioctl"
KERNEL=="iowarrior[0-9]*",	NAME="usb/%k"
KERNEL=="hiddev[0-9]*",		NAME="usb/%k"
KERNEL=="legousbtower[0-9]*",	NAME="usb/%k"
KERNEL=="dabusb[0-9]*",		NAME="usb/%k"
KERNEL=="usbdpfp[0-9]*",	NAME="usb/%k"
KERNEL=="cpad[0-9]*",		NAME="usb/%k"

# do not delete static device nodes
ACTION=="remove", NAME=="?*", TEST=="/lib/udev/devices/$name", OPTIONS+="ignore_remove"
ACTION=="remove", NAME=="", TEST=="/lib/udev/devices/%k", OPTIONS+="ignore_remove"
[UNQUOTE]

PS I don't know why, but most of the icons in the top of the message box (eg Bold, Italic, Quote, etc) don't seem to work either using Swiftweasel or Firefox so I've put [QUOTE] [UNQUOTE] manually which is why it hasn't put it into a quote box. (even though both words in square brackets were typed capitalised, it has posted the first word in lower case - weird.)

Thanks

---

### Post by Mad_Max_1412 on 2009-06-23
Guys,

Any further suggestions?

It's a little annoying to have to remember to run a terminal window and "sudo xsane" rather than just select it from the menu.

BTW, I did a scan of a document which I was going to later print out.  I saved the file as a JPG and when I went to open it, it said "Failed to open input stream for file".  The icon had a padlock in the top right corner and a cross in the bottom right corner.  I then did another scan as a PNG and I had the same issue. Not sure if it's because XSane was started as root.  I ended up doing the scan and sending it straight to the printer.

---

### Post by AlexDudko on 2009-06-23
Your saved scans belong to the root user. To be able to open and edit them you must permissions or user and permissions.

---

### Post by Mad_Max_1412 on 2009-07-08
So how do I change permissions so that I can copy, move, edit etc the scanned graphic?

++ Edit ++ for those who find this thread searching for the answer, I found out that I had to use a terminal window, navigate to the directory where the pictures were and use the command

sudo chmod 744 'filename'

++ End of Edit ++

And more importantly, how do I fix Ubuntu so I don't need to use SUDO to be able to "see" the scanner?

---

### Post by Mad_Max_1412 on 2009-08-16
I've removed my scanner card and thought that XSane should just see the scanner now, but it comes up with no devices.

I still have to use "Sudo Xsane" for it to see the scanner.

Any ideas or do I need to grab a new Live CD of the latest distro and reformat my system?

---

### Post by Mad_Max_1412 on 2009-08-26
BUMP

Hi Guys,

Any suggestions on how to resolve this issue so I don't have to start Xsane using the Sudo command?

Thanks in advance

---

