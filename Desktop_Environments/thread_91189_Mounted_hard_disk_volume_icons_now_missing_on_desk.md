---
title: "Mounted hard disk volume icons now missing on desktop"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Ian Edmont on 2005-11-16
Hi,

Can anyone offer any advice on how to get these back please?

The 'Show device icons' check box is ticked in System Settings | Desktop | Behaviour as is the 'Mounted Hard Disk Volume' check box.

/media directory contains /cdrom, /cdrom0, /floppy, /floppy0, /hda1, /hda7 and /hda8.

Partitions are all mounted but no device icons on the desktop.

Being new to Linux, I'm fearing that it may have something to do with the fact that I have deleted the /mnt directory (also removed from the wastebin) as when I was exploring the directory structure it first appeared that this directory was empty and I therefore removed it. Is this a possibility I wonder?

Hoping someone can offer some advice as to how to get these device icons showing on the desktop again.

Do I need to re-create the /mnt directory. If so, can someone please explain how to do this?

I suppose I have learnt one thing here ... if in doubt, LEAVE alone!!!!

Many thanks.

Ian Edmont.

---

### Post by earobinson on 2005-11-16
Applications -> System Tools -> Configuration Editor

Then go to apps - nautilus - desktop make sure volumes_visible is checked

Also you should just be able to reacreate that dir. And there is nothing wrong with playing around with your computer as long as it dont need to work all the time, i learn the most while breaking my computer :P

---

### Post by Ian Edmont on 2005-11-17
Thanks for the reply earobinson.

Please excuse my ignorance but I'm actually using Kubuntu and thought nautilus was part of the GNOME desktop environment and so I don't currently have that installed.

I'm at work at the moment (away from my linux machine). Please accept my apologies if I am talking total rubbish.

Once again, thanks for the reply.

Ian Edmont.

---

### Post by f1dave on 2005-11-17
Right click desktop -> configure desktop -> behaviour -> show icons on desktop. 

Then select which file and device icons you would like displayed under the file and device tabs.

---

### Post by Ian Edmont on 2005-11-17
Thanks David but I've already checked this as per my original post.

Ian Edmont.

---

### Post by f1dave on 2005-11-17
*smacks head* sorry about that, completely missed it.

---

### Post by Ian Edmont on 2005-11-17
No problem, easy done.

Anyone any other ideas please? Is it maybe a bug that I should report?

Ian Edmont.

---

### Post by earobinson on 2005-11-17
[QUOTE=Ian Edmont]Thanks for the reply earobinson.

Please excuse my ignorance but I'm actually using Kubuntu and thought nautilus was part of the GNOME desktop environment and so I don't currently have that installed.

I'm at work at the moment (away from my linux machine). Please accept my apologies if I am talking total rubbish.

Once again, thanks for the reply.

Ian Edmont.[/QUOTE]
lol sorry about that my bad i dident read the thread location just slammed out a responce.

---

### Post by bin on 2005-11-17
[QUOTE=Ian Edmont]Hi,

Do I need to re-create the /mnt directory. If so, can someone please explain how to do this?

I suppose I have learnt one thing here ... if in doubt, LEAVE alone!!!!
[/QUOTE]

Indeed :) :) :) 

Don't know if it'll help but to recreate mnt:-

sudo -s
password
cd /
mkdir mnt
chmod +755 mnt

Like I said I don't know if it'll fix your problem as by the look of it devicesa re mounted under media rather than mnt - but see how it goes

in light

bin

---

### Post by ajgreeny on 2005-11-17
Just thought I'd let you know that I have the same problem with loss of mounted disk icons in breezy.  The only one that does show is floppy, and that is not even mounted.

I have not removed /mnt, however and although I do not use it I do have gnome and nautilus installed.   I have used apt-get to install KDE and kubuntu-desktop so I suppose I have the same as Kubuntu, with added gnome bits and peices.

I have hoary on a separate drive (just in case I had problems with breezy, which I do slightly) and drive icons are all there in that version.

Any clues?

---

### Post by Ian Edmont on 2005-11-17
[QUOTE=bin]Indeed :) :) :) 

Don't know if it'll help but to recreate mnt:-

sudo -s
password
cd /
mkdir mnt
chmod +755 mnt

Like I said I don't know if it'll fix your problem as by the look of it devicesa re mounted under media rather than mnt - but see how it goes

in light

bin[/QUOTE]
Thanks for that bin.

I'm now back at home on my linux machine now but I installed Mandriva 2006 last night and Lilo's boot menu does not show my Ubuntu entry :( 

So back into Windows to try and find a solution for that and then I can test out your suggested solution. Will post back when done!

Thanks again.

Ian Edmont.

---

### Post by Ian Edmont on 2005-11-17
[QUOTE=bin]Indeed :) :) :) 

Don't know if it'll help but to recreate mnt:-

sudo -s
password
cd /
mkdir mnt
chmod +755 mnt

Like I said I don't know if it'll fix your problem as by the look of it devicesa re mounted under media rather than mnt - but see how it goes

in light

bin[/QUOTE]
No good bin ... Tried your suggestion, rebooted and still nothing.

Ian Edmont.

---

### Post by Quacka on 2005-11-18
[QUOTE=ajgreeny]Just thought I'd let you know that I have the same problem with loss of mounted disk icons in breezy.  The only one that does show is floppy, and that is not even mounted.

I have not removed /mnt, however and although I do not use it I do have gnome and nautilus installed.   I have used apt-get to install KDE and kubuntu-desktop so I suppose I have the same as Kubuntu, with added gnome bits and peices.

I have hoary on a separate drive (just in case I had problems with breezy, which I do slightly) and drive icons are all there in that version.

Any clues?[/QUOTE]
I have exactly the same problem. I can see the floppy-drive, but nothing else.
Very strange. 
I am a newby with linux, so I have no idea what to try.

It disappeared after I upgraded to breezy, so it have something to do with that.

---

### Post by Ian Edmont on 2005-11-29
[QUOTE=Quacka]I have exactly the same problem. I can see the floppy-drive, but nothing else.
Very strange. 
I am a newby with linux, so I have no idea what to try.

It disappeared after I upgraded to breezy, so it have something to do with that.[/QUOTE]
Just out of curiosity, has anyone found the reason for this and/or have a solution?

Thanks.

Ian Edmont.

---

### Post by earobinson on 2005-11-29
Not as of yet, have you bugzilled it?

---

### Post by Jens7677 on 2005-11-29
I think this problem is related to this one:
[http://ubuntuforums.org/showthread.php?t=95680](http://ubuntuforums.org/showthread.php?t=95680)

As I described I found a workaround here to show the fixed drives again, but I'm still living without smb-share icons on my desktop.

The workaround was:

> 
I found a temporary (I guess) solution. 
 I uncommented the last line of /etc/default/hal

 This is the result:
 
 # This will run the hal daemon as normal user 'hal' with some additional
 # privileges; This will not execute callout scripts as root (so fstab-sync
 # won't work) and makes hal unable to do filesystem type autodetection for
 # non-removable devices.
 DAEMON_OPTS=
 
 # This will run the hal daemon as user root 
 DAEMON_OPTS=--retain-privileges

---

### Post by denzilla on 2005-12-17
Just did a fresh install of Kubuntu, downloaded all updates and boom! I have this problem now. The only time the CD-ROM shows up in storage media is when a CD is in the tray and the Hard disk is missing completely! Anyone got a real fix yet? I was liking Kubuntu until this...

---

### Post by infoseeker on 2005-12-27
All my settings have been set to 'display mounted device icons' too and no mounted device icons are displayed :( , but I have inserted an audio CD and it DID bring up the desktop device icon.  After ejecting the CD the unmounted device icon remains on the desktop, although I did NOT select any unmounted devices.  Strange :confused:

---

### Post by Konge Odin on 2005-12-29
I had this problem myself after installing the latest kubuntu    for k7.
I also had it missing in the konqueror -> "hd"media tab. I    cant get my USB   creative Zen Nano Plus to show up either, but can see it mount when I survey the processes with "ps ax" command.
What  I did to be able to get my disks to show up was:
Right click on desktop ->
make new ->
Link to "unit"  ->
Hardisk.. 

Then   you   have a link for the unit you have placed manually on the desktop.
As you may have understood everything mounts, it just doesnt show up in the media window on the konqueror (except  for my DVD and cd rom plus my usb (Mp760) printer when its on), only on the desktop when you make the links yourself.
Hope it helps.

---

### Post by ghostdog on 2006-01-10
Doesn't the hard drive need to belong to the hal group? Such as cdrom or plugdev?

$sudo adduser hal disk

That completely solves the problem. :D

---

### Post by n0gabor on 2006-01-11
thanks man! its real solved now...

someone could inform the developers to inculde this as an update bugfix!

---

### Post by tassoman on 2006-01-16
[QUOTE=ghostdog]Doesn't the hard drive need to belong to the hal group? Such as cdrom or plugdev?

$sudo adduser hal disk

That completely solves the problem. :D[/QUOTE]

what do you mean for *disk*? 
The mount point? (/media/hdc1) or the device (/dev/hdc1)?

---

### Post by grinias on 2006-01-17
[QUOTE=tassoman]what do you mean for *disk*? 
The mount point? (/media/hdc1) or the device (/dev/hdc1)?[/QUOTE]

He means that you have to run in a konsole the command

```

$sudo adduser hal disk

```

then reboot and you will see your hard disk volumes on desktop!!!

Thanx to ghostdog!!!

---

### Post by JuanFerS on 2006-01-17
I had a link to each device... but now I can remove the links.

It worked, thanks!!

---

### Post by grinias on 2006-01-26
There is a minor drawback however. Now, my 120GB (4 FAT partitions) USB external disk does not mount and partition icons do not appear on the desktop until 
doing

```

$ sudo rmmod ehci_hcd

```

as I used to do with fedora core 3 and Hoary (ehci_hcd is the usb controller module).
There was not such a problem either before doing the trick or  while I was using a Gnome based Ubuntu Breezy installation. It is strange and i think that has to do with the interaction between kde and hal.

---

### Post by Pseudo_Nym on 2006-02-01
I had the same problem with device icons not displaying on my desltop after installing Kubuntu Breezy and doing a full upgrade including KDE 3.5.1. I tried ghostdog's solution: 

$sudo adduser hal disk

then rebooted but still no device icons were displayed on my desktop. So just for the hell of it I went into K>> System Settings>> Storage Media and under the Advanced tab unchecked "Enable HAL Backend" (which gave me a crash notice that I didn't note) I went back, rechecked the "Enable HAL Backend" and when I clicked apply my CD Writer and DVD icons magically appeared on my desktop as well as in the Strorage Media applet in the kicker.

I was excited until I inserted a disk neither disk was automounting as they did before. they started their disappearing act. and when I attempt to right click and select "mount" I get the following error:

Could not mount device.
The reported error was:
mount: block device /dev/hdc is write-protected. mounting read-only
mount: wrong fs type, bad option, baad superbllock on /dev/hdc.
missing codepage on other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Ok so now I was stummped again ... afterall I'm a linux newbie and don't have half a clue as to what I'm doing :P So again for the hell of it I right click the desktop and create a link to the device ( in this case my DVD-ROM) insert a DVD and am able to access the drive via the new link I created. But wait .. what is that I see? Could it be? Yes! Finally light at the end of the tunnel. For whatever reason the device icon for my DVD-ROM is now showig that it is mounted and is accessable when I click on it. So I delete the link to the device I just created and the device icon for the DVD both on the sektop and in the kickerapplet are functioning properly. So now as I write this I will attempt the same thing with the CD writer since it is still giving me an identical error when I try to access it ...

and the story continues ... I right clicked the desktop and selected Create New>> Link To Device>> CDWRITER Device tried inserting a few different disks attempting to mount them ... what's this I ask myself? no joy ... I was getting the same error again. Until instead of trying to double click the icon or mount the device from the right click menu I selected "open" from the right click menu and BOOM! a konqueror window appears displaying all the files on the disk in their full glory! Now when trying to open from the "default" CD Recorder icon i get an error message stating the device is busy. Ok, that's an improvment I think. so I go back to the link I created to it and eject the disk, reinsert it, dbl click the CD Recorder icon and no longer do I get an error, but a konqueror window showing nothing ... hmm .. what to do now? Perhaps delete the link I created? First I'll see what happens when I try openin git form there again .. well sure enough it displays the files. Eject the disk and delete the new link it is. *crosses his fingers* 

Well still no joy when trying to see what's on this disk, again I get an empty konqueror window, also I notice that when I right click the icon I do not get an option to mount or eject the disk (note that I do get these option on the icon in the kicker applet though when I try to mount it from there I get the device is write protected, mounting read-only it's already mounted or busy blah blah blah error).

At this point I'm giving up on the CD Recorder for ht enight ... keep in mind I still have not tried writing anthign to a CD on it and that may very well work ... I just don't know. Hopefully this issue will be addressed before to long.

---

### Post by grinias on 2006-02-06
I installed yesterday kd3 3.5.1 without any problem... Everything is where is
supposed to be on Desktop.

---

### Post by FlakJacket on 2006-02-06
I didn't realize I had this problem but I too am missing my hd desktop and media:/ icons.  I didn't notice i guess bc i usually work in konsole when i do system stuff so i don't access them through shortcuts anyway but does the above adduser command work without side effects for most?

Flak

---

### Post by hyperpsyched on 2006-02-10
I had the same problem... it was weird too because I could see the files using firefox but not Konq...

Tried "adduser hal disk" and while I can now see my drives I can see all my partitions including my NTFS WinXP partition and they all have long borg-like names like "S3DAAA... blah blah".

XP already nearly had me assimilated... please don't let kubuntu get me too.

Sooooo...

How can remove the link to my NTFS partition from the desktop?

---

### Post by ghostdog on 2006-02-10
[QUOTE=FlakJacket]I didn't realize I had this problem but I too am missing my hd desktop and media:/ icons.  I didn't notice i guess bc i usually work in konsole when i do system stuff so i don't access them through shortcuts anyway but does the above adduser command work without side effects for most?

Flak[/QUOTE]

The only side effect is that every device with group "disk" will be displayed on your desktop. 

I guess you can hack around "udev" to force certain disks to newly created groups. That way you can control what is displayed when you add hal to the device groups.

---

### Post by newuser111 on 2006-02-15
i also experienced this problem and did some reading

**sudo gpasswd -a <username> plugdev** is the correct command not sudo adduser hal disk


because (quoted from a webpage)  > If devices are not in the plugdev group, but rather in "disk",
the following features will not work:

- pmount will refuse to mount PCMCIA drives since they look like
  normal IDE adapters; mounting USB and FireWire devices will still
  work, though, because pmount then checks the sysfs ancestry for
  USB/FireWire nodes.

- Media checking will not work (e. g. hal will not recognize the
  insertion of a card into an USB card reader), because hal does not
  run in the "disk" group.

- hal will be unable to detect file systems and device labels on the
  removeable devices for the same reason (not being in "disk").

- Users will be unable to partition, format, and label their USB
  devices.

---

### Post by katiad on 2006-02-20
Well... I, too, have had this problem. Did a bit of experimenting... I tried 

> sudo gpasswd -a <username> plugdev

But it did nothing at all. None of my device icons would show up on the desktop, even hard disk volumes. 

So I tried, for the heck of it, sudo adduser hal - which did indeed make my hard drive volumes show up on the desktop, but I'm a bit leery of the effects that newuser111 noted. How do I 'undo' adding hal to the disk group? I was hoping that sudo adduser hal would not only add the hard disks to the storage media panel and desktop, but also cdrom devices, and my usb drive. Neither worked any better with hal added to the user group.

Actually, it seems none of my cds or usb drives will even automount in kde. I'm at a loss of what to do.

---

### Post by curley_sue on 2006-02-23
I guess it does not help the kubuntu users but the general idea:


sudo invoke-rc.d dbus restart
#the icons are restored but no auto-mounting for CDs, USBs etc
# so...
gnome-volume-manager &
# now I have auto-mount but the CD or USB do not appear on the Desktop as the used to...

here's the terminal output:

eldad@eldad:~$ manager.c/562: setting[0]: bool: autobrowse = 1
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

eldad@eldad:~$ manager.c/1619: New Device: /org/freedesktop/Hal/devices/volume_part_1_size_339603456
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
manager.c/1619: New Device: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0_scsi_host_scsi_device_lun0
manager.c/1619: New Device: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0_storage
manager.c/1642: not a mountable volume: /org/freedesktop/Hal/devices/usb_device_58f_9382_noserial_if0_storage
manager.c/1686: Changed: /dev/sda
manager.c/1619: New Device: /org/freedesktop/Hal/devices/volume_uuid_8093_8F05
manager.c/1686: Changed: /dev/sda1
manager.c/1258: mounting /org/freedesktop/Hal/devices/volume_uuid_8093_8F05...
manager.c/696: executing command: /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_uuid_8093_8F05
manager.c/1878: Mounted: /org/freedesktop/Hal/devices/volume_uuid_8093_8F05
manager.c/696: executing command: nautilus -n --no-desktop '/media/FlashDisk'

---

