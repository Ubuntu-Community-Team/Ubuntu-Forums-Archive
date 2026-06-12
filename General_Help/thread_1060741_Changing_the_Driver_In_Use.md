---
title: "Changing the Driver In Use"
date: 2009-02-05
forum: General Help
---

### Post by mpl34 on 2009-02-05
Hey, i have been trying to install compiz however the driver i am currently using has no support for it. i have installed the nvidia driver but i believe i may need to change the xorg.f or something to make sure the nvidia driver loads instead of the nv which i am getting. 

```
michael@michael-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   KDE4
 Graphics chip:         nVidia Corporation GeForce 8600M GT (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) n

```

---

### Post by mpl34 on 2009-02-05
Alittle bit of research lead me to this command however didn't seem to help. I thought it may be useful to post the output

```
michael@michael-laptop:~$ sudo nvidia-xconfig --add-argb-glx-visuals -d 24
[sudo] password for michael:

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver line.

Option "AddARGBGLXVisuals" "True" added to Screen "Screen0".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

Also when i open Nvidia X server Settings i get the following error/message: > "You do no appear to be using the NVIDIA X driver please edit you X configuration file (just run `nvidia xconfig` as root), and restart the X sever"Lol in typing this out i may have found my solution i'm gona give `nvidia-xconfig` a shot.

EDIT: unfortunately it didn't work got the following error
```
michael@michael-laptop:~$ nvidia-xconfig
Using X configuration file: "/etc/X11/xorg.conf".
ERROR: Unable to write to directory '/etc/X11'.
```

---

### Post by kbutcher5 on 2009-02-05
You can't do any administrative work, like configuring drivers without being root, try using "sudo" in front of you commands.
Do this:
```

sudo cat /etc/X11/xorg.conf

```
Then post the output here.

---

### Post by mpl34 on 2009-02-05
your suggestion was correct however it did not seem to solve the problem 
```
michael@michael-laptop:~$ sudo nvidia-xconfig
[sudo] password for michael:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

michael@michael-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   KDE4
 Graphics chip:         nVidia Corporation GeForce 8600M GT (rev a1)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Would you like to know more? (Y/n) ^C

```

---

### Post by mpl34 on 2009-02-05
Ok from the following code i decided to see what my /etc/X11/xorg.conf looked like.

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by kbutcher5 on 2009-02-05
This should point you on to recognizing your driver, if all else fails, just drop by here again.
[http://ubuntuforums.org/showthread.php?t=1058731&highlight=install+nvidia+driver](http://ubuntuforums.org/showthread.php?t=1058731&highlight=install+nvidia+driver)

---

### Post by regala on 2009-02-05
> **kbutcher5 said:**
> You can't do any administrative work, like configuring drivers without being root, try using "sudo" in front of you commands.
Do this:
```

sudo cat /etc/X11/xorg.conf

```
Then post the output here.

no, what he has to do is
```

sudo nvidia-xconfig

```
we know its problem, the error output message is crystal clear.
and putting sudo before cating the xorg.conf is useless since everyone can read this file.

br

---

### Post by mpl34 on 2009-02-05
ok i have tried the sudo nvidia-xconfig and it has changed the xorg.conf however when i reboot the nvidia logo appears the i get a black that flashes with weird lines on it it then crashes and continually repeats this process, I also tried to activate the driver thru the hardware menu then once i restart i get the same error. i can fix this hoever by booting in recovery mode and by choosing the option fix x server (or something similar), this however stops the nvidia driver from loading

---

### Post by mpl34 on 2009-02-06
I have ended up doing a complete re-install of kubuntu which proved to be quite difficult. For some reason after the un-installation grub played up and vista wouldn't boot. I then ran a disk repair with my vista install disc which fixed the problem and allowed me to boot within vista, however it saved necessary system data near the end of my map drive and therefore the simple kubuntu partition software on installation could not complete the partition of 40GB. I ended up running 3 defrag then a boot defrag then one more defrag using perfectdisk to free a 40GB sector on my disk.

Now kubuntu is running perfectly I've installed the nvidia driver with no problems and when running compiz-check everything turns back ok so feels great however did take 5hrs of defrags (which may have been an ineffective method on my choice).

---

