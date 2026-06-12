---
title: "[SOLVED] unable to resolve host"
date: 2008-09-25
forum: Desktop Environments
---

### Post by MacDuff on 2008-09-25
Have been trying to get a USRobotics USB modem to work with my Ubuntu machine without success but after trying several things, I find that I have now broken my wireless network and appear to have lost root privileges.

When I try to do anything in a terminal using the sudo command, the following message appears:
sudo: unable to resolve host T-61
sudo: /etc/sudoers is mode 0460, should be 0440

How can I fix this please and thank you.

---

### Post by sisco311 on 2008-09-25
reboot in recovery mode and in the *root shell* type:

```
chmod 0440 /etc/sudoers
```

open the /etc/hosts file for editing:
```
nano /etc/hosts
```
and edit it to look like this:
> 127.0.0.1	localhost
**127.0.1.1	T-61**

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
(change T-61.*?XYZ?* in the second line to T-61)

save the file and exit(Ctrl+o, Enter, Ctrl+x)

type:
```
exit
```and select the *resume normal boot* option.

---

### Post by MacDuff on 2008-09-25
sisco311, your suggestion makes sense and I will give it a try as soon as I have finished backing up the Home directory on that computer.  I may have broken it so badly by trying out a bunch of edits to make the USB modem work that it may be better to rebuild the system.

I have a follow-up question if you don't mind. Forgive me for being so thick.  You suggest changing the computer name to "T". I understand that  "/etc/hosts" and /etc/hostname must have the same name.  That has always been "T-61" but several times in the past few weeks as I have been struggling with networking, I have found that something in the system has changed the name in "hosts" by adding ".DHLTD" as a suffix. DHLTD is local workgroup (domain?).  When that happens things seem to go in the ditch. I have been able to fix things by editing the offending file as root. This is the first time I have had a problem with the mode setting.

Does your suggestion to change the name to "T" suggest that I should not have the "-" in the name or were you making an assumption that "-61" was the error?

Any advice would be appreciated very much by this old man.

---

### Post by sisco311 on 2008-09-25
> **MacDuff said:**
> sisco311, your suggestion makes sense and I will give it a try as soon as I have finished backing up the Home directory on that computer.  I may have broken it so badly by trying out a bunch of edits to make the USB modem work that it may be better to rebuild the system.

I have a follow-up question if you don't mind. Forgive me for being so thick.  You suggest changing the computer name to "T". I understand that  "/etc/hosts" and /etc/hostname must have the same name.  That has always been "T-61" but several times in the past few weeks as I have been struggling with networking, I have found that something in the system has changed the name in "hosts" by adding ".DHLTD" as a suffix. DHLTD is local workgroup (domain?).  When that happens things seem to go in the ditch. I have been able to fix things by editing the offending file as root. This is the first time I have had a problem with the mode setting.

Does your suggestion to change the name to "T" suggest that I should not have the "-" in the name or were you making an assumption that "-61" was the error?

Any advice would be appreciated very much by this old man.
Sorry, my bad.
You should change T-61*.whateverIsHere* to T-61 .

---

### Post by MacDuff on 2008-09-25
Thank you sisco311

That fixed the problem of not being able to obtain root privileges. 

Now I just have to sort out why I cannot get a network connection anymore. Perhaps I won't have to rebuild the system after all.

I appreciate your help very much.

---

