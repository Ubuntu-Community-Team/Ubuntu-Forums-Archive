---
title: "widescreen resolution"
date: 2013-01-21
forum: Desktop Environments
---

### Post by Erica Prates on 2013-01-21
Hello

I have installed the xubuntu 12.04 and I cannot adjust the right screen resolution to my monitor. The maximum resolution I have found in the " Display settings" or by running  xrandr is 1280x1024. I need  1920 x 1080. Could someone help me to solve this problem?

I really appreciate any help you can provide.

Erica

---

### Post by papibe on 2013-01-21
Hi Erica Prates. Welcome to the forums ):P

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste the file here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back the link to it.

Regards.

---

### Post by Erica Prates on 2013-01-21
> **papibe said:**
> Hi Erica Prates. Welcome to the forums ):P

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste the file here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back the link to it.

Regards.
Hello, papibe!
Here it is: 
[http://paste.ubuntu.com/1556460/](http://paste.ubuntu.com/1556460/)
Thanks!

---

### Post by papibe on 2013-01-21
Thanks.

I can't get what kind of video card you have, only that it may be Nvidia, but Xorg is defaulting to a Vesa driver. Do you know? 

Also, could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

sudo lshw -C display
```
Regards.

---

### Post by dannyboy79 on 2013-01-21
it appears like nouveau is loading as well?

LoadModule: "nouveau"
[131336.457] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[131336.457] (II) Module nouveau: vendor="X.Org Foundation"

---

### Post by Erica Prates on 2013-01-21
> **papibe said:**
> Thanks.

I can't get what kind of video card you have, only that it may be Nvidia, but Xorg is defaulting to a Vesa driver. Do you know? 

Also, could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

sudo lshw -C display
```
Regards.
I know the video card  I am using here is GeForce GTX 660 Ti.

It follows the results for those commands: 
 
$ lspci -nnk |grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1183] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:1280]
    Kernel modules: nouveau, nvidiafb

$ sudo lshw -C display
   *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff

---

### Post by papibe on 2013-01-21
> **Erica Prates said:**
> I know the video card  I am using here is GeForce GTX 660 Ti.

Ok.

Try installing the Nvidia proprietary driver. It should support better the resolutions.

Take a look at this [tutorial]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") if you have any doubt how to do it.

Choose the nvidia-current (recommended). When successfully installed, you'll need to restart to machine in order to take effect. However, before you restart your machine run this command (to create a proper config file):
```
sudo nvidia-xconfig
```
Let us know how it goes.
Regards

---

### Post by Erica Prates on 2013-01-21
It worked perfectly! 
I have installed Nvidia-current using the Synaptic Package Manager. 
Now I have got the perfect resolution. 
Thank you a lot.
Best regards

---

### Post by papibe on 2013-01-21
:) Great! Glad you got it working.

Please mark thread as SOLVED, when you have the time ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to).

Regards.

---

