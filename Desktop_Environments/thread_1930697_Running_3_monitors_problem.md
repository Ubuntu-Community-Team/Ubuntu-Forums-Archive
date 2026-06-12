---
title: "Running 3 monitors problem"
date: 2012-02-24
forum: Desktop Environments
---

### Post by me01273 on 2012-02-24
Hi,

I've got 2 graphics cards in my computer (one built in and an nVidia one). I'm currently running 2 monitors from the VGA and DVI-I sockets on the nVidia card. I'm trying to run a 3rd monitor from one of the sockets on the built in card, but I can't get it to work. I've tried plugging in the monitor to both VGA and DVI-D sockets on the motherboard, but Ubunutu just doesn't recognise it.

This is my output from running xrandr:
```
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 8192 x 8192
DVI-I-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+   60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI-D-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+   60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

```As you can see the DVI-D-1 socket is showing as disconnected even though I have a monitor plugged into it (I'm not sure why the VGA from the motherboard doesn't show on this list.

Any ideas on what I can try? I did read up about X server, but I really don't have the experience with Linux to make my own xorg config file.

I'm running Ubuntu 10.04 LTS in a desktop computer.

David

---

### Post by lncoll on 2012-02-24
Most of the motherboars disable the integrated VGA if there is one pluged.
Try accessing you bios and looking in "integrated peripherals" for graphics card options.

---

### Post by me01273 on 2012-02-27
Thanks for your reply. Just checked my BIOS and both graphics cards are enabled. If I plug my monitors only into the motherboard, it loads fine with that config, but if a single monitor is plugged into either one of the ports on the graphics card, it loads only on that monitor.
I believe this to be an Ubuntu config problem as a colleague is running 4 monitors in a similar setup with Windows without problem.

Am I going to have to take the plunge and try and configure X server manually?
Even if I have to, I don't understand why the output of xrandr doesn't show the monitor plugged in.

David

---

