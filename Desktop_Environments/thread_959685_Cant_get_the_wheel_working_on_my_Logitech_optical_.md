---
title: "Cant get the wheel working on my Logitech optical PS2 mouse"
date: 2008-10-26
forum: Desktop Environments
---

### Post by latev on 2008-10-26
I just installed Ubuntu 8.04 and cant get my standard ps/2 mouse wheel button to work. A cat /dev/input/mice and cat /dev/psaux command both produce events corresponding to mouse movements and button clicks, including the wheel button click, alas upon scrolling the wheel no input is generated. I tried booting into Knoppix live distro to see if that would be any better, but looks like the mouse wheel doesnt work there either. Under WinXP though everything appears to work fine.
Heres my xorg section:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol" "IMPS/2"
#       Option          "Protocol" "ExplorerPS/2"
        Option          "Device" "/dev/psaux"
        Option          "CorePointer"
        Option          "Emulate3Buttons" "false"
        Option          "Buttons" "5"
        Option          "ZAxisMapping"  "4 5"
EndSection

The mouse model at the bottom reads: Logitech Premium Optical Wheel mouse , M-BT58

Heres some more info about my system

tl@AMD:~$ lsmod
Module                  Size  Used by
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
video                  19856  0 
output                  4736  1 video
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
loop                   18948  0 
ipv6                  267780  8 
snd_usb_audio          83936  2 
snd_usb_lib            18432  1 snd_usb_audio
fglrx                1555468  23 
agpgart                34760  1 fglrx
snd_hda_intel         344856  2 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  2 snd_usb_audio,snd_hda_intel
snd_seq_dummy           4868  0 
serio_raw               7940  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
button                  9232  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_usb_audio,snd_usb_lib,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_nforce2             7680  0 
i2c_core               24832  1 i2c_nforce2
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
parport_pc             36260  1 
k8temp                  6656  0 
evdev                  13056  4 
soundcore               8800  1 snd
parport                37832  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
psmouse                40336  0 
reiserfs              239616  2 
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  4 
ata_generic             8324  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
usb_storage            73664  0 
libusual               19108  1 usb_storage
pata_amd               14212  0 
sata_nv                27528  3 
pata_acpi               8320  0 
forcedeth              51980  0 
ehci_hcd               37900  0 
ohci_hcd               26640  0 
libata                159344  4 ata_generic,pata_amd,sata_nv,pata_acpi
scsi_mod              151436  5 sg,sr_mod,sd_mod,usb_storage,libata
usbcore               146412  8 snd_usb_audio,snd_usb_lib,usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 


tl@AMD:~$ uname -a
Linux AMD 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

Am I missing something in the kernel?

---

### Post by ukera on 2008-10-26
perhaps maybe its broken, try re installing driver?  maybe it's not compatible with ubuntu.. maybe not, I'm not the best at ubuntu, have you tried using a different mouse?

---

### Post by latev on 2008-10-26
Thanks for the prompt reply!
Like I mentioned earlier in the original post I don't believe the mouse is physically broken as it works just fine in WinXP. I tend to believe it's more of an incompatibility issue with the Linux kernel for example. I tried rebooting several times while playing around with the configuration settings without any apparent improvement.
Also what exactly do you mean by reinstalling the driver in my case?

---

### Post by ukera on 2008-10-26
hmm if I were you I would try google searching for your mouse version and compatibility with ubuntu or any linux distro.  then reply back k?

---

### Post by Shazaam on 2008-10-26
I have a Logitech mouse (MX1000-shouldn't matter). Here is the relevant parts of my xorg.conf...
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection
```
and...
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
```

---

### Post by latev on 2008-10-26
Looks like other ppl have been able to install and configure this kind of mouse successfully:
[http://www.ubuntuhcl.org/browse/product+logitech-m-bt58?id=726](http://www.ubuntuhcl.org/browse/product+logitech-m-bt58?id=726)

the command cat tl@AMD:~$ cat /proc/bus/input/devices 

reveals among other things
...
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
...

and I think this is part of the problem - my mouse shouldn't be just PS/2 generic it should be ImPS/2, but I guess it's not recognized properly because it's not a usb one. The question now becomes how to tell the kernel to look for a Logitech ImPS/2 mouse at that location

---

### Post by latev on 2008-10-27
Just managed to recover my desktop after it crashed badly when I switched to your xorg settings. I isolated the lines
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
to be causing the problem.
Now my system appears to be working fine - as before, without the scroll button working :(

Just curious Shazaam, does the command cat /dev/psaux produce any output in response to the mouse wheel on your system?

Also what does cat /proc/bus/input/devices say upon mouse initialization?
/see my previous post/

---

### Post by Shazaam on 2008-10-27
This...
```
cat /dev/psaux
```
works but does weird things (strange characters, other things).
Here is cat /proc/bus/input/devices
```
I: Bus=0011 Vendor=0002 Product=0002 Version=000f
N: Name="PS2++ Logitech MX Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=046d Product=c501 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input7
U: Uniq=
H: Handlers=mouse2 event7 
B: EV=20017
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
B: LED=ff00

```
The MX1000 is a usb mouse that I have plugged into the ps/2 port with the Logitech supplied adapter (I need the USB ports for other stuff).

---

### Post by latev on 2008-10-27
This is so discouraging :(
Looks like the problem in my case is indeed the kernel not recognizing my particular mouse properly. It's convinced that my mouse doesn't have a scroll button and I've no idea how to tell the kernel the right mouse model and stuff like that
And the mouse is a true PS/2 model, I think I had a usb adapter for it but couldn't get it work with it

---

