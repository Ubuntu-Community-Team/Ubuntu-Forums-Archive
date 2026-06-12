---
title: "Compiz cube in CCSM?"
date: 2017-10-15
forum: Desktop Environments
---

### Post by andysharpie on 2017-10-15
Does anyone know how to do the cube in CompizConfing Settings Manager? I don't have the cube plugin, but was wondering if I could get it without going to another version of Compiz.

---

### Post by deadflowr on 2017-10-15
You need the compiz-plugins package
```
sudo apt install compiz-plugins
```
it'll get added to the plugins menu, along with the other plugins like 3d windows and rotate cube.

---

### Post by andysharpie on 2017-10-16
I put in the code and it did begin to install the plugins. However, I ran into trouble in the instillation process and got the following (much abbreviated) messages from my terminal.

Errors were encountered while processing:
 linux-firmware
 linux-image-4.10.0-37-generic
 linux-image-extra-4.10.0-37-generic
 linux-image-generic-hwe-16.04
 linux-generic-hwe-16.04
 linux-signed-image-4.10.0-37-generic
 linux-signed-image-generic-hwe-16.04
 linux-signed-generic-hwe-16.04
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have been getting a message every time I boot the system up about 'low disk space', and aside from that I have encountered some instillation errors like this in the past while trying to run updates. I managed to solve a problem of this kind with a sudo ap-get install command, but it seems I've only partially solved the problem. Do you have any ideas?

---

### Post by deadflowr on 2017-10-16
What's
```
df -h
```
show?
(for starters)

---

### Post by andysharpie on 2017-10-16
I ran the command and got a display of used spaces. The only thing that stood out to me was that the /boot file was 100% full. All this still pretty new to me. :) What should I specifically look for?

---

### Post by deadflowr on 2017-10-17
Boot full means you have a few extra obsolete kernels.
You might run
```
uname -a
dpkg -l | grep linux-image | awk '{print $1,$2}'
```
uname -a will how the kernel in use.
dpkg -l | grep linux-image will show what kernels are installed, removed and neither (neither being tried to install but couldn't or tried to remove, but couldn't)
((The awk pipe simply cuts out cruft making it easier to read the bare info needed; no need to read the arch-type (i386 or amd64) nor read the description of the package))

Outputs of installed will show ii
Outputs of removed will show rc (usually)
Outputs for broken will show any number such as iF or iU amongst I think others.
(Easy to understand is that if the second letter is a capital then something's wrong)

try removing one listed as ii that is not the one listed from the uname -a command
You will need to remove both the linux-image and linux-image-extra packages for the one you try
like so
```
sudo dpkg --remove linux-image-4.4.0.4-generic linux-image-extra-4.4.0-4-generic
```
if that removes the one kernel witout errors, then try running the autoremove command
```
sudo apt-get autoremove
```
to see if it can clear out more space.

Once you clear out some space you should be able to install packages properly.

---

### Post by andysharpie on 2017-10-18
I ran the sudo apt-get autoremove and it did clear out space in the /boot file. However, when I opened ccsm last night to change some settings, I had to do a double-take. All the new plugins were installed correctly and I have had no trouble at all with enabling them this morning. My new question is why did I get error messages in the terminal when I installed the new plugins if the plugins are working?

---

