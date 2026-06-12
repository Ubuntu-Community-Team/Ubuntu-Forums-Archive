---
title: "Hang on logon (After entering username/password)"
date: 2006-02-27
forum: Desktop Environments
---

### Post by dwessell on 2006-02-27
Hey all...

I have installed Ubuntu on two Compaq Presario 2100 laptop cards.. One works perfectly, the other hangs while bringing up Gnome (After entering login name and passwod).. It hangs for anywhere from 5-10 mins..

The only difference in the laptops is that the one that hangs has a different wireless NIC, one that I had to use ndiswrapper to use..

I've disabled auto checking for updates, thinking this might cause an issue.. But to no avail, any thoughts would be welcome.

Thanks
David

---

### Post by o_fortuna on 2006-02-27
[QUOTE=dwessell]Hey all...

I have installed Ubuntu on two Compaq Presario 2100 laptop cards.. One works perfectly, the other hangs while bringing up Gnome (After entering login name and passwod).. It hangs for anywhere from 5-10 mins..

The only difference in the laptops is that the one that hangs has a different wireless NIC, one that I had to use ndiswrapper to use..

I've disabled auto checking for updates, thinking this might cause an issue.. But to no avail, any thoughts would be welcome.

Thanks
David[/QUOTE]
Have you narrowed down the wireless as the problem? If so, it would be best to find out what it is. Do this in a terminal (Applications-->Accessories-->Terminal)
```
sudo lshw
```
You'll need to enter your password. Scroll down and look for anything that looks like it might be the wireless NIC. The beginning of mine looks like this:
```
*-network
             description: Wireless interface

```
It may be that the drivers are corrupted/broken/not correct, so this will help us with that.

---

### Post by dwessell on 2006-02-27
ofortuna,

I'm not 100% sure that it is the wireless, however, that's my best guess for now..

My results are 

```

     *-network
          description: Wireless interface
          product: Intersil ISL3890 [Prism GT/Prism Duette]
          vendor: Intersil Corporation
          physical id: 1
          bus info: pci@02:00.0
          logical name: wlan0
          version: 01
          serial: 00:09:5b:ea:b8:48
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper ip=192.168.0.103 link=yes multicast=yes wireless=IEEE 802.11b
          resources: iomemory:c000000-c001fff irq:11

```

This might be of interest too.. This is my /etc/network/interfaces file. It's the only thing that I've modded for this install, except for removing the prism drivers, and installing the ndiswrapper

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid sinnis



# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

```

Thanks
David

---

### Post by bernardfrancois on 2006-02-28
Maybe you can post the contents of ~/.xsession-errors.

---

### Post by dwessell on 2006-02-28
I see in there cannot find localhost... Could that be it? I tried to ping localhost, but recieved no response... Funny thing is, I'm writing this on the laptop now, so I am connecting to the net.. :)

Any thoughts would be welcome.. Thanks for this thread.. I've already learned something new.

Thanks
David

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "molly"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/NCC1701-D:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/NCC1701-D:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/NCC1701-D:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/NCC1701-D:/tmp/.ICE-unix/6918

** (gnome-session:6918): WARNING **: Esound failed to start.


** (gnome-session:6918): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command = 
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
manager.c/2082: mount_all: mounting /dev/hdc
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_label_...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_label_
Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
mount: block device /dev/hdc is write-protected, mounting read-only
manager.c/1878: Mounted: /org/freedesktop/Hal/devices/volume_label_

** (gnome-cups-icon:7543): WARNING **: IPP request failed with status 1280

(gnome-terminal:7617): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7617): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

```

---

