---
title: "feisty is not booting but ok in recovery mode"
date: 2008-04-07
forum: Desktop Environments
---

### Post by venkatat on 2008-04-07
Hi ,

Today i have been downloading some games from Add/Remove after some time some were got failed to download later i went reboot after installed rest of the games ( note : i was logged as ordinary user) . While rebooting the file system damaged and i run *fsck* I press 'Y' to which ever it asked. 

The story ends and done reboot ..this time after loading everything fine the system is hanging (?) rather not showing any progress after loading network module ( this is OK) but i can see some messages on top it as some folder is not there in /etc/modules ( i forgot ) ...


but while running in recovery mode every thing is fine. no error messages like above and i am able to start X by typing *startx* 

Can any one suggest work around for this

---

### Post by venkatat on 2008-04-07
i found the problem ..there are some folders missing in /etc 

those are /etc/modprobe.d/*.*

/etc/network/if-up.d   

etcetera...

But without these folder , iam able to login in and this post i am writing from the same recovery mod. Is there any way to restore without re installing ubuntu...


Please help me....

Thanks in advance
Venkat

---

### Post by prshah on 2008-04-07
> **venkatat said:**
> i found the problem ..there are some folders missing in /etc 
those are /etc/modprobe.d/*.*
/etc/network/if-up.d   
etcetera...
But without these folder , iam able to login in and this post i am writing from the same recovery mod. Is there any way to restore without re installing ubuntu...


I would think you have no way out except a reinstall.

You CAN try to boot into recovery mode, then do a sudo cp of the /etc/modprobe.d/* to your actual installation, but I don't think it will work.

You can also look in the lost+found folder to see if the files are present there. If they are, you can just sudo mv them back to the original location.

---

### Post by warp99 on 2008-04-07
Do the following:

```
sudo apt-get install --reinstall module-init-tools alsa-base fuse-utils linux-restricted-modules-common acpi-support
```

this will re-install the lists in /etc/modprobe.d. If you have an nvidia card then add the package nvidia-kernel-common to the list.

Hint:

If your missing **any** file you can just re-install the package with the file by using the 'Search the content of packages' dialog at [packages.ubuntu.com.]("http://packages.ubuntu.com/") 

So you can recover the items if the damage is not to extensive by re-installing the individual packages. If the damage is extensive you can try the following:

```
sudo apt-get install --reinstall ubuntu-desktop
```

There is absolutely no need to re-install Ubuntu unless there is a catastrophic event.

Edit:

Switch ubuntu-desktop with kubuntu-desktop or xubuntu-desktop if you're running these instead.

---

### Post by venkatat on 2008-04-18
Thanks all guys !!! any how i have re installed ubuntu completely..i can't apt-get as i have so network connectivity .

---

