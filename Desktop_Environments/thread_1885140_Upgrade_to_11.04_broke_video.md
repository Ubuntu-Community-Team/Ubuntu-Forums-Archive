---
title: "Upgrade to 11.04 broke video"
date: 2011-11-22
forum: Desktop Environments
---

### Post by Alastair Rae on 2011-11-22
I was running 10.04 on a desktop with an nvidia graphics card. I accepted the offer from Update Manager to upgrade and now my Ubuntu is unusable - the desktop just flashes and I can't access any menus.

I can boot up in recovery mode but I just lost in a maze of X config stuff. Any suggestions or should I just download 10.04 and zap the whole install?

---

### Post by BC59 on 2011-11-22
Do you have access to your command line from recovery mode?

---

### Post by BC59 on 2011-11-22
If you have access to a terminal execute:

```
sudo apt-get install linux-headers-$(uname -r)
```

and then try

```
sudo apt-get install dkms build-essential
```

Then reboot.

---

### Post by LinuxFan999 on 2011-11-22
Please remember that upgrading in place is not recommended. Reinstall Ubuntu 10.04, then download and burn a CD of Ubuntu 11.04 if you want to upgrade.

---

### Post by Alastair Rae on 2011-11-23
> **LinuxFan999 said:**
> Please remember that upgrading in place is not recommended. Reinstall Ubuntu 10.04, then download and burn a CD of Ubuntu 11.04 if you want to upgrade.
So why does the upgrade tool suggest it?

---

### Post by mörgæs on 2011-11-23
That is a looong discussion which we shouldn't revive here. I think it is sufficient to say that a lot of Buntu users would like this option to be removed.

---

### Post by BC59 on 2011-11-23
As already mentioned your options to save the installation are limited.

The solution I mentioned to install the driver, contains a risk with it, so you should judge what to do.

---

### Post by Alastair Rae on 2011-11-23
I fixed my PC by booting a Windows XP recovery disk and replacing grub with the default MBR. I'll keep the Linux partition for trying out another distro if a mature one ever turns up.

---

### Post by mörgæs on 2011-11-23
When you do that some day, just remember to stick to the fresh installs. 

It is too bad that Ubuntu gets a bad name because the upgrades go haywire.

---

