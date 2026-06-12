---
title: "Virtualbox mayor beginner problem"
date: 2008-08-08
forum: Desktop Environments
---

### Post by F0XX on 2008-08-08
Just installed Virtualbox and when i try to start the new machine its not installing, and a error pops up and reads: 

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

please help me, thanks

---

### Post by whitey on 2008-08-08
Hello Foxx,

If you just installed the Virtualbox kernel module, then you'll have to reboot your machine for the kernel addition to be absorbed.  If that doesn't work paste the error.

~whitey

---

### Post by F0XX on 2008-08-08
still get the error :(

---

### Post by whitey on 2008-08-08
Did you use apt-get to install VirtualBox, or did you install it from source from the Sun website?

---

### Post by F0XX on 2008-08-08
just apt-get install

---

### Post by aveightor on 2008-08-08
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

From a terminal:

$ ls -l /dev/vboxdrv
crw-rw---- 1 root vboxusers 10, 62 2007-10-08 13:27 /dev/vboxdrv

If the group is not set to vboxusers, reload the kernel module:

sudo rmmod vboxdrv
sudo modprobe vboxdrv

Add yourself to the vboxusers group. You can add more usernames after "whoami" if you wish.

sudo gpasswd -a `whoami` vboxusers

To automatically load the kernel module (driver) at boot time you need to run the following to append vboxdrv to /etc/modules

echo "vboxdrv" | sudo tee -a /etc/modules

You will now have to log out of your desktop session and log back in order to update your group membership. Congratulations, you can now skip down to "Using Virtual Box"

---

### Post by F0XX on 2008-08-08
thanks for the help got it working now

---

### Post by chauhanmail@gmail.com on 2008-08-09
> **aveightor said:**
> [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

From a terminal:

$ ls -l /dev/vboxdrv
crw-rw---- 1 root vboxusers 10, 62 2007-10-08 13:27 /dev/vboxdrv

If the group is not set to vboxusers, reload the kernel module:

sudo rmmod vboxdrv
sudo modprobe vboxdrv

Add yourself to the vboxusers group. You can add more usernames after "whoami" if you wish.

sudo gpasswd -a `whoami` vboxusers

To automatically load the kernel module (driver) at boot time you need to run the following to append vboxdrv to /etc/modules

echo "vboxdrv" | sudo tee -a /etc/modules

You will now have to log out of your desktop session and log back in order to update your group membership. Congratulations, you can now skip down to "Using Virtual Box"



hi i followed your procedure and now running virtual box successfully, but i am in big trouble now i cannot do any administrative task on my login and denied from accessing user-group and software addremove and all other administrative tasks and my user name is not in sudoers file even.

please help me to restore to the full admin rights, i am very frustrated now searching forums and now planning to format ubuntu.

please help.

screen shot attached

---

### Post by aveightor on 2008-08-09
That was copied from the Ubuntu Wiki. Can you try sudo -i, if that works do nano -w /etc/group and make sure your user is in the adm group. Sudoers uses the admin group not your username.

---

### Post by andho on 2008-08-13
hello
i run this command so i lost all administrative rights
```
sudo usermod -G vboxusers andho
```

so you mention that i need to be in adm group. i find the adm group as so:
```
adm:x:4:
```

i find my user two lines of these
```
andho:x:1000:www-data
sambashare:x:124:
winbindd_priv:x:125:
vboxusers:x:126:andho
```

so where do i need to add my user

---

