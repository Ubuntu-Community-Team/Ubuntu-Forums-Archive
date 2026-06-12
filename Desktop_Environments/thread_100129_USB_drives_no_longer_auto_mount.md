---
title: "USB drives no longer auto mount"
date: 2005-12-06
forum: Desktop Environments
---

### Post by firenurse4 on 2005-12-06
I am running Breezy and now for some reason none of my usb drives will auto mount when plugged in. ***I can mount them manually***.  There has been no changes to my fstab file and the pertinent line is as follows.

```
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
```

The only thing different on my system have been secuity updates but I honestly can't remember what they were for or how long ago.

So my question is has anyone else had this problem recently.  And if so, what was the solution.

Thanks
](*,)

---

### Post by firenurse4 on 2005-12-07
Well my backup computer also running Breezy auto mounts just fine.  I noticed that they had diverent versions of pmount so I downgraded my main box to the same version as the one that is working. The results...
](*,) ](*,) ](*,) ](*,) 
Will keep trying but this is turning into a real pain.

---

### Post by firenurse4 on 2005-12-07
Well my temp. work around was to remove the /dev/sda line from fstab and to manually mount using pmount.  This will work ok for me but not for my wife and granddaughter who will be using this system.  Any suggestions welcome.

---

### Post by Sokraates on 2005-12-07
I don't really know if this will help you, but try deleting /etc/udev/rules.d/10-custom.rules (after a backup, of course).

You've probably generated that file under Hoary to access Palm-devices. Problem is, with Breezy devices listed in this file will no longer be recognized. I also had my digicam listed and it wouldn't work in PTP-mode (though it was mounted correctly if set to "mass storage").

It's worth a try.

---

### Post by firenurse4 on 2005-12-07
[QUOTE=Sokraates]I don't really know if this will help you, but try deleting /etc/udev/rules.d/10-custom.rules (after a backup, of course).

You've probably generated that file under Hoary to access Palm-devices. Problem is, with Breezy devices listed in this file will no longer be recognized. I also had my digicam listed and it wouldn't work in PTP-mode (though it was mounted correctly if set to "mass storage").

It's worth a try.[/QUOTE]

Well there was on 10-custom.rules file there.

I created a launcher to run the pmount command without typing it in the terminal so that shoul help for now.

Thanks.

---

### Post by firenurse4 on 2005-12-07
I thought this was weird before, now after some more testing I have no idea where to go now.

When I plug in my card reader, it shows up as a device under the disk mounter applete. The media does not mount automatically.  In order to read from the card, the card must be inserted before being plugged into a USB port.  If you try to insert a card after the reader is plugged in, it will not mount. I get this error message.
 ```
ERROR: given UDI is not a mountable volume
```

The drives will mount manually but not as a hotplug. I tried reinstalling hotplug but no change there. The only difference I found so far between the box that works normally and the borked one was that HAL and ROOT were in the Plugdev's group on the box that works. Adding them into the other box was no help.

Any ideas on where to go from here?

---

### Post by kingsidy on 2005-12-07
I have two USB flashdrives. The sandisk cruiser will mount automatically. The Lexar used to mount automatically, but now whenever i connect it, i have to mount manually. Isn't it funny that one works while the other does not

---

### Post by firenurse4 on 2005-12-07
\\:D/

[COLOR="Blue"]**Solution Found!!!**[/COLOR]

Well the last thing I thought to try worked. The problem was with Gnome-volume-manger.  This is the daemon that apprently is supposed to auto mount drives.  What I did was first to uninstall that program.  I rebooted (proably not necessary step in Linux) and the drives were showing up in the Disk Mount Applete.  Still has to mount them but this was progress. Also, the Card reader worked like it should.  I reinstalled the daemon (gnome-volume-manager) and now the system works as it should.

I have no idea what was messed up or how it happened, but I did get it fixed.

---

