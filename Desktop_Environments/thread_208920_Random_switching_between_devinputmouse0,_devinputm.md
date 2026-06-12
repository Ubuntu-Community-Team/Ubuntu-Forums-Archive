---
title: "Random switching between /dev/input/mouse0, /dev/input/mouse1, and /dev/input/mouse2?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by HippoMan on 2006-07-04
I'm running Dapper/kubuntu on a Dell Inspiron 9300 with the **2.6.15-25-686 #1 SMP PREEMPT** kernel.  I have my touchpad totally disabled (see this thread for details: [http://ubuntuforums.org/showpost.php?p=773117&postcount=1)]("http://ubuntuforums.org/showpost.php?p=773117&postcount=1%29"), and I'm using an external USB mouse.

As you can see from the pertinent section of my **xorg.conf** (shown below), I have the reference to **/dev/input/mice** commented out, and instead, I enable **/dev/input/mouse0**.  This ensures that the touchpad is totally dead, and that my external USB mouse is recognized, instead.

Ever since I started running Dapper, I've  noticed that when I reboot, the USB mouse sometimes comes up on **/dev/input/mouse0**, sometimes on  **/dev/input/mouse1**, and sometimes on **/dev/input/mouse2**.  The choice among these three seems to occur randomly.

This takes place whether I do a soft reboot (*i.e.*, without shutting the machine down) or a hard restart after a complete shutdown.  I should also point out that I do not replug the mouse cable ... it remains in the same USB slot between restarts.

After rebooting, I therefore often have to go into a console and change the Option line in **xorg.conf** to reference the currently active mouse ID, and then go back to tty7 and issue a **Ctrl-Alt-Backspace** to restart my X server with the updated settings.

Does anyone know how to prevent this random switching between **mouse0**, **mouse1**, and ** mouse2** without my having to turn on **/dev/input/mice**?

Thanks in advance.

Here's the section  from **xorg.conf**:
```
Section "InputDevice"                                                                               
        Identifier      "Configured Mouse"                                                          
        Driver          "mouse"                                                                     
        Option          "CorePointer" 
        ##Disable touchpad completely:                                                     
        ##Option                "Device"                "/dev/input/mice"                           
        Option          "Device"                "/dev/input/mouse0"                                 
        Option          "Protocol"              "ExplorerPS/2"                                      
        Option          "ZAxisMapping"          "4 5"                                               
        Option          "Emulate3Buttons"       "true"                                              
EndSection                                                                                          


```

---

### Post by HippoMan on 2006-08-26
I'm bumping this thread, just in case someone who knows something about this might have missed my original post on July 4, 2006.

Thanks.

---

### Post by StevenYap on 2006-08-26
You have a couple of options here. Firstly, you can create a udev rule that makes a symbolic link that points to the correct /dev/input/mouseX device regardless of what X turns out to be. See [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html).

The other option you could try is be to use the evdev driver instead of the mouse driver. See [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse). Although it's ostensibly for the Logitech MX1000, the evdev driver should work with any USB mice. 

Specifically, changingr you InputDevice section to something like
```

Section "InputDevice"                                                                               
        Identifier      "Configured Mouse"                                                          
        Driver          "evdev"                                                                     
        Option          "Name"  "XXXX"                                 
EndSection

```
where XXXX is the Name value reported by "cat /proc/bus/input/devices" for your mouse.

Hope that helps.

---

### Post by HippoMan on 2006-08-26
Yes, that indeed helps.

I used the "evdev" method, and it works, but it also enabled my touchpad, which I don't want.  I'm now going to try the udev method.

---

### Post by HippoMan on 2006-08-26
In trying the udev method, I now realize that I don't think that it can help me (or else I'm somehow misunderstanding things).  The problem is that there is no fixed name to use for the mouse symlink.  Sometimes, the **mouse0** device is my USB mouse, sometimes it's the **mouse1** device, and sometimes it's **mouse2**.  And one of the other two (also randomly selected) gets assigned to the touchpad.  These assignments change every time I reboot my system

I don't know how to force the USB mouse to always be set to a specific one of these, since the system seems to assign the **mouse0**/**mouse1**/**mouse2** names randomly to my USB mouse and touchpad.

---

### Post by StevenYap on 2006-08-27
The trick here to give a consistent name to your mouse regardless of what names the kernel assigned to it. You know that the kernel will generate device names of the form /dev/input/eventX and /dev/input/mouseX.

You can see the default udev rules for these in /etc/udev/rules.d/20-names.rules. You can write a udev rule that is more specific like so:
```
KERNEL=="event[0-9]*", SYSFS{name}=="Logitech USB Receiver", SYMLINK+="input/mx1000"
```

Just change the SYSFS part of the rule to something that will uniquely identify your mouse, and the SYMLINK part to the persistent name that you want your mouse to be. You can use 
```
udevinfo -a -p /sys/class/input/inputX/
```
where X is the kernel number assigned your mouse to get a list of SYSFS attributes for your mouse.

---

