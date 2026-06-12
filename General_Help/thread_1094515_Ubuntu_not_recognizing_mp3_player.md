---
title: "Ubuntu not recognizing mp3 player"
date: 2009-03-12
forum: General Help
---

### Post by tegnoto89 on 2009-03-12
I have a Creative Zen Vplus, and when I plug it into the USB slot, nothing happens, except that the light on the mp3 player lights up.  It doesn't show up on "computer", even after refreshing  Can anybody help me out with this?

---

### Post by mb_webguy on 2009-03-12
Plug it in, and then enter the command "sudo fdisk -l" in the terminal to show all drives and partitions connected to your computer.  If you see an entry corresponding to your mp3 player, then it's being recognized but not mounted.  You can mount it using the commands "sudo mkdir /media/mp3; sudo mount /dev/*xxxn* /media/mp3" where *xxxn* is the device associated with the mp3 player, as shown in the output of the fdisk command.

To get it to mount automatically, you might have to add an entry in your fstab file.  If it's being detected, though, I don't know why it isn't being automatically mounted.

---

### Post by jacob01 on 2009-03-12
to transfer music to it if its being mounted:
download nomad 2 or open rhythmbox. on the side of rhythmbox you should find an icon saying zen or somthing similar. then just drag and drop music into it. For nomad just use it the same way you would an ftp.

---

### Post by tegnoto89 on 2009-03-12
This is what I'm getting for "sudo fdisk -l".  Do any of these look like an mp3 player?  I'm not sure what I'm looking for.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6951

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

```

---

### Post by jacob01 on 2009-03-12
im not sure if that last command will list your zen when i type that my zen does not show up. try ```
lsusb
```

---

### Post by tegnoto89 on 2009-03-12
> im not sure if that last command will list your zen when i type that my zen does not show up. try
Code:

lsusb



When I put that in, nothing happens?

---

### Post by tegnoto89 on 2009-03-15
3 day bumpski..  Anyone else have any thoughts?

---

### Post by sgosnell on 2009-03-16
It can take awhile before the device shows up.  Have you waited 30 seconds or so before checking for the device?  It's also possible the cable is faulty.  Does it work on other computers?  The USB port on your PC could also be bad.  Do other USB devices work reliably?  It's possible the power pins are fine but not the data pins.

Just shots in the dark, but it's all I have for now.

---

### Post by todak on 2009-03-16
Install Gnomad ```
sudo apt-get install gnomad2
``` After it is installed, first plug the player into the USB port and then start Gnomad.

---

### Post by perrti-y02 on 2009-03-16
Gnomad2 is vital if you actually want to out anything onto a creative player. I presume they use proprietary drivers because it isn't found in the same way that a usb stick is.

---

### Post by tegnoto89 on 2009-03-28
Okay, Gnomad2 is not recognizing a jukebox.  UPDATE: Windows will recognize the player when it's set as a removable disk, but not when it isn't.  Ubuntu (with or without gnomad) will not recognize either the mp3 player or the "removable disc".


Any other ideas?  This is very frustrating indeed..

---

### Post by tegnoto89 on 2009-03-30
Scratch that; works fine with windows.  Ubuntu still won't recognize it at all.  I've tried Gnomad2 and kzenexplorer.

---

### Post by tegnoto89 on 2009-03-31
Bump

---

### Post by coldmack on 2009-03-31
I am not sure if you guys actually factored in the fact the Creative players are MTP players, so the user would need some sort of plugin/add on that will allow the OS to recognize the MTP protocol?

---

### Post by tegnoto89 on 2009-03-31
I don't know if I should note that my lsusb output is:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 004: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000  

```

Also, when I open gnomad2 or kzenexplorer (tried both) with nothing plugged into the USB, it immediately says no jukebox found; when my player is in, it takes a few minutes, then tells me there's no jukebox found.

---

