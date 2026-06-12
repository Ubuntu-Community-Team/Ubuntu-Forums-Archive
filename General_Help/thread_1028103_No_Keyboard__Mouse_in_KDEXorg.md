---
title: "No Keyboard / Mouse in KDE/Xorg"
date: 2009-01-02
forum: General Help
---

### Post by tpf80 on 2009-01-02
Hello and thanks in advance for your help.

Pretty much I had a computer built in 2004, which the motherboard capacitors blew, so I got new parts and put my old hard drive in the new computer.

At first everything worked great except that the computer would not shut down, it just went to a blank screen, and attempting to go to tty1-whatever just gave me a blank screen. 

I fixed that by removing the closed source nvidia drivers and now my computer reboots / shuts down fine, however now the mouse and keyboard will not work in X! I also noticed that my xorg.conf has been replaced with an almost empty file. I get to the login screen and there is no mouse movement at all, and no keyboard activity. I can however press [CTRL][ALT][F1] and get to a command prompt and log in.

Now, I have done everything I can think of, reinstalling drivers, modifying my xorg.conf, etc that is suggested in these forums, but nothing I can find will make my mouse and keyboard work in X.

I can see that the devices are detected, and of course they work in the command window. 

I also notice that we are now using something called evdev, which seems to be the heart of the problem. It looks like the old way of using xorg.conf has gone away, and now evdev has taken over.


My Xorg.0.log shows the following error message about this issue for pretty much every USB device in my system:

> 
(II) config/hal: Adding input device <whatever device it is>
(EE) No input driver/identifier specified (ignoring)
(EE) config/hal: NewInputDeviceRequest failed


So theres the problem, and it tells me what to do. Where do I specify the input driver? I have looked up this error on google, in these forums, etc. and I couldn't find much relating to my problem.

Also I'm on intrepid 8.10 AMD64

---

### Post by tpf80 on 2009-01-02
I have tried to add the following to my Xorg.conf with no results:

> 
Section "InputDevice"
        Identifier  "Mouse[0]"
        Driver      "evdev"
        Option      "Device" "/dev/input/event0" 
        Option      "Name" "Logitech Mouse"
EndSection


I have confirmed that my mouse is event 0, however doing this and restarting yields no results. KDE starts but with no mouse and the same errors.

---

### Post by tpf80 on 2009-01-02
well I finally got my mouse working, just skipping evdev, and modifying xorg.conf. however now my graphics driver is having problems. 

If I attempt to install the nvidia drivers, it erases my xorg.conf causing my mouse and keyboard to not work, and the kernel module fails to compile.

I almost would rather my computer not shutting down properly like it was this morning than my graphics to be messed up..

---

### Post by tpf80 on 2009-01-02
well I figured it out, somehow my system had the latest kernel headers, but was using an older kernel. After changing my grub configuration and rebooting. I was able to use the instructions on Nvidia's web site to purge all the old drivers, and then reinstall with no problems *sigh of relief* and it even shuts down properly now.

---

