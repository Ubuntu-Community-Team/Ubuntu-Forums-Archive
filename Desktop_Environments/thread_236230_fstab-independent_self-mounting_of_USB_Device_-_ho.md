---
title: "fstab-independent self-mounting of USB Device - how?"
date: 2006-08-14
forum: Desktop Environments
---

### Post by jackn on 2006-08-14
My USB MP3 Player mounts automatically when plugged in (/dev/sda1 to /media/player_name).

It is not listed in /etc/fstab, however.

Would like to learn more about how this is done and perhaps tweak it, or shift to manual mount through fstab.

Specifically:
*How is the USB device mounted? Command? File? Options and tweaking?
*Can the automatic mounting of USB devices be overridden by adding the device to the /etc/fstab file?

Have done a great deal of research, and still can't figure out where and how it's done in Ubuntu.
A good reference will do, as you like.

Jackn

---

### Post by jackn on 2006-08-18
OK, some headway.


[computx]("http://www.ubuntuforums.org/showthre...ight=usb+fstab") refers to a [solution]("http://computx.us/blog/index.php?/ar...r-and-win.html") by Alex Fleak.
Thanks a bunch to computx, dfa_geko and to Alex Fleak.

First, some observations. Then, below, references for those who would like to pursue this further, as the system remains less than fully clear, and access to it limited.

[LIST]
[*]How fstab-independent mounting works:
fstab-independent mounting is based on 'hal' (Hardware Abstration Layer), whatever that is, available since the 2.6 kernel. This is explained by Martin Pitt in the man pages for 'pmount-hal'.
Basically, removeable USB devices are simply mounted using the 'pmount' command:
'("policy mount") is a wrapper around the standard mount program which
permits normal users to mount removable devices without a matching /etc/fstab entry'
'pmount-hal extends pmount by making it work together with hal (Hardware Abstration Layer).'
Does this mean that removable devices are mounted with all the defaults ('async,atime,nodev,noexec,noauto,nosuid,user,rw') of a typical 'pmount' command? Indeed, you don't need to be root and you can read your USB device and write to it when it self-mounts. For all I know, however, 'pmount-hal' may be using 'pmount' switches, or somehow constrain 'pmount'.
Where can one obtain this information?
[/LIST]

[LIST]
[*]Some limited configuration of the mounting of USB removable devices

Some access to settings with removable devices can be had through a GUI. This GUI is launched by running 'gnome-volume-properties' in CLI (or System>Preferences>Removable Devices and Media from the menus).

The GUI allows limited control. Used it, for example, to stop the system from browsing the mounted device automatically, as like to work from the CLI. The GUI includes tabs for CD's, DVD's, PDA's, and storage (including MP3 players) and input devices.
[/LIST]

[LIST]
[*]/etc/fstab listing overrules mounting with pmount-hal

Listing of a removable USB device in /etc/fstab overrides self-mounting. Upon removal of the entry from fstab, the device will self-mount.
When the device doesn't mount, then, one possible cause is that it is listed in /etc/fstab (which might happen if it was plugged-in during the installation, and, as a result, taken by the system not to be a removabale device).
There's something strange here, however:
In 'man pmount', it says:
'... if it (the device) is (in /etc/fstab), 'pmount' executes  'mount  device' as the calling user to handle this transparently.'
I therefore expected removable devices to mount according to an /etc/fstab entry when plugged in.
Yet, when I list an entry in /etc/fstab, no mounting occurs at all. [/LIST]
[LIST]
[*]Viewing the detailed parameters of your USB device and settings for its mounting
```
lshal|less 
```allows you to list and conveniently view all devices handled by 'hal'. As with any 'less'-viewed file, typing '/' at the cursor then will allow you to search for any string typed after the forward slash. You can thus find the USB device of your interest in the list, and see whether and how it is handled by 'hal'.
Such details about your USB device can also be viewed through the GUI:
'hal-device-manager' from the CLI (or System>Administration-Device Manager from the menus) allows you to view the properties of your device as above.
In particular, you can find the usb_device.linux.sysfs_path parameter in the 'hal' listing. This reads something like  /sys/devices/pci0000:00/0000:00: 1f.2/usb1/1-2/1-2.2, depending on the particular device.
This directory can in turn be listed and files in it modified.
There is one excellent, authoritative and detailed [source]("http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD#device-properties-pcmcia_socket") for the meaning of all the variables listed in 'hal'.
[/LIST]


[LIST]
[*]Making a USB device self-mount
[Alex Fleak]("http://computx.us/blog/index.php?/ar...r-and-win.html") wanted to make a removable USB device self-mount. For some reason, the system wasn't doing it itself. According to him, for a USB device to self-mount with pmount-hal, an entry is needed in /etc/hal/fdi/policy/preferences.fdi. The/preferences.fdi file provides examples for entries. Alternatively, an independent file, modeled on the /preferences.fdi examples, can be set up in the /etc/hal/fdi/policy directory. An [example]("http://computx.us/blog/uploads/21-flash-reader.fdi") of an independent file is provided by Alex Fleak. 
Finally, Alex Fleak adds, the device name must be added to /etc/pmount.allow. To find the device name, you need to plug it in, and run 'demsg' in the CLI. The output will include a device name. MP3 players are usually /dev/sda1, for example. 

joft [indicates]("http://www.ubuntuforums.org/showthread.php?t=221462") some detail about the /etc/hal/fdi/policy/preferences.fdi-type file to be created. He has created a harddisk.fdi file in the /policy directory in order to mount a harddisk. If the variables listed there, such as 'volume.uuid' match the mounted volume, a 'merge' event will take place, namely the mounting. The mountpoint can be set with the 'merge key' variable.

The /preferences.fdi file discussed here allows the user to tweak things if the default hotplugging setup of his/her device is not to their liking. It still remains a mystery to me, however, where the default settings for the different removable media are stored.
[/LIST]
[LIST]
[*] Setting the mountpoint anywhere you like
The 'pmount' protocol used in hotplugging only allows mounting under /media. It is possible however to set a mountpoint anywhere you like by creating a symbolic link to the desied mountpoint ([post #4]("http://www.ubuntuforums.org/showthread.php?t=221462")).
[/LIST]

References:
hal [secrets]("http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD") exposed
[hal]("http://www.freedesktop.org/wiki/Software_2fhal") mailing lists and source code
A detailed [description]("http://www.redhat.com/magazine/003jan05/features/hal/#fdi") of the configuration in RedHat, which only partly applies to things in Ubuntu


Jackn

---

### Post by christhemonkey on 2006-08-18
I'm gonna give the cop out answer:
```
sudo mkdir /media/usbdisk
sudo mount -t vfat /dev/sda1 /media/usbdisk 
```

---

### Post by waldschm on 2006-08-18
man pmount
is handy, don't know if you've checked it out. It names a file /etc/pmount.allow for additional devices as well as criteria for successful mounting using pmount.

---

### Post by gostal on 2006-09-05
> **hroit said:**
> OK, some headway.


[computx]("http://www.ubuntuforums.org/showthre...ight=usb+fstab") refers to a [solution]("http://computx.us/blog/index.php?/ar...r-and-win.html") by Alex Fleak.
Thanks a bunch to computx, dfa_geko and to Alex Fleak.

First, some observations. Then, below, references for those who would like to pursue this further, as the system remains less than fully clear, and access to it limited.

[LIST]
[*]How fstab-independent mounting works:
fstab-independent mounting is based on 'hal' (Hardware Abstration Layer), whatever that is, available since the 2.6 kernel. This is explained by Martin Pitt in the man pages for 'pmount-hal'.
Basically, removeable USB devices are simply mounted using the 'pmount' command:
'("policy mount") is a wrapper around the standard mount program which
permits normal users to mount removable devices without a matching /etc/fstab entry'
'pmount-hal extends pmount by making it work together with hal (Hardware Abstration Layer).'
Does this mean that removable devices are mounted with all the defaults ('async,atime,nodev,noexec,noauto,nosuid,user,rw') of a typical 'pmount' command? Indeed, you don't need to be root and you can read your USB device and write to it when it self-mounts. For all I know, however, 'pmount-hal' may be using 'pmount' switches, or somehow constrain 'pmount'.
Where can one obtain this information?
[/LIST]

[LIST]
[*]Some limited configuration of the mounting of USB removable devices

Some access to settings with removable devices can be had through a GUI. This GUI is launched by running 'gnome-volume-properties' in CLI (or System>Preferences>Removable Devices and Media from the menus).

The GUI allows limited control. Used it, for example, to stop the system from browsing the mounted device automatically, as like to work from the CLI. The GUI includes tabs for CD's, DVD's, PDA's, and storage (including MP3 players) and input devices.
[/LIST]

[LIST]
[*]/etc/fstab listing overrules mounting with pmount-hal

Listing of a removable USB device in /etc/fstab overrides self-mounting. Upon removal of the entry from fstab, the device will self-mount.
When the device doesn't mount, then, one possible cause is that it is listed in /etc/fstab (which might happen if it was plugged-in during the installation, and, as a result, taken by the system not to be a removabale device).
There's something strange here, however:
In 'man pmount', it says:
'... if it (the device) is (in /etc/fstab), 'pmount' executes  'mount  device' as the calling user to handle this transparently.'
I therefore expected removable devices to mount according to an /etc/fstab entry when plugged in.
Yet, when I list an entry in /etc/fstab, no mounting occurs at all. [/LIST]
[LIST]
[*]Viewing the detailed parameters of your USB device and settings for its mounting
```
lshal|less 
```allows you to list and conveniently view all devices handled by 'hal'. As with any 'less'-viewed file, typing '/' at the cursor then will allow you to search for any string typed after the forward slash. You can thus find the USB device of your interest in the list, and see whether and how it is handled by 'hal'.
Such details about your USB device can also be viewed through the GUI:
'hal-device-manager' from the CLI (or System>Administration-Device Manager from the menus) allows you to view the properties of your device as above.
In particular, you can find the usb_device.linux.sysfs_path parameter in the 'hal' listing. This reads something like  /sys/devices/pci0000:00/0000:00: 1f.2/usb1/1-2/1-2.2, depending on the particular device.
This directory can in turn be listed and files in it modified.
There is one excellent, authoritative and detailed [source]("http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD#device-properties-pcmcia_socket") for the meaning of all the variables listed in 'hal'.
[/LIST]


[LIST]
[*]Making a USB device self-mount
[Alex Fleak]("http://computx.us/blog/index.php?/ar...r-and-win.html") wanted to make a removable USB device self-mount. For some reason, the system wasn't doing it itself. According to him, for a USB device to self-mount with pmount-hal, an entry is needed in /etc/hal/fdi/policy/preferences.fdi. The/preferences.fdi file provides examples for entries. Alternatively, an independent file, modeled on the /preferences.fdi examples, can be set up in the /etc/hal/fdi/policy directory. An [example]("http://computx.us/blog/uploads/21-flash-reader.fdi") of an independent file is provided by Alex Fleak. 
Finally, Alex Fleak adds, the device name must be added to /etc/pmount.allow. To find the device name, you need to plug it in, and run 'demsg' in the CLI. The output will include a device name. MP3 players are usually /dev/sda1, for example. 

joft [indicates]("http://www.ubuntuforums.org/showthread.php?t=221462") some detail about the /etc/hal/fdi/policy/preferences.fdi-type file to be created. He has created a harddisk.fdi file in the /policy directory in order to mount a harddisk. If the variables listed there, such as 'volume.uuid' match the mounted volume, a 'merge' event will take place, namely the mounting. The mountpoint can be set with the 'merge key' variable.

The /preferences.fdi file discussed here allows the user to tweak things if the default hotplugging setup of his/her device is not to their liking. It still remains a mystery to me, however, where the default settings for the different removable media are stored.
[/LIST]
[LIST]
[*] Setting the mountpoint anywhere you like
The 'pmount' protocol used in hotplugging only allows mounting under /media. It is possible however to set a mountpoint anywhere you like by creating a symbolic link to the desied mountpoint ([post #4]("http://www.ubuntuforums.org/showthread.php?t=221462")).
[/LIST]

References:
hal [secrets]("http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD") exposed
[hal]("http://www.freedesktop.org/wiki/Software_2fhal") mailing lists and source code
A detailed [description]("http://www.redhat.com/magazine/003jan05/features/hal/#fdi") of the configuration in RedHat, which only partly applies to things in Ubuntu


Jackn

Regarding where default options are stored this should be the various .fdi-files located at /usr/share/hal/fdi/policy/10osvendor/ Something odd is going on, though. My LaCie USB external hard drive automounts with iocharset=utf8. But since fstype is vfat I want iso8859-1 and I've tried hard to get it but sofar no success. Editing the files 10-storage-policy.fdi and 20-storage-methods.fdi does not give iso8859-1 which is apparent from /etc/mtab:```
cat /etc/mtab
```

...snip
/dev/sda1 /media/LACIE vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=2627,gid=1000,umask=077,iocharset=utf8 0 0
....end snip

but my changes are apparently read and are duly reported by the system as is evident both from gnome-volume-manager and the output from```
lshal
```

...snip
udi = '/org/freedesktop/Hal/devices/volume_uuid_6853_5BA9'
  volume.policy.mount_option.iocharset=iso8859-1 = true  (bool)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'iso8859-1', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid='} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-system-storage-mount', 'hal-system-storage-unmount', 'hal-system-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  volume.ignore = false  (bool)
  volume.policy.desired_mount_point = 'LACIE'  (string)
  volume.policy.mount_filesystem = 'vfat'  (string)
  volume.policy.should_mount = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_6853_5BA9'  (string)
  volume.partition.msdos_part_table_type = 12  (0xc)  (int)
  info.product = 'LACIE'  (string)
  volume.size = 250056705024  (0x3a388a8400)  (uint64)
  volume.num_blocks = 488392002  (0x1d1c4542)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_mounted = true  (bool)
  volume.mount_point = '/media/LACIE'  (string)
  volume.label = 'LACIE'  (string)
  volume.uuid = '6853-5BA9'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'vfat'  (string)
  storage.model = ''  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SEAGATE_ST3250823A_10000E000A7A546F'  (string)
  block.is_volume = true  (bool)
  block.minor = 1  (0x1)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sda1'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SEAGATE_ST3250823A_10000E000A7A546F'  (string)
  linux.sysfs_path_device = '/sys/block/sda/sda1'  (string)
  linux.sysfs_path = '/sys/block/sda/sda1'  (string)
...end snip

For some reason the iocharset option is ignored by the mounting process and I'm at my wits end. Even odder is that I had exactly the same problem running Mandriva Free 2006 some months ago but then the matter was indeed solved by tweaking corresponding policy files. To be exact the file controlling this particular mount option was /usr/share/hal/fdi/30osvendor/locale-policy.fdi and the pertinent lines were```
<match key="volume.fstype" string="vfat">
		<merge key="volume.policy.mount_option.iocharset=iso8859-1"
type="bool">true</merge>
```

So still there is a mystery regarding how Ubuntu handles these mount options and unveiling this would be greatly appreciated.

Gösta

---

### Post by jackn on 2006-09-05
> **gostal said:**
> Regarding where default options are stored this should be the various .fdi-files located at /usr/share/hal/fdi/policy/10osvendor/ 




I didn't know about the hal config files, this is excellent news. Thanks, Gostal.

As to your issue, I really don't know enough to be useful to you, I'm afraid, but here's what occurs to me, for what's it's worth.
a. Do you know for a fact that you've got "iocharset=iso8859-1" on your system, and that you can use it? In other words, if the mounting of the disk is not involved, do you have any other way of testing whether you can use it on a FAT fs, on your configuration?
b. How about a direct remount using iocharset=iso8859-1? 
In other words, 
```
 mount -t vfat -o remount -o rw /dev/sda1 /media/LACIE
```

It seems like the iocharset is not needed here, as vfat is mounted with it by default, according to 'man mount'. Of course '-o iocharset=iso8859-1' could be tested, too.

This is not a solution to your precise issue, but it just might allow you to get the right charset.

Is that silly?

What is the outcome?

Thanks again, Gostal, for this great input as to the whereabouts of the 'hal' config files. Please forgive me if this is too elementary....

Jackn

---

### Post by gostal on 2006-09-06
Manually mounting the drive and putting relevant options in /etc/fstab will probably get me what I want in terms of mounting options but then automounting destroyed or at least should be but then again strange things are going on and I haven't tried it yet. And yes iso8859-1 is available on the system. I tried remounting with iso8859-1 as an otion but then I got both iocharsets which I beleive would cause interpretation problems. Well, till the mist clears regarding the automounting issue I suppose I'll have to use manual mounting. 

Best wishes!
Gösta

---

### Post by jackn on 2006-09-06
> **gostal said:**
> Manually mounting the drive and putting relevant options in /etc/fstab will probably get me what I want in terms of mounting options but then automounting destroyed or at least should be. 
Gösta

No, no /etc/fstab. Please read post #2.

*Once a drive is self-mounted*, it can be mount -o remount(ed), with your options, and *without* an fstab entry, that's what I'm talking about it. Indeed, it is perhaps counterintuitive.
You can have your cake and it it too, that is self-mount and personal settings without an fstab entry.
I wonder, first, whether it works in your case, and, secondly, how one would go about automating it  -  putting the remount in the startup files wouldn't work, as often the drive would not be there to begin with. But maybe that's no big deal, just a regular error message (which can be redirected to /dev/null anyway).

Jackn

---

### Post by gostal on 2006-09-07
> **hroit said:**
> No, no /etc/fstab. Please read post #2.

*Once a drive is self-mounted*, it can be mount -o remount(ed), with your options, and *without* an fstab entry, that's what I'm talking about it. Indeed, it is perhaps counterintuitive.
You can have your cake and it it too, that is self-mount and personal settings without an fstab entry.
I wonder, first, whether it works in your case, and, secondly, how one would go about automating it  -  putting the remount in the startup files wouldn't work, as often the drive would not be there to begin with. But maybe that's no big deal, just a regular error message (which can be redirected to /dev/null anyway).

Jackn
I wonder, too, for several reasons. In fact I seriously doubt it will work. 

1: the drive automounts painlessly which means that I have to unmount it to get rid of utf8 and I see no easy way to automate that. mount -o desiredOption,remount only adds the desired option hence the two iocharset options ...

2: I now know exactly what's going on. It turns out that mounting options are hard coded into pmount/pmount-hal. See the following URLs:

[http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.html]("http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.html")
and
[http://www.ubuntuforums.org/showthread.php?t=107892&highlight=hal+default+mount+options]("http://www.ubuntuforums.org/showthread.php?t=107892&highlight=hal+default+mount+options")

Any tricks involving pmount will then keep utf8.

For solutions I see two possibilities:

1: get rid of gnome-volume-manager and pmount which hopefully means that hal gets to do the mounting but then I probably would have to add a program that dynamically updates /etc/fstab. This is the approach taken by Mandriva which I used earlier.

2: modify the sources and recompile pmount. This approach was taken by joft see URL 2 above. 

Hard coded options aren't really options anymore and this warrants some thought. Certainly the kernel spits out a warning message that utf8 isn't such a great choice for vfat:
```

dmesg
....
[17180090.384000] USB Mass Storage support registered.
[17180095.384000]   Vendor: SEAGATE   Model: ST3250823A        Rev: 3.03
[17180095.384000]   Type:   Direct-Access                      ANSI SCSI revisio n: 02
[17180095.408000] usb-storage: device scan complete
[17180095.500000] Driver 'sd' needs updating - please use bus_type methods
[17180095.504000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17180095.504000] sda: assuming drive cache: write through
[17180095.504000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17180095.504000] sda: assuming drive cache: write through
[17180095.504000]  sda: sda1
[17180095.576000] sd 0:0:0:0: Attached scsi disk sda
[17180095.596000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180096.044000] FAT: utf8 is not a recommended IO charset for FAT filesystems,  filesystem will be case sensitive!
```

On the other hand it could be that either vfat or utf8 has improved since my earlier bad experience. With utf8 some files and directories created using WinXP simply didn't show up. iso8859-1 was necessary to get this right. Also with utf8 I couldn't write to FAT volumes. Case sensitivity I could live with but it really was much worse than that. But that was half a year ago. I find it hard to believe, though, that the kernel people would be caught with their pants down regarding file system drivers and that utf8 and vfat isn't really an issue anymore but hard coding such options isn't something one would do without good reason either. I'll do some more research into the matter and se if I can dig up something more of interest.

I also read post 2 again and I'm none the wizer, really. The point using pmount is to allow a user without root privileges to mount a device without an fstab entry and pmount-hal makes this happen automatically by co-operating with hal. Certainly I can mount a device with desired options without an fstab entry anyway. All it takes is a looong command line. :-). I can skip the root privileges too by adding the user to the disk group and possibly I would have to create another group to handle mount point permissions. I haven't tried it but I'm possitive it would work. So the big deal with pmount really is the automation but then we're back at square one.

Thanks for an interesting discussion so far.

Gösta

---

