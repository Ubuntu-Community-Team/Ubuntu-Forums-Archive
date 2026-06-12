---
title: "Magic Jack DOES work in ubuntu.. happy days!!"
date: 2009-03-31
forum: General Help
---

### Post by bsskibum on 2009-03-31
Successfully setup Ubuntu Linux + VMWare + XP + MagicJack

I was using a dedicated XP box for MagicJack and I have a 24x7 server running ubuntu so I decided to give it a try and was able to move MagicJack to my Ubuntu box successfully.

Here are what I did, hope it will help others like me who don't want a dedicated XP running just for MagicJack.

I started with an existing Ubuntu server install that does not have GUI.

Install GUI and VNC:
Downsize the system:
- sudo vi /etc/default/linux-restricted-modules-common:
DISABLED_MODULES="ath_hal fc fglrx ltm nv"

Install the X11 bare bone:
- sudo aptitude install x-window-system-core
- sudo aptitude install xorg
- sudo aptitude install fluxbox fluxconf #lightwight windows manager
- sudo aptitude install dillo #lightweight browser
- sudo aptitude install xfe #lightweight file manager

Change /etc/X11/xorg.conf:
- sudo dpkg-reconfigure xserver-xorg #guided setup
- manual edit /etc/X11/xorg.conf (use "gtf 1024 768 60" to obtain the Modeline values):

Section "Monitor"
Identifier "KDS k717s" #This is my monitor
HorizSync 31-80
VertRefresh 60-75
# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "KDS k717s"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
EndSection

Starting X:
- use startx
- Virtual console F7 is the x window (display :0)

Install X11vnc:
- sudo aptitude install x11vnc

Start vnc:
- startx
- x11vnc --forever &

Connect to server remotely via vnc:
- vncviewer host:0

By now, I got a light GUI Ubuntu box that can be accessed remotely via VNC.

Setup VMWare:
Get the kernel header:
- sudo apt-get install linux-headers-$(uname -r)

Then run the vmware-install.pl as root

Then run the vmware-config.pl (install will prompt to run this)

If you receive compilation error when run vmware-config.pl like this:
include/asm/bitops_32.h:9:2: error: #error only can be included directly, and vmmon-only compile failes
The solution is: change line 74 in vmmon-only source file to read: #include “linux/bitops.h”
Steps:
cd /usr/lib/vmware/modules/source
cp vmmon.tar vmmon.tar.orig
sudo tar xvf vmmon.tar
cd vmmon-only/include/
sudo vi vcpuset.h
change line 74 from: #include “asm/bitops.h” to: #include “linux/bitops.h”
rm vmmon.tar (return to the folder where you decompressed the tar file)
sudo tar cvf vmmon.tar vmmon-only/
sudo rm -rf vmmon-only/

Then re-run: sudo vmware-config.pl

After this I have a working vmware that can be launched by "vmware".

Guest XP OS install:
You would need to install and activate your XP Guest OS. I already have a VMware image so this is skipped.

Detect MagicJack USB devices:
I was initially having problem detecting the MagicJack USB devices. I did two things that fixed it:
1. Make sure the XP virtual machine has the USB Controller in the hardware list
2. Check that the vmx file of the virtual machine has:
usb.present = "TRUE"
usb.generic.skipsetconfig = "TRUE"
The second line is missing in my vmx file and I had to manually add it.

After this, I rebooted the guest XP OS and re-plug in the MagicJack. XP detected both devices properly and started its installation. After that the MagicJack is up and running and I was able to make calls.

Cheers!

BTW, I was posting this to the unofficialmagicjack forum but keep getting "Method Not Implemented, POST to /posting.php not supported." error when submit the post - tried 3 different browsers.

---

### Post by sdowney717 on 2009-06-15
A Linux version will be out 3rd quarter this year
good news for sure

[http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010](http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010)

---

### Post by SubCool on 2009-06-19
VNC is not making magic jack work in Ubuntu

They maybe releasing soon- but why isnt it out already?
its just a sip?
the IPHONE has it working- 
Im forced to install a XP box just to hack it and steal it for my iphone.
Thats kinda sad... there has to be something else
I saw that EKIGA has it working- but u have to hack it first to make it work on ubuntu.

---

