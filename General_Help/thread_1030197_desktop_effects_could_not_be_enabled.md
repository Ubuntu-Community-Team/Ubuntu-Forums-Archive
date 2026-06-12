---
title: "desktop effects could not be enabled"
date: 2009-01-04
forum: General Help
---

### Post by shashank.shekher.02 on 2009-01-04
i am comparatively a new user at ubuntu. i have ubuntu ultimate 1.8. i use a nvidia graphics card 6200 TC. using envy i installed its driver because it was the easy way. now the problem is i m unable to activate the desktop effects. i dont know wut the problem is. i m very confused. my system requirements are more than sufficient. plzzz help me out of this. i will let u know anymore information about this if u ask for it. thanx in advance.

---

### Post by Peter09 on 2009-01-04
First check what driver you have install - post the output of

```
lshw -C display
```
also check you if you have any drivers waiting to be enabled in
System->Admin->Hardware Drivers

---

### Post by Forlong on 2009-01-04
> **shashank.shekher.02 said:**
> i m unable to activate the desktop effects. i dont know wut the problem is. i m very confused. my system requirements are more than sufficient. plzzz help me out of this. i will let u know anymore information about this if u ask for it.

[Compiz-Check -- no more "Desktop effects could not be enabled"]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by shashank.shekher.02 on 2009-01-04
> **Peter09 said:**
> First check what driver you have install - post the output of

```
lshw -C display
```
also check you if you have any drivers waiting to be enabled in
System->Admin->Hardware Drivers

this the output

```
 *-display               
       description: VGA compatible controller
       product: NV44 [GeForce 6200 TurboCache(TM)]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
```

---

### Post by shashank.shekher.02 on 2009-01-04
> **Peter09 said:**
> First check what driver you have install - post the output of

```
lshw -C display
```
also check you if you have any drivers waiting to be enabled in
System->Admin->Hardware Drivers

and yes...thr is a driver waiting to be enabled in system->admin->hardware drivers....but i have intentionally disabled it because when i enable it and reboot my comp then the pixel size is enlarged to 600*480 or something like that....and also even after enabling the driver same error message would be displayed when activating desktop effects. presently i installed the graphics driver using envy...the easy way of course!

---

### Post by shashank.shekher.02 on 2009-01-04
> **Forlong said:**
> [Compiz-Check -- no more "Desktop effects could not be enabled"]("http://ubuntuforums.org/showthread.php?t=799070")

this is the output after i had run compiz-check on my comp

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size
```

well it seems like everything is wrong...is there any way we can mend it??!!

---

### Post by Forlong on 2009-01-04
> **shashank.shekher.02 said:**
> presently i installed the graphics driver using envy...the easy way of course!
How is that easier than going to *System &#8594; Administration &#8594; Hardware Drivers*?

Anyway... the Envy install obviously went wrong.
Try un-installing it and go with the Ubuntu one.


P.S. Is there any particular reason why you installed Ubuntu "ultimate"?

---

### Post by shashank.shekher.02 on 2009-01-04
> **Forlong said:**
> How is that easier than going to *System &#8594; Administration &#8594; Hardware Drivers*?

Anyway... the Envy install obviously went wrong.
Try un-installing it and go with the Ubuntu one.


P.S. Is there any particular reason why you installed Ubuntu "ultimate"?

ok i will uninstall it...but the ubuntu's driver is also unable to enable the desktop effects. anyways i will try it once again and reply to you. thanx anyways. and yes...thr is no particular reason for me to install ubuntu ultimate.

---

### Post by Forlong on 2009-01-04
> **shashank.shekher.02 said:**
> thr is no particular reason for me to install ubuntu ultimate.
Then you might want to switch to a regular Ubuntu install, since it's much easier to get support then.

---

### Post by shashank.shekher.02 on 2009-01-05
> **Forlong said:**
> How is that easier than going to *System &#8594; Administration &#8594; Hardware Drivers*?

Anyway... the Envy install obviously went wrong.
Try un-installing it and go with the Ubuntu one.


P.S. Is there any particular reason why you installed Ubuntu "ultimate"?

i did what u told me to do without any luck....it is showing the same message "desktop effects could not be enabled":(...also i dont have any other ubuntu version here....so i request u to suggest me some other solution to this problem. thanx in advance!!!:)

---

### Post by Forlong on 2009-01-05
Is the output of Compiz-Check the same now?

---

### Post by shashank.shekher.02 on 2009-01-05
> **Forlong said:**
> Is the output of Compiz-Check the same now?

yes sir...its exactly the same!!:(

---

### Post by Forlong on 2009-01-05
I have no experience with Nvidia hardware myself but your driver is obviously not properly installed.

What's the output of ```
dpkg -l | grep 'nvidia\|fglrx'
```
And you might want to post the content of **/var/log/Xorg.0.log**

---

### Post by shashank.shekher.02 on 2009-01-05
> **Forlong said:**
> I have no experience with Nvidia hardware myself but your driver is obviously not properly installed.

What's the output of ```
dpkg -l | grep 'nvidia\|fglrx'
```
And you might want to post the content of **/var/log/Xorg.0.log**

the output of first code is
```
ii  nvidia-glx-new                             169.12+2.6.24.14-22.53                               NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                                    NVIDIA binary kernel module common files

```
"/var/log/Xorg.0.log" this code is showing "permission denied" on execution

---

### Post by shashank.shekher.02 on 2009-01-05
the output of your first code is

ii  nvidia-glx-new                             169.12+2.6.24.14-22.53                               NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                                    NVIDIA binary kernel module common files

---

### Post by Forlong on 2009-01-05
Sorry, I think you'll have to contact the guys over at Ubuntu ultimate to fix this.

---

### Post by shashank.shekher.02 on 2009-01-06
> **Forlong said:**
> Sorry, I think you'll have to contact the guys over at Ubuntu ultimate to fix this.

neways,ur help is highly appreciated...thank you!!!:)

---

