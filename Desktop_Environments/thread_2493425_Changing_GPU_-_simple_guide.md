---
title: "Changing GPU - simple guide?"
date: 2023-12-14
forum: Desktop Environments
---

### Post by bingodingo on 2023-12-14
Is there a simple guide re how to [install drivers in advance?] if changing a GPU?
I recently tried swapping from an AMD to an Nvidia GPU. Getting the system to boot properly afterwards did not look easy; for the moment, just gave up on using Ubuntu on that system.
If I want to revisit the issue in the future - is there a simple guide? Is the problem essentially installing the graphics drivers?
Thanks

---

### Post by ActionParsnip on 2023-12-15
I'd always uninstall the proprietary video driver you installed then reboot so that the open source driver is used. Then swap the hardware

---

### Post by Tadaen_Sylvermane on 2023-12-15
I know in my case with an LTSP pxe system I have running Ubuntu I keep the nvidia driver installed in the chroot along with the mesa amd drivers. It seems to pick whichever one depending on what machine boots the image. So while it may be ideal to remove the other driver in my case it seems to not have any real effect. Granted I don't use these pxe boot machines very often these days.

---

### Post by bingodingo on 2023-12-15
> **ActionParsnip said:**
> I'd always uninstall the proprietary video driver you installed then reboot so that the open source driver is used. Then swap the hardware

How do I manually install the open source driver?
How do I list what proprietary driver I have installed?
I usually have above 4g decoding / resizable bar enabled in bios - do I need to disable them in bios before booting in when using the open source driver?
BTW: ubuntu 22.04
Thanks.

---

### Post by #&amp;thj^% on 2023-12-15
> **bingodingo said:**
> How do I manually install the open source driver?
How do I list what proprietary driver I have installed?
I usually have above 4g decoding / resizable bar enabled in bios - do I need to disable them in bios before booting in when using the open source driver?
BTW: ubuntu 22.04
Thanks.

To see what's installed currently:
```
apt list nvidia* |grep installed

```
The opensource driver is in the kernel, nothing needs to be done.
Note; You need to remove the nVidia driver first, before trying again.
then check with:
```
ubuntu-drivers list
```
or for an automated install use:
```
ubuntu-drivers install
```

---

### Post by bingodingo on 2023-12-15
> **1fallen said:**
> To see what's installed currently:
```
apt list nvidia* |grep installed

```

output:
```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
E: input:0-11: error: Expected pattern
   nvidia_list
   ^^^^^^^^^^^

```
>  The opensource driver is in the kernel, nothing needs to be done.
Note; You need to remove the nVidia driver first, before trying again.

Software and updates, additional drivers reports: no proprietary drivers in use
> 
then check with:
```
ubuntu-drivers list
```

no output for above.
> 
or for an automated install use:
```
ubuntu-drivers install
```
output from the above:
All the available drivers are already installed.

---

### Post by bingodingo on 2023-12-15
Clarification re the above:
I now have the Ubuntu drive in an AMD machine with the original GPU (rx 6800 xt), I don´t currently have an Ubuntu drive in the original machine that now contains an nvidia GPU.

---

### Post by #&amp;thj^% on 2023-12-15
> **bingodingo said:**
> Clarification re the above:
I now have the Ubuntu drive in an AMD machine with the original GPU (rx 6800 xt), I don´t currently have an Ubuntu drive in the original machine that now contains an nvidia GPU.

When your ready to try again use the suggested method to install the nVidia driver
```
ubuntu-drivers install
```

A reboot will be needed to activate the driver.

---

### Post by bingodingo on 2023-12-15
> **1fallen said:**
> When your ready to try again use the suggested method to install the nVidia driver
```
ubuntu-drivers install
```

A reboot will be needed to activate the driver.
Problem: previously, when I put the drive in the machine that now contains the nvidia GPU I couldn´t boot into Ubuntu. Is that expected? (I end up with a blinking cursor black screen after the os / bios splash screen.)
(One option: I can connect the monitor to an internal GPU and perhaps boot in to Ubuntu and do the above.)

---

### Post by #&amp;thj^% on 2023-12-15
> **bingodingo said:**
> I can connect the monitor to an internal GPU and perhaps boot in to Ubuntu and do the above.)

See your getting the hang of it. Yep that's a a good plan.
After the driver has a successful install connect to the nVidia card>>>(While the machine is powered off of course) 
Boot back up to your beautiful new graphics delight. :)

---

