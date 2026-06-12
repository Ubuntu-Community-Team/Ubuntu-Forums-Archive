---
title: "Auto Disabling Synaptic Touch Pad"
date: 2008-03-14
forum: Dell  Ubuntu Support
---

### Post by Xephyrind on 2008-03-14
Hello,

My system is Dell Inspiron E1505 laptop notebook. I was wondering if there is a automatic way for the synaptic touch pad to disable itself when I plug in a usb mouse and re-enable itself automatically when a usb mouse is no longer present/detected. I am a complete noob to shell command and Linux system. A complete step by step guide walk through would be great! Thanks for reading :)

---

### Post by xeth_delta on 2008-03-14
I am not sure about disabling the trackpad when a USB mouse is connected, it might be possible.
It is possible to make the system ignore accidental clicks, should you be interested in this. I remember having read some threads discussing how to do it.

---

### Post by Acunga on 2008-03-20
Answer pls how to disable the dem touchpad forever!

---

### Post by tact on 2008-03-20
> **Acunga said:**
> Answer pls how to disable the dem touchpad forever!

There are a few ways to turn it off.  If you want a GUI then search synaptic package manager for "gsynaptics" and install it.  It will then show up in System>Preferences>Touchpad and you can turn it off with a click.

For poetic justice use the touchpad to deselect the tick box "Enable Touchpad".   hehehe

alternately install from CLI with
```
sudo apt-get install gsynaptics
```

If you don't want to turn it off manually/permanently like that you can have it set up so that it is automatically disabled when you are typing and is automatically re-enabled only after a timedelay (you set) after your last keypress.

I have mine set to delay re-enabling the touchpad until one (or two?) seconds after my last keypress.  It really does stop those annoying accidental touchpad incidents - and then the touchpad is there when you want it...  like for emulating a scrollwheel when you dont have the external mouse connected.

To achieve the above (auto disable/enable) the software is already installed.  You need to add a line to your xorg.conf and create a startup item to run "syndaemon" with parameters you choose.
(further info on request). 

Ciao

---

### Post by Arthur Archnix on 2008-03-20
My preffered methods of:

**1. Permamently disabling touchpad. **

```
sudo apt-get remove xserver-xorg-input-synaptics
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
gksudo gedit /etc/X11/xorg.conf
```Delete or comment out the device section about synaptics. Then, scroll down and remove subsequent references to synaptics. Save and close. Reboot computer to make sure 'X' still works and that synaptics drivers are unloaded. At this point, touchpad probably still works using fallback driver. Confirm that its being controlled now by psmouse
```
sudo modprobe -r psmouse
```If this disables the touchpad, we can now blacklist the driver.
```
gksudo gedit /etc/modprobe.d/blacklist
```add at the bottom
> # disables fallback touchpad driver
blacklist psmouseReboot and touchpad is off for good. You must undo all this damage to turn it back on.

--alternative method--

Since I uninstall the synaptics driver, I am not sure what it's called. You would need to determine this in order to blacklist it. Then simply add that driver to a second line in the blacklist file. Also, I'm not sure that it's necessary to remove or comment out the info on synaptics. I think all that happens is that xorg mildly and quietly complains in the logs about the fact that there's supposed to be this touchpad thing, but it's not there.


**2. Compromise, disabling when mouse present, enabling when no mouse present.**

I'm just gonna link to another post on the subject, since I don't want to retype it...
[http://ubuntuforums.org/showpost.php?p=4423915&postcount=9](http://ubuntuforums.org/showpost.php?p=4423915&postcount=9)

The only thing I'd add to that, is that you should still create keyboard shortcuts to disable your touchpad manually, since the udev rules sometimes don't work upon boot, or after resuming from standby.

From the same thread: [http://ubuntuforums.org/showpost.php?p=4177125&postcount=7](http://ubuntuforums.org/showpost.php?p=4177125&postcount=7)

Even if you don't want to create the shortcut, you still need to follow the instructions about editing xorg.conf to add the option SHMConfig on, otherwise the udev rules won't work.

---

