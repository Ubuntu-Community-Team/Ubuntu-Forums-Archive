---
title: "Two simple PnP questions"
date: 2005-08-02
forum: Desktop Environments
---

### Post by maruchan on 2005-08-02
I have a printer question and a card reader question:

1. If I unplug my printer's USB cable from my PC, then plug it back in, I have to go to the control center and tell it to start the printer service again. Is there a way to have it auto-start?

2. If I plug a CF card from my camera into my card reader, it doesn't appear to mount unless I restart the computer. Then, after I take the card out, the icon is still there. Can I make the system handle this stuff automatically?

Thanks for any help with this.

---

### Post by cwaldbieser on 2005-08-02
This has something to do with the hotplug system.  If you can do a little shell scripting, you can probably solve both your problems.  "$ man hotplug" provides the gory details.  The basic idea is that when you plug or unplug a USB device, the hotplug system allows you to specify a script or scripts to run.  The ACTION environment variable is exported to your script (e.g. with the value "add" when plugging in).  You can then just have the script do what you would do manually (restarting the printer or mounting the USB device and creating the desktop icon).

If you aren't comfortable with shell scripting, I can try to help you out, or maybe someone else knows an easier way to get the system working?

---

### Post by maruchan on 2005-08-02
Thanks for the reply. I can do a teeny tiny bit of shell scripting, so I'd be more interested in that.

Would it be possible, for example, to detect a plugged in card or USB printer/scanner and show a message on the screen somewhere? That would be really groovy.

---

### Post by cwaldbieser on 2005-08-02
[QUOTE=maruchan]Thanks for the reply. I can do a teeny tiny bit of shell scripting, so I'd be more interested in that.

Would it be possible, for example, to detect a plugged in card or USB printer/scanner and show a message on the screen somewhere? That would be really groovy.[/QUOTE]

Short answer: yes.

Longer answer: There are really no constraints on what the triggered script can do as far as I can tell.  I am not exactly sure what you mean by "message" and "screen" in your example.  Here are several interpretations, all of which are possible:

+ An icon (message) is placed on the KDE desktop (screen).
+ A pop up window with a message saying "Your pen drive was plugged in." appears on your X display.
+ Your bash prompt prints a message above it that says "USB flash drive plugged in." on your console screen (no X in this case).

The trick is to first set up some maps in /etc/hotplug/usb.  There are probably already some scripts and maps in there (for scanners or digital cameras).  The map basically will have lines in it that have the name of the script to execute along with the USB device ID.  I forget the exact format, but Googling will probably turn it up.

You can find out the device IDs for your USB devices by plugging them in and typing "lsusb".

A simple script I did to make my flashdrive appear on my desktop:

```
#!/bin/bash

#If the USB device is not plugged in (e.g. during bootup), then skip trying to perform an action.
if [ -z "$(lsusb | grep 05dc:0080)" ]; then 
    exit 0
fi
if [ "$ACTION" = "add" ]; then
    #Sleep until the device becomes available.
    while [ ! -e /dev/sdb1 ]; do
        sleep 1
    done

    #Make the mount point and mount if it does not exist.
    mkdir -p /media/sdb1
    mount /dev/sdb1

    #Create the desktop icons on each user's desktop.
    for desktop in /home/*/Desktop
    do
        cat > "$desktop/USB Drive.desktop" << DRIVEFILE
[Desktop Entry]
Dev=/dev/sdb1
Encoding=UTF-8
Icon=hdd_mount
MountPoint=/media/sdb1
ReadOnly=false
Type=FSDevice
UnmountIcon=hdd_unmount
DRIVEFILE
    done
fi
``` 

I did this a long time ago-- I'd probably use "pmount" instead of "mount" today, so I wouldn't have to have an /etc/fstab entry for my USB drive.

---

