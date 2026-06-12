---
title: "autorun script when inserting my usb drive"
date: 2009-07-02
forum: Desktop Environments
---

### Post by kurci2 on 2009-07-02
Hello!
I have a little problem.
I found these dwo sites:
[http://ubuntuforums.org/showpost.php?p=](http://ubuntuforums.org/showpost.php?p=) … stcount=16
[http://ubuntuforums.org/showthread.php?t=268291](http://ubuntuforums.org/showthread.php?t=268291)
they helped my with my problem.
i want to insert my usb in my computer and a script runs automatically, because i want to unlock my screen with usb.

i created file:
/etc/udev/rules.d/10-usbkeysync.rules, and i wrote that in it:

```
ACTION=="add", BUS=="usb", SYSFS{manufacturer}=="SanDisk Corporation", SYSFS{product}=="U3 Titanium", SYSFS{serial}=="SanDisk_U3_Titanium_0877701437811AA2-0:0", RUN+="/home/marko/unlock.sh"
```

my unlock.sh script is this:

```
#!/bin/bash
gnome-screensaver-command -d
```

but the probem is that, unlock.sh is not executed.

thanks for help!

---

### Post by Boondoklife on 2009-07-02
Check out pamusb-tools, it will do just what you want and MORE.

It does things when the drive is removed and plugged.

---

### Post by kurci2 on 2009-07-03
ok
i've installed pamusb-tools and libpam-usb
and it work as it should
thank you very very much for that!

---

### Post by Boondoklife on 2009-07-03
Try this [http://ubuntuforums.org/showthread.php?t=1159146&highlight=pamusb](http://ubuntuforums.org/showthread.php?t=1159146&highlight=pamusb)

---

### Post by Boondoklife on 2009-07-03
Also if you add the section to the pam setup then the usb stick will let you login to GDM without a password. If you do not want to do that then simply dont put it in there.

---

### Post by kurci2 on 2009-07-03
```
<service id="gdm">
        <option name="enable">true</option>
</service>
```

is this write section to put in and i will log in with my usb?

---

### Post by Boondoklife on 2009-07-03
Here [this]("http://pamusb.org/doc/quickstart") is a better walkthrough, It should take you step by step, also the part that lets you in is the pam module.

---

