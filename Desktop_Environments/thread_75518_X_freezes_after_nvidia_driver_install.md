---
title: "X freezes after nvidia driver install"
date: 2005-10-13
forum: Desktop Environments
---

### Post by melgrim on 2005-10-13
Hi,

I installed breezy and X has working fine. I then installed the nvidia drivers:
```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable
ctrl+alt+backspace
```and everything worked as supposed to, but now when I start X, it works well for a while and then it freezes. The mouse cursor still moves in the screen but no action occurs. I can’t use ctrl+alt+F2 to change to text mode so the only way out is doing a reset to the machine.

Is anyone with the same problem?
Any suggestion to solve it?

---

### Post by fimbulvetr on 2005-10-13
What does "grep EE /var/log/Xorg.0.log' give you?

---

### Post by melgrim on 2005-10-13
There's no error in "/var/log/Xorg.0.log"
The grep doesn't give anything useful.
However I can only see the log before the problem occurs since after it, I've no control of the machine (if you rule out moving the mouse around, because that I can do!)
:|

---

### Post by vrecan on 2005-10-13
This has been a pretty consistent problem with nvidia drivers.. but I usually only see this when composite is enabled.

---

### Post by melgrim on 2005-10-14
Since for the time being no solution seems to appear, how can I go back to using the default driver from installation?
Is it enough to change the name of the driver in xorg.conf to "nv" or does it require anything else?

---

### Post by N8MAN1068 on 2005-10-14
hey! at least you got yours to boot! when i did 'sudo nvidia-glx-config enable', X wouldn't start.

I was able to go in through command line and 'sudo nano /etc/X11/xorg.conf' and change it back to 'nv', and it's working ok.

I think later, I'll uninstall the packaged drivers, and download+compile them from nvidia.

---

### Post by Karasu Tengu on 2005-10-14
[QUOTE=melgrim]Since for the time being no solution seems to appear, how can I go back to using the default driver from installation?
Is it enough to change the name of the driver in xorg.conf to "nv" or does it require anything else?[/QUOTE]

Yes it is,
simply rename the driver to nv and it'll be back

---

### Post by yusufk on 2005-10-14
I just upgraded to breezy using synaptic from hoary. Everything works fine, even my nvidia 5500 on dual monitor! Very impressed with the splashy ( is it still called that? ) effect on boot. 

However, I must admit that it seems a little sluggish, not sure whats the cause or how to look for the cause? I'm not keen on reformatting and installing a fresh, at least until the ship-it cd's arrive that is.

---

### Post by melgrim on 2005-10-17
Well, back to 'nv' driver. I sure would like to know why doesn't it work, but for now at least I have a working X.

---

### Post by ugorox on 2006-11-02
if you add "NvAGP" "0" to your device section it will runs normally. it worked for me. 

Section "Device"
        Identifier     "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Driver          "nvidia"
        Option          "NvAGP" "0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

dont ask why

---

