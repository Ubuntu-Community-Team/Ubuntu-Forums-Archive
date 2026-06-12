---
title: "[SOLVED] Virtual Box Error"
date: 2007-12-29
forum: Desktop Environments
---

### Post by jose158 on 2007-12-29
Okay, I'm trying to start a Virtual machine and I got this error: ```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
``` Any help? Thanks

---

### Post by kelbizzle on 2007-12-29
Maybe you missed the step to add your user to the vbox group. Or the Second part you haven't restarted or reloaded the driver. I just restarted so I didin't have any issues. Don't forget to install guest additions.

Heres how I installed it.
```
First, we install VirtualBox Open Source Edition :

sudo apt-get install virtualbox-ose virtualbox-modules-`uname -r`

and we add our user to the group of users allowed to run VirtualBox :

sudo adduser $USER vboxusers

Now, you need to restart your computer to apply this modifications.
Instant run

If you want to launch VirtualBox without restarting your computer, run the following command lines :

sudo /etc/init.d/udev reload
sudo modprobe vboxdrv
su -c virtualbox $USER

At the end of the last command, type your password to run VirtualBox.
```

---

### Post by linux4me on 2007-12-29
I was getting the same error as jose using the version of VirtualBox in the repositories, and I had added myself to the users in the group "virtualbox".

I tried using your steps to install VirtualBox after removing it using Synaptic, but found that the process failed because the kernel I am using (from uname) is 2.6.22-14-386, whereas the modules file for VirtualBox is called 2.6.22-14-generic.

Instead, I downloaded the current version of VirtualBox from [www.virtualbox.org](www.virtualbox.org) and installed it using the following command:
```
sudo dpkg -i virtualbox_1.5.4-27034_Ubuntu_gutsy_i386.deb

```

Ubuntu then helpfully informed me that I was missing two dependencies:
> Selecting previously deselected package virtualbox.
(Reading database ... 130601 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.5.4-27034_Ubuntu_gutsy_i386.deb) ...
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
jsherman@Albatross:~/Desktop$ sudo apt-get install libxerces27
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  virtualbox: Depends: libxalan110 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So I ran the following:
>  sudo apt-get -f install
After which Ubuntu installed the dependencies, configured VirtualBox, and I was able to start VirtualBox from the Applications->System Tools menu, configure my VM, and it ran flawlessly.

It seems like there is a problem with the version of VirtualBox in the repositories?

---

### Post by markharding557 on 2007-12-29
when i had this problem the solution i found was adding "nmi_watchdog=0"to the end of the kernel line in boot/grub/menu.1st.(reboot after adding)
the nmi watchdog was preventing virtualbox driver from loading.
worked anyway

---

### Post by jose158 on 2007-12-29
Keep getting this.
[ATTACH]54614[/ATTACH]

---

### Post by jose158 on 2007-12-29
Never mind. I fixed it. Just had to log out for the changes to take affect.:lolflag:

---

### Post by linux4me on 2007-12-31
> **markharding557 said:**
> when i had this problem the solution i found was adding "nmi_watchdog=0"to the end of the kernel line in boot/grub/menu.1st.(reboot after adding)
the nmi watchdog was preventing virtualbox driver from loading.
worked anyway

I read about disabling NMI_watchdog, but after reading [this article]("http://www.mjmwired.net/kernel/Documentation/nmi_watchdog.txt") it seemed like it might not be a good idea?

---

