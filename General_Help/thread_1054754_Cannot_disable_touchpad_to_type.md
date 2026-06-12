---
title: "Cannot disable touchpad to type"
date: 2009-01-30
forum: General Help
---

### Post by Nickelrw87 on 2009-01-30
This is my first post in this here forum. I love this site and i love Ubuntu, everyone is so damn smart its just awesome to see everyone help everyone. Anyways, i am trying to get my touchpad to disable while i type, i have searched on this forum many, many times - tryed every damn thing i could find on the internet. I could never find the same EXACT situation.So after screwing around with Ubuntu for a while i did a clean install and now im at the beginning with a clean plate.

Ill post my xorg.conf file fist off i guess and ill post any information you need. Thanks a bunch, i know this can be fixed, its Ubuntu!

Toshiba 305d
AMD64
3 gig ram
ATI Radeon
Ubuntu Intrepid
             xorg.conf 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection


.....and also when i try and run syndaemon....

X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  150 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

---

### Post by darkmire on 2009-01-30
[QUOTE=Nickelrw87;6643293]This is my first post in this here forum. I love this site and i love Ubuntu, everyone is so damn smart its just awesome to see everyone help everyone. Anyways, i am trying to get my touchpad to disable while i type, i have searched on this forum many, many times - tryed every damn thing i could find on the internet. I could never find the same EXACT situation.So after screwing around with Ubuntu for a while i did a clean install and now im at the beginning with a clean plate.


So you're trying to disable your touchpad?  In GNOME you can do this through  System > Preferences > Mouse > Touchpad.

---

### Post by kmac on 2009-01-30
Search for "Touchpad" in the Add/Remove package manager. There should be an app (can't remember which) that can map a key combination to disable

---

### Post by blazemore on 2009-01-30
The touchpad is quite easy to bump whilst typing. The best fix is to disable all scroll and tap commands for 1 second after each keystroke. 

Go to Preferences and select "Sessions". Click the add button and add an entry: 

```

Name: Syndaemon
Command: syndaemon -d -t -i 1
Comment: Disable trackpad while typing
```
The '1' can be changed to any decimal number, and defines the amount of time (in seconds) to lock the trackpad after each keystroke. See the Syndaemon man page for full details.

---

### Post by Nickelrw87 on 2009-01-30
Thank you for this information. I added in the commands for start-up in sessions menu. It was a no go, there was no errors that popped up or anything. Also when i try to run the same command, this is what comes out.

"X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  150 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10"

^^I have ran it sudo and non sudo. both come out with same error.


Thanks for the timely response!

---

### Post by Nickelrw87 on 2009-01-31
bump i guess

---

### Post by Nickelrw87 on 2009-02-01
BUmp - again....come on guys i had like 2-3 posts within a day of me starting this and now no one?

---

### Post by Nickelrw87 on 2009-02-04
thanks guys!!!!!! that worked out ******* GRRRREAT!!!! im glad everyone else who has a ******* post and needs help everyone jumps on until its fixed....

---

