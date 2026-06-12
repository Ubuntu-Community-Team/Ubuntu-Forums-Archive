---
title: "Lubuntu 12.10 TouchScreen detected as JoyStick make Axes Swap &amp; Inversion"
date: 2012-10-28
forum: Desktop Environments
---

### Post by B3taboy on 2012-10-28
I would like to say hello to everybody considering that it is my first post on this great community.

I have a small question regarding my touchscreen display, what seems to have the axes inverted. After i execute in terminal the :

    xinput set-int-prop 8 'Evdev Axis Inversion' 8 1 0
    xinput set-int-prop 8 'Evdev Axes Swap' 8 1
everything seems to work great and the mouse if calibrated as it should be but the settings are lost at reboot.

How can i make this settings permanent.

I created a 99-calibration.conf in /usr/share/X11/xorg.conf.d with the fallowing content after running input_calibrator, but I'm bot sure where to add the Axes swap and Inversion.

Section "InputClass" Identifier "calibration" MatchProduct "FREE INTERACTIVE TECHNOLOGY FITOUCH Devices" Option "Calibration" "-388 32919 -159 33106" EndSection

Here is my 10-edev.conf file in case you will need it:

```
 # Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Option "SwapAxes" "yes"
        Option "InvertY" "yes"
        Option  "Calibration"   "-388 32919 -159 33106"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "tap-by-default"
        MatchIsTouchpad "on"
        Option "TapButton1" "1"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```

Thank you

---

### Post by Favux on 2012-10-28
Hi B3taboy,

Welcome to Ubuntu forums!


So the device name is "FREE INTERACTIVE TECHNOLOGY FITOUCH Devices"?  What is the tablet line in the **lsusb** ouput and in the output of **xinput list**?  It would be nice to confirm the touch screen name is FITOUCH (Free Interactive Touch?).

FYI custom (user) .conf files should be in /etc/X11/xorg.conf.d.  The /usr/share/X11/xorg.conf.d is for the Distro.  Also I'm not quite sure why you altered the 10-evdev.conf (which you shouldn't do) when you also added a custom .conf file for calibration.

So in /etc/X11/xorg.conf.d add a file called say 52-touchscreen.conf:
```
gksudo gedit /etc/X11/xorg.conf.d/52-touchscreen.conf
```
You may need to create the directory first:
```
sudo mkdir /etc/X11/xorg.conf.d
```
Add into the file the following snippet:
```
Section "InputClass"
    Identifier "FITouch"
    MatchIsTouchscreen "on"
    MatchProduct "FREE INTERACTIVE TECHNOLOGY FITOUCH Devices"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    Option "SwapAxes" "on"
    Option "InvertY" "on"
    Option "Calibration" "-388 32919 -159 33106"
EndSection
```
Save Close and reboot.  That's my best guess based on what you've shown.  May need a little tweaking.

The xinput commands are runtime commands not static options you can place in xorg.conf.d or xorg.conf.  If you wanted to use them instead they can be placed in a script that you set to run at startup.  For instructions and examples see part IV. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Notice part VI. discusses some xinput commands.  You'd probably want to call the script xinput.sh or some such.  Also ID # can change so it is better to use "device name" instead in a script.

---

### Post by B3taboy on 2012-11-07
Thank you for your reply..
```

xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; FREE INTERACTIVE TECHNOLOGY  FITOUCH Devices	id=8	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; CHICONY HP Basic USB Keyboard           id=9	[slave  keyboard (3)]
```

I don't know the reason why the device is not showing in lsusb.
But i confirm the touchscreen is 
FREE INTERACTIVE TECHNOLOGY  FITOUCH Devices	id=8	[slave  pointer  (2)]

Sholud i do any modifications in the 52-touchscreen u gave me?

Thank you

---

### Post by Favux on 2012-11-07
Hmm. Not in lsusb.  Maybe you should post it?

Since it isn't there, but is in xinput list, then the only other option is an internal serial connection rather than a usb one.  It could be it is using inputattach.  That might explain the joystick deal.

If you get lucky you might be able to determine the serial port it is on with:
```
sudo dmesg | grep ttyS
```

And yes the .conf file should work if it is a serial device that is using inputattach.

---

### Post by B3taboy on 2012-11-07
Here is the output:

```
sudo dmesg | grep usb
[    0.232297] ACPI: bus type usb registered
[    0.232368] usbcore: registered new interface driver usbfs
[    0.232403] usbcore: registered new interface driver hub
[    0.232463] usbcore: registered new device driver usb
[    0.628111] usb usb1: >New USB device found, idVendor=1d6b, idProduct=0002
[    0.628119] usb usb1: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.628126] usb usb1: >Product: EHCI Host Controller
[    0.628133] usb usb1: >Manufacturer: Linux 3.5.0-17-generic ehci_hcd
[    0.628139] usb usb1: >SerialNumber: 0000:00:1d.7
[    0.628875] usb usb2: >New USB device found, idVendor=1d6b, idProduct=0001
[    0.628883] usb usb2: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.628889] usb usb2: >Product: UHCI Host Controller
[    0.628896] usb usb2: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    0.628902] usb usb2: >SerialNumber: 0000:00:1d.0
[    0.629472] usb usb3: >New USB device found, idVendor=1d6b, idProduct=0001
[    0.629480] usb usb3: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.629487] usb usb3: >Product: UHCI Host Controller
[    0.629493] usb usb3: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    0.629499] usb usb3: >SerialNumber: 0000:00:1d.1
[    0.630077] usb usb4: >New USB device found, idVendor=1d6b, idProduct=0001
[    0.630085] usb usb4: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.630091] usb usb4: >Product: UHCI Host Controller
[    0.630098] usb usb4: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    0.630104] usb usb4: >SerialNumber: 0000:00:1d.2
[    0.630682] usb usb5: >New USB device found, idVendor=1d6b, idProduct=0001
[    0.630690] usb usb5: >New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.630697] usb usb5: >Product: UHCI Host Controller
[    0.630703] usb usb5: >Manufacturer: Linux 3.5.0-17-generic uhci_hcd
[    0.630710] usb usb5: >SerialNumber: 0000:00:1d.3
[    0.631299] usbcore: registered new interface driver libusual
[    1.108054] usb 1-5: >new high-speed USB device number 4 using ehci_hcd
[    1.257407] usb 1-5: >New USB device found, idVendor=148f, idProduct=3070
[    1.257415] usb 1-5: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.257420] usb 1-5: >Product: 802.11 n WLAN
[    1.257425] usb 1-5: >Manufacturer: Ralink
[    1.257430] usb 1-5: >SerialNumber: 1.0
[[B]    1.608048] usb 3-1: >new full-speed USB device number 2 using uhci_hcd
[    1.764486] usb 3-1: >New USB device found, idVendor=10c4, idProduct=5e50
[    1.764495] usb 3-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.764501] usb 3-1: >Product: FITOUCH Devices
[    1.764506] usb 3-1: >Manufacturer: FREE INTERACTIVE TECHNOLOGY [/B]
[    2.008146] usb 3-2: >new low-speed USB device number 3 using uhci_hcd
[    2.176508] usb 3-2: >New USB device found, idVendor=192f, idProduct=0916
[    2.176521] usb 3-2: >New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.176529] usb 3-2: >Product: USB Optical Mouse
[    2.236978] usbcore: registered new interface driver usbhid
[    2.236987] usbhid: USB HID core driver
[    2.380212] usb 1-5: >reset high-speed USB device number 4 using ehci_hcd
[    2.592570] Registered led device: rt2800usb-phy0::radio
[    2.592649] Registered led device: rt2800usb-phy0::assoc
[    2.592731] Registered led device: rt2800usb-phy0::quality
[    2.592837] usbcore: registered new interface driver rt2800usb
[ [B]   2.617691] input: FREE INTERACTIVE TECHNOLOGY  FITOUCH Devices as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input7
[    2.621007] hid-generic 0003:10C4:5E50.0001: >input,hiddev0,hidraw0: USB HID v10.01 Mouse [FREE INTERACTIVE TECHNOLOGY  FITOUCH Devices] on usb-0000:00:1d.1-1/input0[/B]
[    2.623238] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input8
[    2.624203] hid-generic 0003:192F:0916.0002: >input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2/input0
[    2.632070] usb 5-1: >new full-speed USB device number 2 using uhci_hcd
[    2.821696] usb 5-1: >New USB device found, idVendor=046d, idProduct=c52b
[    2.821705] usb 5-1: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.821710] usb 5-1: >Product: USB Receiver
[    2.821715] usb 5-1: >Manufacturer: Logitech
[    2.855918] logitech-djreceiver 0003:046D:C52B.0005: >hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.3-1/input2
[    2.862192] input: Logitech Unifying Device. Wireless PID:2007 as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.2/0003:046D:C52B.0005/input/input9
[    2.864318] logitech-djdevice 0003:046D:C52B.0006: >input,hidraw3: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2007] on usb-0000:00:1d.3-1:1
[    2.866266] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.2/0003:046D:C52B.0005/input/input10
[    2.867871] logitech-djdevice 0003:046D:C52B.0007: >input,hidraw4: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:1d.3-1:2
```
```
~$ sudo dmesg | grep ttyS
[    0.410387] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.430809] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.451229] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.471650] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    0.494759] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.515281] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.535801] 00:08: ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
[    0.556366] 00:09: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A
[    0.576886] 00:0a: ttyS4 at I/O 0x2f0 (irq = 6) is a 16550A
[    0.597402] 00:0b: ttyS5 at I/O 0x2e0 (irq = 7) is a 16550A
```

I m not really sure how to interpret the code, but the touchscreen is connected to a low speed port?
That may explain the touch event delay ?

In the meantime i was able to create a startup script and place it in:
/home/andrei/.config/autostart/the.sh but this dosn't work for the other user i have.
Do you have any suggestions?

---

### Post by Favux on 2012-11-07
Okay, so it looks to be a usb device.
> I m not really sure how to interpret the code, but the touchscreen is connected to a low speed port?
That may explain the touch event delay ?
That could be or just as likely if there isn't a HID driver, in another words if it is using the generic HID core driver, that might be the problem.  It may need code to switch it into high speed reporting mode for example.

Is this suppose to be a multi-touch touchscreen?  If so we could check the ENAC site.  I can see if I have a 3.5 kernel around (haven't installed Quantal) and if there is a FITOUCH in the HID.

For the .conf file if the there isn't a HID driver you may want to comment out the touchscreen match line as the descriptor may not be setting that flag:
```
#    MatchIsTouchscreen "on"
```
> In the meantime i was able to create a startup script and place it in:
/home/andrei/.config/autostart/the.sh but this dosn't work for the other user i have.
Do you have any suggestions?
What is the script?

---

### Post by B3taboy on 2012-11-07
In fact they are 2 scripts:


```
/home/andrei/.config/autostart/swapaxes.desktop 
[Desktop Entry]
Name=SwapAxis
Exec=/usr/local/bin/swapaxex.sh
Type=Application
Terminal=false

/home/andrei/.config/autostart/invertaxis.desktop  
[Desktop Entry]
Name=InvertAxis
Exec=/usr/local/bin/axisinversion.sh
Type=Application
Terminal=false
```

Thanks again for your great support

---

### Post by Favux on 2012-11-07
I would think you could consolidate the two scripts into one with the two runtime xinput commands.  Or you should be able to use the static evdev options I showed you for the .conf file.

Don't see a FITOUCH or FREE INTERACTIVE TECHNOLOGY in the 3.5 /drivers/hid/usb-core.c or usb-ids.h.  And no driver.

Multi-touch?  Worth looking at ENAC?

---

### Post by B3taboy on 2012-11-08
It is multitouch (2 points, but 1 is enogh for me) but i guess it is a "no name" brand and we will not find it there.
I have a driver but the compatibility is till 10.10... please have a look.
[https://www.dropbox.com/s/aypr9473hwrc2x0/linux.rar](https://www.dropbox.com/s/aypr9473hwrc2x0/linux.rar)

I will keep you posted with the results.

---

### Post by Favux on 2012-11-08
So 2FGT.  Not at ENAC:  [http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html)

PDF claims up to and including Natty (11.04).  With Natty you probably have to whitelist the tray icon so it shows up in the Unity system tray.  They didn't happen to release it in C rather than the binary?  Is there a pkg.tar.bz2 pkg(?) the install.sh refers too?

Have you tried installing on Quantal?  What does the install script say when you do?

---

### Post by B3taboy on 2012-11-08
Hello,

After adding the script in /etc/X11/xorg.conf.d ... seems that nothing changed.

The startup script is good enough.. the only problem is that the the settings are not picked-up by the 2nd user. Do you thing it has something to do with the xsessions or with lightdm?

Thank you

---

### Post by Favux on 2012-11-08
Adding the two .desktop files for each user so the scripts autostart should work.

Unless the second user has a permissions problem with /usr/local/bin/swapaxex.sh and /usr/local/bin/axisinversion.sh?

---

### Post by B3taboy on 2012-11-09
Hello Favux,

Seems that whathewer i do the script doesn't start up for the other user.
I want to tell you that the pc works with one full screen browser and the 2nd user is the only one used.

I chmod 777 the script consolidated into one. but seems that nothing is working.

---

### Post by B3taboy on 2012-11-10
It worked !
Thank you for you help Favux!

Because i'm using xsessions the only way to execute the script for the other user was  to modify /home./user2/.xsession

```
!/bin/bash
xinput set-int-prop 8 'Evdev Axis Inversion' 8 1 0
xinput set-int-prop 8 'Evdev Axes Swap' 8 1
nm-applet &
nm-online
xset s off
xset -dpms

matchbox-window-manager &

while true; do
      browser
done


```

Btw.. do you know a simple virtual keyboard for lubuntu for kiosk use?

---

### Post by Favux on 2012-11-10
Nice work!  :)

I believe the default is suppose to be Onboard.  Is there a problem with it?

I don't know if one of the others like CellWriter or Florence work in Lubuntu.

---

