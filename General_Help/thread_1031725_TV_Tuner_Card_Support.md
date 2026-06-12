---
title: "TV Tuner Card Support"
date: 2009-01-05
forum: General Help
---

### Post by fdepinto on 2009-01-05
I bought an HP computer a few months ago.  It has Vista on it and Ubuntu 8.10 now.  

The computer came with a TV tuner card installed.  It's the last thing that I need Vista for, but I'd love to dump Vista all together.  I don't know the make/model number of the TV tuner card, but before I get started on this project, is there any hope at all that this card will work in Ubuntu?  Ubuntu doesn't seem to see the card, and what about software - is that available?

Thanks in advance.

---

### Post by sendblink23 on 2009-01-05
> **fdepinto said:**
> I bought an HP computer a few months ago.  It has Vista on it and Ubuntu 8.10 now.  

The computer came with a TV tuner card installed.  It's the last thing that I need Vista for, but I'd love to dump Vista all together.  I don't know the make/model number of the TV tuner card, but before I get started on this project, is there any hope at all that this card will work in Ubuntu?  Ubuntu doesn't seem to see the card, and what about software - is that available?

Thanks in advance.


Download TVtime.. through:
Applications
Add/Remove..
Show: All available Packages
Search: Tvtime

Afterwards.. test the new application *Applications / Sound & Video - "TVtime".. to see if it automatically detects.. your tvcard, that worked for me

---

### Post by fdepinto on 2009-01-05
> **sendblink23 said:**
> Download TVtime.. through:
Applications
Add/Remove..
Show: All available Packages
Search: Tvtime

Afterwards.. test the new application *Applications / Sound & Video - "TVtime".. to see if it automatically detects.. your tvcard, that worked for me

No good.  I installed the application, but it just says "No Signal" and "No Video Source."

---

### Post by oldos2er on 2009-01-05
Can you post the output of the command "lspci"?

---

### Post by fdepinto on 2009-01-05
> **oldos2er said:**
> Can you post the output of the command "lspci"?

frank@frank-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
frank@frank-desktop:~$
frank@frank-desktop:~$

---

### Post by mosimea on 2009-01-05
In the US?  You probably need to get IVTV working.  I've got a Hauppauge PVR-150 working great.  Here is a how-to page to help:

[https://help.ubuntu.com/community/Install_IVTV_Troubleshooting]("https://help.ubuntu.com/community/Install_IVTV_Troubleshooting")

I stream it via Totem and change channels with CSMonkey remote:

[http://tvremote.csmonkey.com]("http://tvremote.csmonkey.com")

---

### Post by saedelaere on 2009-01-06
And here is an alternative application to use with ivtv, [TV-Viewer]("http://ubuntuforums.org/showthread.php?t=763698").

Regards
Saedelaere

---

### Post by fragos on 2009-01-06
The line of lspci output your interested in is:

03:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series

The following URL taakes you to the manufacturers page:

[http://www.vixs.com/sections/products/xcode_2100/xcode_2100.htm](http://www.vixs.com/sections/products/xcode_2100/xcode_2100.htm)

I'm aware of two drivers that cover perhaps all TV cards - bttv and ivtv. The driver should have been loaded automatically for you. We can determine that by running "lsmod |gerp tv" in a terminal window. You should see either "bttv" or "ivtv" in the output. I will assume you have an attenna or cable hookup connected to your PC. Tvtime would have worked with little muss or fuss with a bttv driver. I suspect you have an ivtv supported card. Most tv viewer applications only support bttv. The following is a link to an TV viewer package that was mentioned above:

[http://home.arcor.de/saedelaere/info_eng.html](http://home.arcor.de/saedelaere/info_eng.html)

I've no experience with that viewer but it appears to be simpler than the normal ivtv alternative "mythtv" which can be installed from the standard Ubuntu repositories. Mythtv is very full featured.

---

### Post by ttilberg on 2009-11-18
I believe I have this same device, and am having a heck of a time getting it to function.

lspci:
02:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series


I've installed the ivtv-utils package and did modprobe ivtv -- it shows up in dmesg:

lsmod:
ivtv                  141924  0 
i2c_algo_bit            5760  1 ivtv
cx2341x                13440  1 ivtv
v4l2_common            17500  2 ivtv,cx2341x
videodev               36736  2 ivtv,v4l2_common
tveeprom               11872  1 ivtv

dmesg:
[  958.093790] ivtv: Start initialization, version 1.4.1
[  958.093825] ivtv: End initialization



But there isn't a line in dmesg that says something about registering the device at /dev/video0... That makes me think these are not the right drivers... Any hints?

Thanks,
Tim

---

### Post by fragos on 2009-11-18
Web cams for example are also mounted as video devices and the assignment of /dev/video{#} is inconsistent between boots. I have 2 TV cards and a web cam. In order to get consistent mounting I had to add the following UDEV rules as 50-video.rules in /etc/udev/rules.d:

KERNEL=="video*", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYSFS{name}=="ivtv0 encoder MPEG", SYMLINK+="video/pvr150"
KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/bttv"
KERNEL=="video*", SYSFS{vendor}=="0x046d", SYSFS{device}=="0x092e", SYMLINK+="video/webcam"

---

### Post by monkeybritt on 2009-11-19
i use ivtv with an asus ivtv6 card with cable input in karmic and how i get it to work is dmesg to make sure its working sometimes i have to restart.
open pvr in vlc and use ivtv-tune --channel= to tune channels.

---

### Post by deltron30 on 2009-11-22
I have an Asus PHC1-300 which has the ViXS Systems, Inc. XCode 2100 Series chip in it. I tried installing the IVTV drivers but when I do lsmod | grep tv I don't get any response. I've tried mythtv but it doesn't recognize the card. In Win 7 media center it recognizes it right away and works perfectly. I don't want to use windows 7 and hate having to boot into it to watch tv. Has anyone been able to get this chipset to work on linux? I can't find anything about it anywhere online. Help would be much appreciated.

---

### Post by fragos on 2009-11-22
If the tuner device is recognized the driver should be loaded for you by the system. I assume you're talking about a PCI card and not USB. I couldn't find any information on a PHC1-300 but did find a PHC3-100 on the ASUS site. IVTV would seem to be the correct driver since that card has hardware MPEG2 support. The only support committed was that for the Windows world. That doesn't mean it won't work in Linux but my concern is that the card may not have been recognized. It could be that the IVTV driver doesn't support your your card. Hauppauge cards that use the BTTV or IVTV drivers do reliably work with Ubuntu.

---

### Post by ekips on 2010-09-28
Hello,

I have a similar card in my system, and I was hoping to install MythBuntu or just simply Ubuntu with some other software to control the capture card in my Gateway Desktop.  I have installed the ivtv drivers as well, but that didn't seem to work as the drivers aren't loaded (lsmod|grep tv returns nothing).


Here is the information for my card:

02:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series
        Subsystem: ASUSTeK Computer Inc. Device 48b8
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at d0000000 (64-bit, prefetchable) [size=1M]
        Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at <unassigned>
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [60] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Virtual Channel <?>


Has anyone had any luck with these cards in Ubuntu?  Does anyone know why there is so little support in the Linux world for them?


I really don't want to have to install Windows to use this device...


Thank you!

---

