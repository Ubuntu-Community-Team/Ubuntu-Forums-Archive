---
title: "22&quot; Widescreen Problems"
date: 2007-05-10
forum: Desktop Environments
---

### Post by daengbo on 2007-05-10
I ordered "The Perfect Ubuntu Desktop" for my gal to do her graphics work on with all hardware well supported by OS drivers, but I'm having real trouble getting the widescreen resolution correct. The monitor is a TopSync 22" widesceen LCD.
I've searched the forums and also Google, coming up with five different methods, none of which worked.
> This is the recommended procedure:
• Download the 915resolution tool:
&#8728; aptitude install 915resolution
• Tweak the video BIOS:
&#8728; 915resolution 5a 1680 1050 32
• Add the resolution to the Xorg configuration file:
&#8728; cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak0
&#8728; sed 's/\(1280x1024\)/1680x1050 \1/g' </etc/X11/xorg.conf >/etc/X11/xorg.conf'{new}'
&#8728; mv /etc/X11/xorg.conf'{new}' /etc/X11/xorg.conf
• Restart the Xorg server (managed by gdm):
&#8728; /etc/init.d/gdm restart
• To make this behavior persist across reboots:
&#8728; cat <<EOT >/etc/default/915resolution
&#8227; MODE=5a
&#8227; XRESO=1680
&#8227; YRESO=1050
&#8227; BIT=32
&#8227; EOT
( from [http://grosskurth.ca/hardware/widescreen.html](http://grosskurth.ca/hardware/widescreen.html) )

Another Howto says:
• Install the 915resolution package. This package is in the universe repository.
• Make xorg use the i810 driver. I did this by executing sudo dpkg-reconfigure xserver-xorg  and answering all the questions, but you could also edit /etc/X11/xorg.conf by hand. Make sure that the "Device" section mentions the i810 driver.
• Turn off your X-server: Go to one of your text consoles (CTRL-ALT F1, e.g.), login and do a sudo /etc/init.d/x11-common stop.
• Ask 915resolution to give you the list of resolutions from your graphics card: sudo 915resolution -l. This will give you a list of that contains a mode number and a resolution on each line. Pick a resolution that you don't want to use and note the mode number.
• Edit the file /etc/default/915resolution. Enter the mode you noted in step 4 after MODE= and enter your x and y resolution in the corresponding lines.
• Reboot.
[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

Try:
  sudo xresprobe i810

One of the recommendations, to install the modesetting version of the i810 driver won't work on Feisty because it was removed just before the release.

Using the intel driver instead of i810 doesn't work under ANY resolution.

**uname -a**
Linux chiraporn-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

**915resolution -l**
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1680x1050, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1680x1050, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1680x1050, 24 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
These modes have been screwed with a little.

**lsmod**
Module                  Size  Used by
binfmt_misc            14604  1
rfcomm                 45352  0
l2cap                  28160  5 rfcomm
bluetooth              62340  4 rfcomm,l2cap
ppdev                  11272  0
i915                   29056  3
drm                   103464  4 i915
acpi_cpufreq           10760  1
cpufreq_ondemand       10640  2
cpufreq_userspace       6176  0
cpufreq_stats           8416  0
freq_table              6336  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     9736  0
cpufreq_powersave       3072  0
pcc_acpi               15616  0
dev_acpi               17028  0
tc1100_wmi              9224  0
sony_acpi               7064  0
battery                12040  0
sbs                    17856  0
asus_acpi              19756  0
backlight               8448  1 asus_acpi
ac                      6920  0
button                 10016  0
dock                   11992  0
video                  19080  0
i2c_ec                  6784  1 sbs
i2c_core               26624  1 i2c_ec
container               6144  0
ipv6                  307072  14
lp                     15048  0
fuse                   51888  1
joydev                 12928  0
snd_intel8x0           38952  3
snd_ac97_codec        117720  1 snd_intel8x0
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49536  0
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           5380  0
snd_seq_oss            36608  0
snd_seq_midi           11008  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
usbhid                 29088  0
hid                    34048  1 usbhid
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
af_packet              27020  2
xpad                   11272  0
snd                    68904  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13648  0
iTCO_vendor_support     5636  1 iTCO_wdt
pcspkr                  4736  0
soundcore              10272  1 snd
parport_pc             40104  1
parport                43404  3 ppdev,lp,parport_pc
intel_agp              29376  1
snd_page_alloc         11792  2 snd_intel8x0,snd_pcm
evdev                  13056  5
tsdev                  10112  0
ext3                  143760  1
jbd                    68208  1 ext3
mbcache                11400  1 ext3
sg                     40616  0
sd_mod                 25092  3
sr_mod                 18980  0
cdrom                  40744  1 sr_mod
ata_piix               18308  2
ata_generic            10628  0
libata                137000  2 ata_piix,ata_generic
8139cp                 27776  0
scsi_mod              166968  4 sg,sd_mod,sr_mod,libata
generic                 6532  0 [permanent]
floppy                 67944  0
8139too                30976  0
mii                     7424  2 8139cp,8139too
ehci_hcd               37004  0
uhci_hcd               28320  0
usbcore               154416  5 usbhid,xpad,ehci_hcd,uhci_hcd
thermal                16912  0
processor              34952  2 acpi_cpufreq,thermal
fan                     6536  0
fbcon                  44416  0
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0
commoncap               9472  1 capability


**/etc/X11/xorg.conf**
Linux chiraporn-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
chiraporn@chiraporn-desktop:~$ cat /etc/X11/xorg.conf
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
        Load    "bitmap"
        Load    "dbe"
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
        Identifier      "Intel 945G"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "TopSync 22 inch"
        Option          "DPMS"
        HorizSync       31-83
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 945G"
        Monitor         "TopSync 22 inch"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1280x1024" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1280x1024" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1280x1024" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1280x1024" "1280x768" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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

**Supported monitor resolutions**
720x400
640x480
720x480
800x600
1024x768
1152x864
1280x720
1280x768
1280x1024
1360x768
1680x1050

**xresprobe i810**
id: ANALOG
res: 1280x1024 1280x960 1024x768 832x624 800x600 720x400 640x480
freq: 31-83 56-75
disptype: crt

Best resolution achieved 1280x960

Please help me out! I'm dying here.

---

### Post by wgandhi on 2007-05-11
I think the problem maybe that the section of your xorg.conf that corresponds to the Depth 16 setting does not list 1680x1050 as a supported resolution. Try adding that and restart X.

If that does not work, can u post the output of Xorg.log

-Wish

---

### Post by daengbo on 2007-05-13
Thanks for the suggestion, but that's the first thing I did. I had to remove video modes which didn't work, because my monitor would go blank except for the message "Unsupported video mode" or some such. Really quite frustrating for me. I spent a fair amount on the monitor to make it as nice as possible, qand can't get it to work. 

I think the problem can be seen in the resprobe i810 section. Nothing above 1280x960 is supported, and that's the highest resolution I can get. I really don't understand the command, though, so I'm not sure whether the problem lies with the driver or the monitor.

Additional headaches come from the monitor supporting 16 or 32 bit mode, while the i810 drive supports 16 or 24 bit, leaving my "graphics station" with 16 bit color. Yech!

---

### Post by jimbo99 on 2007-05-13
On my nvidia setup I have to run the nvidia-settings to set the correct resolution and then I have to run the "screen resolution" off the system > Preferences menu.  When both are set to the correct resolution I can have my 24" lcd widescreen HD monitor work at the correct resolution.

I didn't focus on your specific instructions because frankly it sounds like you are working too hard.  Getting far more complex than should be necessary.

Ubuntu is for human beings.  Hopefully you'll get your problem worked out and she can see the beauty that is Ubuntu.  But there are still lots of issues with X and video and screens that the folks at Ubuntu should be focusing on.  Too much labor spent on this by the users ends typically in people going back to Windows.

---

### Post by RedSquirrel on 2007-05-13
Have you tried adding a Modeline? 

That is sometimes required for the i810 driver + [915resolution]("http://www.geocities.com/stomljen/") combination.

Have a look at this HOWTO to setup the Modeline:

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?p=454217")

---

### Post by RedSquirrel on 2007-05-13
> **jimbo99 said:**
> I didn't focus on your specific instructions because frankly it sounds like you are working too hard.  Getting far more complex than should be necessary.

The steps to configure the i810 driver are more challenging than the steps to setup some of the other drivers out there.

It's too bad, but that's just the way it is (for now). ;)

---

### Post by daengbo on 2007-05-14
> **jimbo99 said:**
> On my nvidia setup I have to run the nvidia-settings to set the correct resolution and then I have to run the "screen resolution" off the system > Preferences menu.  When both are set to the correct resolution I can have my 24" lcd widescreen HD monitor work at the correct resolution.

I didn't focus on your specific instructions because frankly it sounds like you are working too hard.  Getting far more complex than should be necessary.

Ubuntu is for human beings.  Hopefully you'll get your problem worked out and she can see the beauty that is Ubuntu.  But there are still lots of issues with X and video and screens that the folks at Ubuntu should be focusing on.  Too much labor spent on this by the users ends typically in people going back to Windows.

I've been a Linux user since 1997 and Ubuntu since Hoary, so I don't normally have a problem setting stuff up. Too many conflicting pieces on this one. Monitor specs report something different than the i810 driver. I'm considering giving up and buying NVidia and using the closed driver for it. Yech!

Swuirrel: Thanks for the modeline link. I'll try it when I get hope, but I really suspect that the driver is artificially limiting my choices  here, so I'm not sure if it will help. Haven't used a modeline in five years. I though I was past that stuff.

---

