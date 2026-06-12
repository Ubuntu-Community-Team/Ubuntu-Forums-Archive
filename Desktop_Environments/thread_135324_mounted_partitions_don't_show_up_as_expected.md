---
title: "mounted partitions don't show up as expected"
date: 2006-02-23
forum: Desktop Environments
---

### Post by curley_sue on 2006-02-23
I am a linux newbie.
I have ubuntu Breezy installed. 
I used to have my mounted partitions (FAT32 and NTFS) shown on the Desktop (as icons), in the Places menu and in nautilus (just like 'File system' and 'home'). when I used to load a CD or connect a usb the same would occur for those...

NOW SOMTHING WENT WRONG:
when I restart I don't get those mounted partitions any longer (auto mounting and icons appearing of CDs and USB works as expected).
I saw there was a bug posted for the same in Dapper but maybe ther could be a solution for the meanwhile?

what i've managed by now:

sudo invoke-rc.d dbus restart
#the icons are restored but no auto-mounting for CDs, USBs etc
# so...
gnome-volume-manager &
# now I have auto-mount but the CD or USB do not appear on the Desktop as the used to...

here's the terminal output: (I'll also attach my fstab at the end)

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
manager.c/562: setting[17]: bool: autoprinter = 1
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject

manager.c/1619: New Device: /org/freedesktop/Hal/devices/volume_part_1_size_339603456
manager.c/1669: no sensible filesystem for /org/freedesktop/Hal/devices/volume_part_1_size_339603456
manager.c/1686: Changed: /dev/hdc
manager.c/696: executing command: sound-juicer -d /dev/hdc

(sound-juicer:9899): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(sound-juicer:9899): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
This CD was not found.
manager.c/1812: Device removed: /org/freedesktop/Hal/devices/volume_part_1_size_339603456
manager.c/1619: New Device: /org/freedesktop/Hal/devices/volume_part_1_size_339603456
manager.c/1669: no sensible filesystem for /org/freedesktop/Hal/devices/volume_part_1_size_339603456
manager.c/1686: Changed: /dev/hdc
manager.c/696: executing command: sound-juicer -d /dev/hdc

(sound-juicer:9954): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(sound-juicer:9954): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
This CD was not found.
manager.c/1619: New Device: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial
manager.c/1619: New Device: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0
manager.c/1619: New Device: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0_scsi_host
manager.c/1619: New Device: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0_scsi_host_scsi_de vice_lun0
manager.c/1619: New Device: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0_storage
manager.c/1642: not a mountable volume: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0_storage
manager.c/1686: Changed: /dev/sda
manager.c/1619: New Device: /org/freedesktop/Hal/devices/volume_uuid_8093_8F05
manager.c/1686: Changed: /dev/sda1
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_uuid_8093_8F05...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_uuid_8093_8F05
manager.c/1878: Mounted: /org/freedesktop/Hal/devices/volume_uuid_8093_8F05
manager.c/696: executing command: nautilus -n --no-desktop '/media/FLASH_DISK' 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/windoz ntfs umask=0222 0 0		
/dev/hda5 /media/switzerland vfat umask=000 0 0

---

