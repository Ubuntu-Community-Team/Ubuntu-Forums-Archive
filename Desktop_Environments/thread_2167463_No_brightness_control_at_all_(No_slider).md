---
title: "No brightness control at all? (No slider)"
date: 2013-08-13
forum: Desktop Environments
---

### Post by gabe2 on 2013-08-13
After finally getting my correct resolution, I'm now trying the simple matter of changing the brightness level. The problem, as mentioned in the subject line, there is no brightness control. I looked up and down in the forums and Googled it and there seems to be multiple solutions, none of which really appeal to me, which is that I want my brightness and lock settings to show up and work.

(Simple resolution fix for those who may want to know: log into Guest Session, hopefully resolution is correct there or you can choose it, if so, save xorg.conf and copy contents and paste into YOUR session's xorg.conf file.)

Thanks!

---

### Post by Toz on 2013-08-13
Can you provide some more information? Specifically (enter the commands below in a terminal window):
[LIST=1]
[*]The make and model of your computer.
[*]Your video card(s):
```
lspci -k | grep -A3 VGA
```
[*] Your current kernel command line:
```
cat /proc/cmdline
```
[*]Your backlight interfaces and some of their settings:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
[*]
[/LIST]

---

### Post by gabe2 on 2013-08-13
1. It's custom built. Bought the parts on Newegg and put it together myself. I'm happy to tell you what you need to know regarding the set-up.

2. 2 EVGA GeForce 460 GTX in SLI configuration, but not enabled. - [http://paste.ubuntu.com/5982990/](http://paste.ubuntu.com/5982990/)

3. [http://paste.ubuntu.com/5982994/](http://paste.ubuntu.com/5982994/)

4. [http://paste.ubuntu.com/5983001/](http://paste.ubuntu.com/5983001/)

Interesting...apparently I have no backlight according to #4?

---

### Post by Toz on 2013-08-13
> **gabe2 said:**
> 
Interesting...apparently I have no backlight according to #4?
Indeed. This would be the reason that you have no brightness slider. Can you try a couple of kernel parameters? See the "Kernel Boot Parameters" link in my signature for information on how. I would suggest trying:

[LIST=1]
[*]**acpi_osi=\"!Windows 2012\"**
The relevant lines in /etc/default/grub should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
...make sure to run "sudo update-grub" and reboot.



[*]**acpi_backlight=vendor**
The relevant lines in /etc/default/grub should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
[*]
[/LIST]
With each attempt, post back the results of:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
If you get a backlight interface, check your brightness slider.

---

### Post by gabe2 on 2013-08-13
Thanks, I'll have to try that tomorrow when I'm not so tired and heading for bed. Will update.

---

### Post by gabe2 on 2013-08-14
No luck, the brightness slider remains missing...

Here are the results of those commands: [http://paste.ubuntu.com/5986671/](http://paste.ubuntu.com/5986671/)

What could cause it to go missing? Thanks for your help so far.

---

### Post by Toz on 2013-08-14
That really is odd. Can you pastebin back your **/var/log/Xorg.0.log** and **/var/log/dmesg** log files? 

Anything in the bios about brightness?

Can I also which modules are loaded:
```
lsmod
```

...and
```
xrandr -q
```

---

### Post by gabe2 on 2013-08-14
I can't say I saw anything for brightness in the BIOS, I'll have to look, but I doubt it.
*EDIT* Confirmed, I couldn't find anything in BIOS with regards to brightness.

Xorg.0.log file: [http://paste.ubuntu.com/5987302/](http://paste.ubuntu.com/5987302/)

dmesg file: [http://paste.ubuntu.com/5987306/](http://paste.ubuntu.com/5987306/)

lsmod: [http://paste.ubuntu.com/5987309/](http://paste.ubuntu.com/5987309/)

xrandr -q: [http://paste.ubuntu.com/5987310/](http://paste.ubuntu.com/5987310/)

---

### Post by Toz on 2013-08-15
> 
xrandr -q: [http://paste.ubuntu.com/5987310/](http://paste.ubuntu.com/5987310/)
Do the following commands change brightness:
```
xrandr --output  DVI-I-2 --brightness 0.5
xrandr --output  DVI-I-2 --brightness 0.8
xrandr --output  DVI-I-2 --brightness 1.0
```

> Xorg.0.log file: [http://paste.ubuntu.com/5987302/](http://paste.ubuntu.com/5987302/)
Can you post back /etc/X11/xorg.conf?

> dmesg file: [http://paste.ubuntu.com/5987306/](http://paste.ubuntu.com/5987306/)
And can you remove the "acpi_backlight=vendor" kernel parameter and try the "acpi_osi=" kernel parameter instead? After boot, check to see if you have any backligt interfaces and post back /var/log/dmesg again.

> lsmod: [http://paste.ubuntu.com/5987309/](http://paste.ubuntu.com/5987309/)
Now this is interesting. The i915 driver is loaded. Do you have an onbaord intel graphics chip? If so, can you disable it in the bios?

---

### Post by gabe2 on 2013-08-15
> **Toz said:**
> Do the following commands change brightness:
```
xrandr --output  DVI-I-2 --brightness 0.5
xrandr --output  DVI-I-2 --brightness 0.8
xrandr --output  DVI-I-2 --brightness 1.0
```

Yes, they do. I have it currently set at 0.8, that's about right for me.


> Can you post back /etc/X11/xorg.conf?

Here: [http://paste.ubuntu.com/5990583/](http://paste.ubuntu.com/5990583/)


> And can you remove the "acpi_backlight=vendor" kernel parameter and try the "acpi_osi=" kernel parameter instead? After boot, check to see if you have any backligt interfaces and post back /var/log/dmesg again.

Nope, no backlight interface :-(
dmesg file: [http://paste.ubuntu.com/5990661/](http://paste.ubuntu.com/5990661/)

> Now this is interesting. The i915 driver is loaded. Do you have an onbaord intel graphics chip? If so, can you disable it in the bios?

Yes, I have onboard VGA, and it is disabled.

Would I have to set the brightness in the terminal every time I boot? Is there a way to make the change permanent? Of course, I would much rather have the interface show up and work correctly as designed, but as a last resort, I can do the terminal fix if there's a persistent way to do it.

---

### Post by Toz on 2013-08-15
> **gabe2 said:**
> I would much rather have the interface show up and work correctly as designed, 
Okay then. Lets try a few more things.
First, remove any kernel boot parameters and reboot (lets get back to a clean system), then:
```
sudo modprobe -r i915
```
...if there are no errors while you do this, check to see if the i915 module was unloaded:
```
lsmod | grep i915
```
If that returns nothing and there were no errors during removal, check for a backlight interface and brightness slider (you may need to log out and back in again (not reboot yet).

If there were errors, post them back.

If no errors removing the module and still no backlight interface/brightness slider, try adding i915 to the module blacklist by editing as root /etc/modprobe.d/blacklist and adding:
```
blacklist i915
```
...and this time rebooting.

Lets try this first and see what happens. In the meantime, I'll review the log files you posted.

---

### Post by gabe2 on 2013-08-17
> **Toz said:**
> Okay then. Lets try a few more things.
First, remove any kernel boot parameters and reboot (lets get back to a clean system), then:
```
sudo modprobe -r i915
```
...if there are no errors while you do this, check to see if the i915 module was unloaded:
```
lsmod | grep i915
```
If that returns nothing and there were no errors during removal, check for a backlight interface and brightness slider (you may need to log out and back in again (not reboot yet).

If there were errors, post them back.

If no errors removing the module and still no backlight interface/brightness slider, try adding i915 to the module blacklist by editing as root /etc/modprobe.d/blacklist and adding:
```
blacklist i915
```
...and this time rebooting.

Lets try this first and see what happens. In the meantime, I'll review the log files you posted.

Wow...tried all of those and nothing. In fact, when I tried the terminal commands after removing the kernal parameter (and rebooting) nothing at all happened. There was no error OR confirmation of anything, it just went straight to the next $ command line.

I also just realized that while I would like to have the brightness control available, it may not matter much because I have a Pantone Huey monitor calibrator and I used the ICC profile created in Windows and just assigned it to Ubuntu. It worked very nicely and I believe it compensates for the lighting too. It's too bad there isn't a Pantone Huey app for Ubuntu. I'd code it if I had any knowledge at all about coding (which, obviously, I do not).

So, may not be a big deal after all, but I suspect you're as confused by this problem as I am that Ubuntu on my system is being a stubborn ass about giving up brightness controls.

---

### Post by Toz on 2013-08-17
> **gabe2 said:**
> Wow...tried all of those and nothing. In fact, when I tried the terminal commands after removing the kernal parameter (and rebooting) nothing at all happened. There was no error OR confirmation of anything, it just went straight to the next $ command line.
Just to confirm:
```
sudo modprobe -r i915
```
...then post back:
```
lsmod
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

One other thing to try (long shot). In /etc/X11/xorg.conf, can you add, to the "Devices" section, this line in red:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 460"
    BusID          "PCI:1:0:0"
[COLOR="#FF0000"]    Option "RegistryDwords" "EnableBrightnessControl=1"[/COLOR]
EndSection
```
...and log out and back in again.

> I also just realized that while I would like to have the brightness control available, it may not matter much because I have a Pantone Huey monitor calibrator and I used the ICC profile created in Windows and just assigned it to Ubuntu. It worked very nicely and I believe it compensates for the lighting too. It's too bad there isn't a Pantone Huey app for Ubuntu. I'd code it if I had any knowledge at all about coding (which, obviously, I do not).
Worst case, you can still xbacklight to control the backlight.

> So, may not be a big deal after all, but I suspect you're as confused by this problem as I am that Ubuntu on my system is being a stubborn ass about giving up brightness controls.
Yes I am confused. I don't think I've ever seen a system that didn't have at least one backlight interface. Ususally its the other way around - too many interfaces getting in the way.

---

### Post by gabe2 on 2013-08-18
Did the first two commands here: [http://paste.ubuntu.com/5999408/](http://paste.ubuntu.com/5999408/)

As you can see, the first command just went straight to the next command line with nothing (besides asking for my password).

Backlight command: [http://paste.ubuntu.com/5999416/](http://paste.ubuntu.com/5999416/)

Doing the last entry now...nope. No brightness control. Wish I knew coding and programming so I could solve this issue and issue a fix and include that for future versions.

---

### Post by Toz on 2013-08-18
You just can't seem to get a user-facing backlight interface. Have a read of [https://wiki.ubuntu.com/Kernel/Debugging/Backlight]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight"). There is further debugging information including info on how to look directly into the acpi bios. You might also consider creating a bug report to bring this to the attention of the devs.

In the meantime, as a workaround, you can use xbacklight/xrandr.

---

