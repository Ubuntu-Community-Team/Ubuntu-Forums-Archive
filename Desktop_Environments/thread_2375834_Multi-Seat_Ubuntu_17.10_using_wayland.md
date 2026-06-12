---
title: "Multi-Seat Ubuntu 17.10 using wayland ???"
date: 2017-10-27
forum: Desktop Environments
---

### Post by MasterCATZ on 2017-10-27
I have been using x-org / light-dm for quite some time for my multi-seated setup 
but this is now all broken with the drop on Unity for Gnome

how do I go about multi-seating again? I had multiple monitors bound to their own Bluetooth key/mouse and usb sound cards 
I especially need my wireless projector to be bound to its own environment as in a single user setup normally when its turned on it throws all other displays out of wack 
either crashing the display driver or causing all displays to change settings/positions

---

### Post by TheFu on 2017-10-28
On the login screen, click the gear, select the "xorg" option.  Be happy.

BTW, "17.10" is the proper version.  There is no 17.1.  The "10" means October, so the trailing zero matters.
Similarly, 18.04 is April of 2018, so the leading zero matters. ;)

---

### Post by mal on 2017-10-30
I have multiseat running on 17.10 with gdm and wayland.  I just assigned the relevant display controller, usb hub and sound card using loginctl commands, rebooted and up it came with 2 seats.  It seems to block access to virtual terminals (ctrl-F1, etc), but otherwise it is working well.

Regards,

Mal

---

### Post by MasterCATZ on 2017-11-03
@mal thanks for the hint loginctl
could you direct me to a way to do this 
I just need to work out how to use that extra seat 

my attempts left me with a flickering screen on reboot looked like gdm stuck in a loop

Nov 3 22:37:12 aio systemd-logind[2822]: Removed session c49.
Nov 3 22:37:12 aio systemd: pam_unix(systemd-user:session): session closed for user gdm
Nov 3 22:37:12 aio gdm-launch-environment]: pam_unix(gdm-launch-environment:session): session opened for user gdm by (uid=0)
Nov 3 22:37:12 aio systemd: pam_unix(systemd-user:session): session opened for user gdm by (uid=0)
Nov 3 22:37:12 aio systemd-logind[2822]: New session c50 of user gdm.
Nov 3 22:37:12 aio gdm-launch-environment]: pam_unix(gdm-launch-environment:session): session closed for user gdm



[https://itfknworks.wordpress.com/2015/06/21/ubuntu-dual-seat-setup/](https://itfknworks.wordpress.com/2015/06/21/ubuntu-dual-seat-setup/)



$sudo loginctl attach seat_kodi /sys/devices/pci0000:0&#8230;0/0000:03:00.0/usb10/10-1/10-1:1.2/0003:046D:C52B.0003/0003:046D:400E.0004/input/input3
Could not attach device: No such device

$ sudo loginctl attach seat_kodi /sys/bus/hid/drivers/logitech-djreceiver/0003:046D:C52B.0003/0003:046D:400E.0004/input/input3


$ sudo loginctl attach seat_kodi /sys/devices/pci0000:00/0000:00:01.0/drm/card0/card0-HDMI-A-1


$ sudo loginctl attach seat_kodi /sys/devices/pci0000:00/0000:00:14.2/sound/card1



SESSION UID USER SEAT TTY 
c1 132 gdm seat0 /dev/tty1 
10 1000 aio seat0 /dev/tty2 
6 1000 aio seat0 /dev/tty2 
597 1001 kodi seat0 /dev/tty3 
602 1001 kodi seat0 /dev/tty4 


 
loginctl seat-status seat_kodi
seat_kodi
Devices:
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.0/drm/card0/card0-HDMI-A-1
&#9474; [MASTER] drm:card0-HDMI-A-1
&#9500;&#9472;/sys/devices/pci0000:0&#8230;7.0/0000:03:00.0/usb10/10-1/10-1:1.2/0003:046D:C52B.0003/0003:046D:400E.0004/input/input3
&#9474; input:input3 "Logitech K400"
&#9492;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1
sound:card1 "Generic"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input10
&#9474; input:input10 "HD-Audio Generic Rear Mic"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input11
&#9474; input:input11 "HD-Audio Generic Line"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input12
&#9474; input:input12 "HD-Audio Generic Line Out Front"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input13
&#9474; input:input13 "HD-Audio Generic Line Out Surround"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input14
&#9474; input:input14 "HD-Audio Generic Line Out CLFE"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input15
&#9474; input:input15 "HD-Audio Generic Line Out Side"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input16
&#9474; input:input16 "HD-Audio Generic Front Headphone"
&#9492;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input9
input:input9 "HD-Audio Generic Front Mic"
input:input9 "HD-Audio Generic Front Mic"



$ loginctl list-seats
SEAT 
seat0 
seat_kodi 


2 seats listed.



all I can find is ways to get lightdm to multiseat 

what config file would be used to start a wayland session with kodi running with its own hardware locked to it ( key/mouse and display ) 
and still, have my normal session running x11 with all other devices



loginctl seat-status seat0
seat0
Sessions: 602 597 *10 6 c1
Devices:
&#9500;&#9472;/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
&#9474; input:input1 "Power Button"
&#9500;&#9472;/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
&#9474; input:input0 "Power Button"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.0/drm/card0
&#9474; [MASTER] drm:card0
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.0/drm/card0/card0-DVI-D-1
&#9474; &#9474; [MASTER] drm:card0-DVI-D-1
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.0/drm/card0/card0-HDMI-A-1
&#9474; &#9474; [MASTER] drm:card0-HDMI-A-1
&#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.0/drm/card0/card0-VGA-1
&#9474; [MASTER] drm:card0-VGA-1
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.0/drm/renderD128
&#9474; drm:renderD128
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.0/graphics/fb0
&#9474; [MASTER] graphics:fb0 "radeondrmfb"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:01.1/sound/card0
&#9474; sound:card0 "HDMI"
&#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:01.1/sound/card0/input8
&#9474; input:input8 "HDA ATI HDMI HDMI/DP,pcm=3"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:07.0/0000:03:00.0/usb10
&#9474; usb:usb10
&#9474; &#9492;&#9472;**/sys/devices/pci0000:0&#8230;0/0000:03:00.0/usb10/10-1/10-1:1.2/0003:046D:C52B.0003/0003:046D:400E.0004/input/input3**
&#9474; input:input3 "Logitech K400"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:07.0/0000:03:00.0/usb11
&#9474; usb:usb11
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:10.0/usb6
&#9474; usb:usb6
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:10.0/usb7
&#9474; usb:usb7
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:10.1/usb8
&#9474; usb:usb8
&#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:10.1/usb8/8-2/8-2:1.0/sound/card2
&#9474; sound:card2 "Pro"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:10.1/usb9
&#9474; usb:usb9
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.0/usb3
&#9474; usb:usb3
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1
&#9474; &#9474; usb:3-1
&#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.1/3-1.1:1.0/0003:046D:C221.0005/input/input4
&#9474; &#9474; &#9474; input:input4 "Logitech Logitech Gaming Keyboard"
&#9474; &#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.1/3-1.1:1.1/0003:046D:C221.0006/input/input5
&#9474; &#9474; &#9474; input:input5 "Logitech Logitech Gaming Keyboard"
&#9474; &#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1.4/3-1.4:1.0/0003:046D:C222.0007/input/input6
&#9474; &#9474; input:input6 "G15 Keyboard G15 Keyboard"
&#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/0003:046D:C049.0008/input/input7
&#9474; input:input7 "Logitech USB Gaming Mouse"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:12.2/usb1
&#9474; usb:usb1
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.0/usb4
&#9474; usb:usb4
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:13.2/usb2
&#9474; usb:usb2
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1
&#9474; sound:card1 "Generic"
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input10
&#9474; &#9474; input:input10 "HD-Audio Generic Rear Mic"
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input11
&#9474; &#9474; input:input11 "HD-Audio Generic Line"
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input12
&#9474; &#9474; input:input12 "HD-Audio Generic Line Out Front"
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input13
&#9474; &#9474; input:input13 "HD-Audio Generic Line Out Surround"
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input14
&#9474; &#9474; input:input14 "HD-Audio Generic Line Out CLFE"
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input15
&#9474; &#9474; input:input15 "HD-Audio Generic Line Out Side"
&#9474; &#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input16
&#9474; &#9474; input:input16 "HD-Audio Generic Front Headphone"
&#9474; &#9492;&#9472;/sys/devices/pci0000:00/0000:00:14.2/sound/card1/input9
&#9474; input:input9 "HD-Audio Generic Front Mic"
&#9500;&#9472;/sys/devices/pci0000:00/0000:00:14.5/usb5
&#9474; usb:usb5
&#9500;&#9472;/sys/devices/virtual/misc/kvm
&#9474; misc:kvm
&#9492;&#9472;/sys/devices/virtual/misc/rfkill
misc:rfkill

---

### Post by mal on 2017-11-07
MasterCATZ,

My loginctl commands were:

sudo loginctl attach seat-1 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
sudo loginctl attach seat-1 /sys/devices/pci0000:00/0000:00:1b.0/sound/card0
sudo loginctl attach seat-1 /sys/devices/pci0000:00/0000:00:14.0/usb3

It seems to only work with whole devices, like the video cards, sound device and usb hub.  I was not able to attach an individual usb device, like a keyboard or mouse.

Hope this helps.

Mal

---

