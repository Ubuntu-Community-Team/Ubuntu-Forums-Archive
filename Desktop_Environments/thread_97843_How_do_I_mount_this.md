---
title: "How do I mount this?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-01
I plugged in my iriver mp3 player and now I need to know how to mount it so I can put mp3's on it. There is an entry in /var/log/messages:

```
Dec  1 17:02:48 localhost kernel: [4294787.221000] usb 4-1: new high speed USB device using ehci_hcd and address 3
```

And dmesg gives me this:

```
[4294787.221000] usb 4-1: new high speed USB device using ehci_hcd and address 3
```

OK, I don't mind having to mount this mp3 player manually, but I need to know **how** to mount it. I know the command is something like:

```
sudo mount ? /mnt/mp3
```

But I need to know what to put in place of that question mark.
I tried mount /dev/sda1 /mnt/mp3 but there are no sda1, sdb2, etc. in /dev so I don't know the "device".
How do Ifind the device that this mp3 player is?

Any ideas?

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=ardchoille]I plugged in my iriver mp3 player and now I need to know how to mount it so I can put mp3's on it. There is an entry in /var/log/messages:

```
Dec  1 17:02:48 localhost kernel: [4294787.221000] usb 4-1: new high speed USB device using ehci_hcd and address 3
```

And dmesg gives me this:

```
[4294787.221000] usb 4-1: new high speed USB device using ehci_hcd and address 3
```

OK, I don't mind having to mount this mp3 player manually, but I need to know **how** to mount it. I know the command is something like:

```
sudo mount ? /mnt/mp3
```

But I need to know what to put in place of that question mark. Any ideas?[/QUOTE]

Did the dmesg also tell you what the device created was?  (e.g. /dev/sdb2).  What you want to do is:
```

$ sudo mount /dev/sdb2 /media/mp3

```
You can specify the type if you know it with -t (e.g. mount -t vfat /dev/sdb2 /media/mp3), but mount can guess the filesystem type many times.  You do need to specify the device if it's not in you /etc/fstab, though.

---

### Post by HermanAB on 2005-12-01
It is most likely FAT.  So try -t vfat

Something like:
mount  -t  vfat  /dev/sda1  /mnt/mp3

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by jasmuz on 2005-12-01
iRiver Mp3 players are not the standard mountable type Mp3 players. 

Check these applications to see what works for you:
ifp-line - command line tool to access iRiver iFP audio players
ifp-line-libifp - command line tool to access iRiver iFP audio players
iripdb - Generates the DB files for the iRiver iHP-1xx
libifp-dev - communicate with iRiver iFP audio devices (development files)
libifp4 - communicate with iRiver iFP audio devices
pmp-common - hotplug scripts for portable music players

---

### Post by ardchoille on 2005-12-01
[QUOTE=cwaldbieser]Did the dmesg also tell you what the device created was?  (e.g. /dev/sdb2).  What you want to do is:
```

$ sudo mount /dev/sdb2 /media/mp3

```
You can specify the type if you know it with -t (e.g. mount -t vfat /dev/sdb2 /media/mp3), but mount can guess the filesystem type many times.  You do need to specify the device if it's not in you /etc/fstab, though.[/QUOTE]
I cannot figure outhow to tell which device it is, that is the problem.

---

### Post by ardchoille on 2005-12-01
[QUOTE=HermanAB]It is most likely FAT.  So try -t vfat

Something like:
mount  -t  vfat  /dev/sda1  /mnt/mp3

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)[/QUOTE]
Yes, I could do that, but I don't know the device (/dev/?), so I cannot mount it and dmesg gives no hint about thwich device it is.

---

### Post by ardchoille on 2005-12-01
[QUOTE=jasmuz]iRiver Mp3 players are not the standard mountable type Mp3 players. 

Check these applications to see what works for you:
ifp-line - command line tool to access iRiver iFP audio players
ifp-line-libifp - command line tool to access iRiver iFP audio players
iripdb - Generates the DB files for the iRiver iHP-1xx
libifp-dev - communicate with iRiver iFP audio devices (development files)
libifp4 - communicate with iRiver iFP audio devices
pmp-common - hotplug scripts for portable music players[/QUOTE]
I tried installing ifp-line but the command was not dound when I tried to run it as both user and root. I tried installing ifp-line-libifp and the same thing happened. There is no way to run these apps after installing them.

---

### Post by aysiu on 2005-12-01
The command ```
sudo fdisk -l
``` will tell you what /dev it's at and what filesystem type it is.

---

### Post by ardchoille on 2005-12-01
[QUOTE=aysiu]The command ```
sudo fdisk -l
``` will tell you what /dev it's at and what filesystem type it is.[/QUOTE]
Can you tell which one it is in the sudo fdisk -l output below?

```
[ardchoille@~ 17:49:52]$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris
[ardchoille@~ 17:53:26]$
```

Because I am missing it.

---

### Post by aysiu on 2005-12-01
That's disconcerting. Not only is it not mounted, but--as far as Ubuntu's concerned--it's not even physically plugged in.

---

### Post by ardchoille on 2005-12-01
[QUOTE=aysiu]That's disconcerting. Not only is it not mounted, but--as far as Ubuntu's concerned--it's not even physically plugged in.[/QUOTE]
ok, well, I am getting off this ride. This is the fifth mp3 player I have tried from the same number of companies and nothing seems to work. I guess I won't be able to have an mp3 player as long as I am using Ubuntu 5.10.. that's sad.

---

### Post by aysiu on 2005-12-01
Really? Because both my Sandisk 256 MB MP3 player and my wife's G3 20 GB iPod work on Breezy. Maybe something's up with your USB port?

---

### Post by cwaldbieser on 2005-12-01
[QUOTE=ardchoille]I tried installing ifp-line but the command was not dound when I tried to run it as both user and root. I tried installing ifp-line-libifp and the same thing happened. There is no way to run these apps after installing them.[/QUOTE]
OK, if it creates a device node at all, this will find it:
1) Unplug device.  Type:
```

$ ls /dev > unplugged.txt

```
2) Plug in device, wait a few seconds.  Type:
```

$ ls /dev > plugged.txt
$ diff unplugged.txt plugged.txt

```
This should show any new devices that have appeared after plugging in.

---

### Post by ardchoille on 2005-12-01
[QUOTE=cwaldbieser]OK, if it creates a device node at all, this will find it:
1) Unplug device.  Type:
```

$ ls /dev > unplugged.txt

```
2) Plug in device, wait a few seconds.  Type:
```

$ ls /dev > plugged.txt
$ diff unplugged.txt plugged.txt

```
This should show any new devices that have appeared after plugging in.[/QUOTE]
Nothing.. there was no diference between the two. I give up. Thanks for trying, though :)

---

