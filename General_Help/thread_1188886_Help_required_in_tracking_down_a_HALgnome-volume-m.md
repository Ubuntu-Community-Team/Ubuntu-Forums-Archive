---
title: "Help required in tracking down a HAL/gnome-volume-manager issue"
date: 2009-06-16
forum: General Help
---

### Post by Azdour on 2009-06-16
Hi All

Is this the correct place to ask in-depth questions about the workings of HAL and gnome-volume-manager?

I would like to know how I can debug these to try and resolve an issue with USB mounting for a specific user.

If I log in as user1 I can mount USB's. If I switch and log in as user2 I cannot mount USB's... so it seems its a software issue not a hardware one. Both users belong to the plugdev group.

HAL recognizes the Corsair USB stick, as it appears in the lshal listing. But it appears labeled as a USB Drive rather than Corsair under Places | Computer - clicking on it returns the message that it cannot mount the file.

If I run gmount from the command line it mounts correctly, but I want to try and resolve why HAL and gnome-volume-manager are not working correctly.

Are there any logs I an look at or generate to try and isolate this problem?

I been trying to work out what the issue is for some time now, so any help would be greatly appreciated.

---

### Post by sdennie on 2009-06-16
I don't have a solution but, I can offer another debugging tool.  The interaction between HAL and volume managers usually happens via dbus.  Try using dbus-monitor while plugging in the drive and see if you notice any differences between the two users.

---

### Post by Azdour on 2009-06-17
Hi,

Thanks for the dbus-monitor information, is does reveal a difference but unfortunately I'm not able to determine why.

I ran dbus-monitor with a user who could mount the USB and copied the dbus info to a file to compare with the other user.

When I logged in as the other user and used dbus-monitor the dbus information stopped at:

signal sender=:1.1 -> dest=(null destination) path=/org/freedesktop/Hal/devices/storage_serial_Corsair_Flash_Voyager_000802218427B87A132E_0_0; interface=org.freedesktop.Hal.Device; member=PropertyModified
   int32 1
   array [
      struct {
         string "info.interfaces"
         boolean false
         boolean true
      }
   ]

Where as with the user that could mount, it proceeded past that point onto:

signal sender=:1.1 -> dest=(null destination) path=/org/freedesktop/Hal/Manager; interface=org.freedesktop.Hal.Manager; member=DeviceAdded
   string "/org/freedesktop/Hal/devices/volume_uuid_F04C_4288"

etc...

I'm now wondering why it stops.

---

