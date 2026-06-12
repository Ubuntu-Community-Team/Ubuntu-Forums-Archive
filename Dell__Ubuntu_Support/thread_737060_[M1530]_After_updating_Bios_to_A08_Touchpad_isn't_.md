---
title: "[M1530] After updating Bios to A08 Touchpad isn't working anymore"
date: 2008-03-27
forum: Dell  Ubuntu Support
---

### Post by GordonFreeman on 2008-03-27
Hi,
yesterday I updated my Bios vom A07 to A08 since it was said that the new Bios will resolve the touchpad issue which appears after closing the lid. And it's working fine unter Vista.
But today I booted Xubuntu 7.10 and the touchpad is not working anymore. But it's not that it won't be found, the touchpad ist listed in /proc/bus/input/devices and X can load the synaptics driver for it just fine.
The weird thing is that wenn I'm moving with the touchpad the cursor starts to spring around the desktop and issue all kind of events, sometimes X just hangs and I have to restart it.

I also tried xev and there are no events coming from the touchpad, when moving around or pressing the buttons (but after a time the cursor springs away and does whatever it wants). When it does that and I open a terminal and bring it to focus, something like this appears until I press ESC:
```

^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~^[[18~gordon@gordon-xps:~$ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ 

```

Here is the Xorg.log.0 (There are no errors or warnings in the whole log output):
```

(II) Synaptics touchpad driver version 0.14.6 (1406) 
(**) Option "Device" "/dev/input/event6" 
(**) Option "VertEdgeScroll" "1" 
(**) Option "HorizEdgeScroll" "1" 
(--) Synaptics Touchpad touchpad found 
(**) Option "SendCoreEvents" "true" 
(**) Synaptics Touchpad: always reports core events 
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE) 
(II) XINPUT: Adding extended input device "Bluetooth Mouse" (type: MOUSE) 
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD) 
Synaptics DeviceInit called 
SynapticsCtrl called. 
(II) Bluetooth Mouse: ps2EnableDataReporting: succeeded 
Synaptics DeviceOn called 
(--) Synaptics Touchpad touchpad found

```


cat /proc/bus/input/devices
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100 
N: Name="Macintosh mouse button emulation" 
P: Phys= 
S: Sysfs=/class/input/input0 
U: Uniq= 
H: Handlers=mouse0 event0 
B: EV=7 
B: KEY=70000 0 0 0 0 0 0 0 0 
B: REL=3 

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41 
N: Name="AT Translated Set 2 keyboard" 
P: Phys=isa0060/serio0/input0 
S: Sysfs=/class/input/input1 
U: Uniq= 
H: Handlers=kbd event1 
B: EV=120013 
B: KEY=100f 2002000 380207a f840d001 feffffdf ffefffff ffffffff ffffffff 
B: MSC=10 
B: LED=7 

I: Bus=0003 Vendor=0a5c Product=4502 Version=0111 
N: Name="Broadcom Corp" 
P: Phys=usb-0000:00:1d.2-2.2/input0 
S: Sysfs=/class/input/input2 
U: Uniq= 
H: Handlers=kbd event2 
B: EV=120003 
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe 
B: LED=7 

I: Bus=0003 Vendor=0a5c Product=4503 Version=0111 
N: Name="Broadcom Corp" 
P: Phys=usb-0000:00:1d.2-2.3/input0 
S: Sysfs=/class/input/input3 
U: Uniq= 
H: Handlers=mouse1 event3 
B: EV=7 
B: KEY=70000 0 0 0 0 0 0 0 0 
B: REL=3 

I: Bus=0010 Vendor=001f Product=0001 Version=0100 
N: Name="PC Speaker" 
P: Phys=isa0061/input0 
S: Sysfs=/class/input/input4 
U: Uniq= 
H: Handlers=kbd event4 
B: EV=40001 
B: SND=6 

I: Bus=0011 Vendor=0002 Product=0008 Version=0000 
N: Name="PS/2 Mouse" 
P: Phys=isa0060/serio2/input1 
S: Sysfs=/class/input/input5 
U: Uniq= 
H: Handlers=mouse2 event5 
B: EV=7 
B: KEY=70000 0 0 0 0 0 0 0 0 
B: REL=3 

I: Bus=0011 Vendor=0002 Product=0008 Version=7321 
N: Name="AlpsPS/2 ALPS GlidePoint" 
P: Phys=isa0060/serio2/input0 
S: Sysfs=/class/input/input6 
U: Uniq= 
H: Handlers=mouse3 event6 
B: EV=f 
B: KEY=420 0 70000 0 0 0 0 0 0 0 0 
B: REL=3 
B: ABS=1000003 

I: Bus=0019 Vendor=0000 Product=0005 Version=0000 
N: Name="Lid Switch" 
P: Phys=PNP0C0D/button/input0 
S: Sysfs=/class/input/input7 
U: Uniq= 
H: Handlers=event7 
B: EV=21 
B: SW=1 

I: Bus=0019 Vendor=0000 Product=0001 Version=0000 
N: Name="Power Button (CM)" 
P: Phys=PNP0C0C/button/input0 
S: Sysfs=/class/input/input8 
U: Uniq= 
H: Handlers=kbd event8 
B: EV=3 
B: KEY=100000 0 0 0 

I: Bus=0019 Vendor=0000 Product=0003 Version=0000 
N: Name="Sleep Button (CM)" 
P: Phys=PNP0C0E/button/input0 
S: Sysfs=/class/input/input9 
U: Uniq= 
H: Handlers=kbd event9 
B: EV=3 
B: KEY=4000 0 0 0 0 

I: Bus=0005 Vendor=046d Product=b006 Version=0124 
N: Name="Logitech Bluetooth Mouse" 
P: Phys=00:1E:4C:E4:E7:CE 
S: Sysfs=/class/input/input11 
U: Uniq=00:07:61:B7:75:79 
H: Handlers=mouse5 event11 
B: EV=7 
B: KEY=ff0000 0 0 0 0 0 0 0 0 
B: REL=143 

I: Bus=0011 Vendor=0002 Product=0001 Version=0000 
N: Name="PS/2 Generic Mouse" 
P: Phys=isa0060/serio1/input0 
S: Sysfs=/class/input/input16 
U: Uniq= 
H: Handlers=mouse4 event10 
B: EV=7 
B: KEY=70000 0 0 0 0 0 0 0 0 
B: REL=3

```


xorg.conf
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig 
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008 

# xorg.conf (xorg X Window System server configuration file) 
# 
# This file was generated by dexconf, the Debian X Configuration tool, using 
# values from the debconf database. 
# 
# Edit this file with caution, and see the xorg.conf manual page. 
# (Type "man xorg.conf" at the shell prompt.) 
# 
# This file is automatically updated on xserver-xorg package upgrades *only* 
# if it has not been modified since the last upgrade of the xserver-xorg 
# package. 
# 
# If you have edited this file but would like it to be automatically updated 
# again, run the following command: 
#   sudo dpkg-reconfigure -phigh xserver-xorg 

Section "ServerLayout" 

        # Uncomment if you have a wacom tablet 
        #       InputDevice     "stylus"        "SendCoreEvents" 
        #       InputDevice     "cursor"        "SendCoreEvents" 
        #       InputDevice     "eraser"        "SendCoreEvents" 
    Identifier     "Default Layout" 
    Screen         "Default Screen" 0 0 
    InputDevice    "Generic Keyboard" 
    InputDevice    "Bluetooth Mouse" "CorePointer" 
    InputDevice    "Synaptics Touchpad" 
EndSection 

Section "Files" 
EndSection 

Section "Module" 
    Load           "glx" 
EndSection 

Section "InputDevice" 
    Identifier     "Generic Keyboard" 
    Driver         "kbd" 
    Option         "CoreKeyboard" 
    Option         "XkbRules" "xorg" 
    Option         "XkbModel" "pc105" 
    Option         "XkbLayout" "de" 
    Option         "XkbVariant" "deadacute" 
EndSection 

Section "InputDevice" 
       Identifier      "Bluetooth Mouse" 
       Driver          "mouse" 
       Option          "CorePointer" 
       Option          "Device"                "/dev/input/mice" 
       Option          "Protocol"              "ExplorerPS/2" 
       Option          "Buttons"               "7" 
       Option          "ZAxisMapping"          "4 5" 
       Option          "ButtonMapping"         "1 2 3 6 7" 
       Option          "Emulate3Buttons"       "false" 
EndSection 

Section "InputDevice" 
    Identifier     "Synaptics Touchpad" 
    Driver         "synaptics" 
    Option         "SendCoreEvents" "true" 
    Option         "Device" "/dev/input/event6" 
    Option         "Protocol" "event" 
    Option         "HorizEdgeScroll" "1" 
    Option         "VertEdgeScroll" "1" 
EndSection 

Section "InputDevice" 
    Identifier     "stylus" 
    Driver         "wacom" 
    Option         "Device" "/dev/input/wacom" 
    Option         "Type" "stylus" 
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
    Identifier     "eraser" 
    Driver         "wacom" 
    Option         "Device" "/dev/input/wacom" 
    Option         "Type" "eraser" 
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
    Identifier     "cursor" 
    Driver         "wacom" 
    Option         "Device" "/dev/input/wacom" 
    Option         "Type" "cursor" 
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY 
EndSection 

Section "Monitor" 
    Identifier     "Generic Monitor" 
    HorizSync       28.0 - 72.0 
    VertRefresh     43.0 - 60.0 
    Option         "DPMS" 
EndSection 

Section "Device" 
    Identifier     "nVidia Corporation G80 [GeForce 8600M GT]" 
    Driver         "nvidia" 
EndSection 

Section "Screen" 
    Identifier     "Default Screen" 
    Device         "nVidia Corporation G80 [GeForce 8600M GT]" 
    Monitor        "Generic Monitor" 
    DefaultDepth    24 
    Option         "AddARGBVisuals" "True" 
    Option         "AddARGBGLXVisuals" "True" 
    Option         "NoLogo" "True" 
    SubSection     "Display" 
        Depth       24 
        Modes      "1440x1440" 
    EndSubSection 
EndSection

```

The psmouse module is (obviously) loaded.


Has anybody else this problem with the new bios?


Thanks.

---

### Post by GordonFreeman on 2008-03-27
I switched back to bios version A07 and touchpad is now fine again :)

---

### Post by raphoun on 2008-03-29
And if we want to stay on bios version A08, how to do to make the touchpad working?

---

### Post by bbroth on 2008-04-02
I had exactly the same issue in Fedora 8.
Funny thing is that the issue didn't appear in my Ubuntu 7.10 installation, nor in my OpenSuse 10.3 installation.
Was able to fix it by specifying the following extra argument to the kernel startup line in grub: 
i8042.nomux=1

---

### Post by TookiTheGreat on 2008-04-03
Thanks bbroth!

Your solution: 

"Was able to fix it by specifying the following extra argument to the kernel startup line in grub:
i8042.nomux=1"

Worked like a charm. I don't know where you gurus find this kind of arcana, but it sure made my day!

Cheers,

Bard (aka TookiTheGreat)
"Going for the ONE"

---

### Post by drumsticks on 2008-04-03
I had the same experience: upgraded to A08; found touchpad wonky; downgraded to A07. Can't really be bothered to upgrade again and apply the grub fix. Is there a real strong incentive to upgrade to A08?

---

### Post by mrojas73 on 2008-04-26
You guys saved my day!  Thank you very much.  For those who are new here is what needs to be done:

Edit grub:

```

sudo gedit /boot/grub/menu.lst

```

Find the Kernel line and add 18042.nomux=1 at the end.

---

### Post by rmgabald on 2008-04-26
Which Kernel line is the right one? What does the line look like when edited?

---

### Post by mrojas73 on 2008-04-26
> **rmgabald said:**
> Which Kernel line is the right one? What does the line look like when edited?

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=446ea0c7-57b1-4112-939c-3f1d74be9f5f ro quiet splash [COLOR="Red"]18042.nomux=1[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic quiet

```

---

### Post by rmgabald on 2008-04-27
When I insert the fix into the Kernel I get an "unknown boot option" error. The system still runs, but the touchpad is not fixed. I guess this patch just doesn't work for Ubuntu 8.04? any other suggestions would be great.

---

### Post by madiyaan on 2008-04-28
I just installed Ubuntu 8.04 on my M1530 laptop. I get an "unknown boot option" message at boot when I add the line 18042.nomux=1 in my menu.lst.

Does anyone have a fix? 

Regards,

---

### Post by smazero on 2008-05-01
I think a typo has crept into this tip, which is probably why it's not working for you. 

If you check bbroths original recommendation the kernel startup line addition should be:

```
i8042.nomux=1
```

but somewhere along the way that's been munged to

```
18042.nomux=1
```

So my complete menu.lst entry is:

```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4d1f9d83-796c-4618-bcfe-6125202bf4f4 ro quiet splash **i8042.nomux=1**
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

```

Adding the correct info has got my touchpad working fine, so check it and give it another try.

best of luck!

s

---

### Post by smazero on 2008-05-02
Actually after reading this thread: [http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

it seems that a better way of passing this option to the kernel boot options is to look for the line that starts [FONT="Lucida Console"]#defoptions[/FONT] in [FONT="Lucida Console"]/boot/grub/menu.lst[/FONT], and add this option to that line; and then run [FONT="Lucida Console"]sudo update-grub[/FONT]. 

I think this will ensure that if a kernel update is later released, then this option will be passed automatically to any new default boot entry.

So to clarify my /boot/grub/menu.lst now has the following lines:

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash i8042.nomux=1

```

It's important that this line remains commented out with the # at the start; don't be tempted to uncomment it.

Then execute:

```

$ sudo update-grub

```

Now if you reopen the menu.lst file, you should find that the default kernel option has the i8042.nomux=1 option appended to it.

---

### Post by damis648 on 2008-05-04
thank you so much smazero! i was worried for a minute that my trackpad had been serriosuly messed up...

---

### Post by toobaz on 2008-05-07
Actually, everything smazero wrote is true.

I just want to explicitly confirm that this fix *does* work on Ubuntu 8.04 Hardy (by experience!). Thanks to everyone.

Pietro

---

### Post by bloodorange on 2008-05-07
You guys and this forum are awesome.  I've got a Dell M1530, too, which worked perfectly with Gutsy (even with the BIOS A08 update!), but the touchpad just wouldn't work with Hardy.  I had to revert back to Gutsy, which wasn't too big a deal because Gutsy's great anyway.  I was disappointed, though, because I was really looking forward to getting Hardy on my machine.  I've been searching for a solution to the touchpad problem ever since Hardy was released, but couldn't find one.  Until now.

I've just put a fresh install of Hardy Ubuntu Studio (64 bit) back on my laptop and it works perfectly, including the touchpad.

Awesome!

Thank you so much!:guitar:

---

### Post by ParvathReddy on 2008-05-07
Thank you smazero, fix worked for me :)

---

### Post by semiconductor on 2008-05-08
Can someone help explain to a total newb where and how I add this code?
thanks semiconductor

---

### Post by amp_man on 2008-05-09
I tried the above fix with 8.04, and now the keyboard and touchpad are both nonresponsive.

EDIT: I have an XPS M1530 with the A08 BIOS as well.

---

### Post by semiconductor on 2008-05-10
I decided to go for the full ubuntu install as I was just running off the ubuntu live cd which worked fine apart from the erratic mouse error which others seemed to have fixed. 
Dell XPS 1530 320GB HD

I followed others explanations on how to install dual boot. Dell xps 1530 comes with 4 partitions so I deleted the restore partition which was 2nd. I then moved my OS partition along to 2nd so that I could add a larger one after it. After trying this which took more than 10 hours!!! Vista was totally lost. So I erased all the OS and media direct partitions and started to reinstall windows and media direct from scratch.
This worked for a while but then I started getting read / write errors. I went back to vista install again and formatted the HD again. Each time the HD got worse and now it doesn't work at all.

It was fine until I used Gparted. I have no confidence in trying any NTFS modification again with Gparted or ubuntu for that matter. I was very excited about using it and now I have a dead brand new laptop that Im going to have to beg to Dell to fix.

---

### Post by mrojas73 on 2008-05-10
> **rmgabald said:**
> When I insert the fix into the Kernel I get an "unknown boot option" error. The system still runs, but the touchpad is not fixed. I guess this patch just doesn't work for Ubuntu 8.04? any other suggestions would be great.

Can you paste a copy of your start menu here?

---

### Post by venky80 on 2008-05-10
both my keyboard and mouse are behaving erratically even after putting the kernel option in menu.lst.
I have the 1920 x 1200 8600 gt version of m1530, also the flash youtube videos are jerky in full screen, but i think something is really wrong with keyboard and mouse

---

### Post by semiconductor on 2008-05-13
After Gparted totally destroyed my new laptop hard drive I have been sent a replacement by DEll in 1 business working day and I now have it installed with vista and Ubuntu and fixed the trackpad. Media Direct does not work though. Even though I followed the instruction and installed it first. Never mind I will use Ubuntu instead

---

### Post by refus3 on 2008-05-16
Hello everyone, 
i have the same problem that some people i have a xps m1530 and when i update my bios the touchpad stop working, i add to the grub menu the suggested by the community but the touchpad still not working.
i appreciate all your help

---

### Post by htrex on 2008-05-26
I'm using Hardy and upgraded to A08 because it adds an option in the BIOS to enable Intel VT-x (disabled by default in A07 with no option to enable it).

After upgrade the touchpad started to behave erratically and had to fix with i8042.nomux=1, the problem now is that the touchpad becomed really slow and changing MinSpeed/MaxSpeed in xorg.conf has no effect.

Anyone knows how to enable VT-x while having a working touchpad ?

--htrex;

---

### Post by mrojas73 on 2008-05-27
> **htrex said:**
> I'm using Hardy and upgraded to A08 because it adds an option in the BIOS to enable Intel VT-x (disabled by default in A07 with no option to enable it).

After upgrade the touchpad started to behave erratically and had to fix with i8042.nomux=1, the problem now is that the touchpad becomed really slow and changing MinSpeed/MaxSpeed in xorg.conf has no effect.

Anyone knows how to enable VT-x while having a working touchpad ?

--htrex;

The new kernel updates to 24.17 broke it and there is no fix as far as I know.

---

### Post by htrex on 2008-06-09
the recent kernel update ( 2.6.24-18 ) solved the mouse problem with bios A08 for me.

still using i8042.nomux=1, I'll try to remove it to see if ok even without it.

--htrex;

---

### Post by Lacrimstein on 2008-06-12
The i8042.nomux=1 solution works for me, except now the touchpad is completely unconfigurable, not even through xorg.conf. I would really like to disable tap click but I cant :(

---

