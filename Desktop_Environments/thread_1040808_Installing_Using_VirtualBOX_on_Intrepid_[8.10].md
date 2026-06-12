---
title: "Installing/ Using VirtualBOX on Intrepid [8.10]"
date: 2009-01-15
forum: Desktop Environments
---

### Post by physeetcosmo on 2009-01-15
Thanks to all the posts out there on the net that have added to this posting for Ubuntu. I have officially tested VirtualBOX 2.1.0 hosted in Ubuntu 8.10. It installs great but there are some prerequisites that need to be installed and some tweaking after it is installed.

Thank you too the posting from ubuntugeek.com, these next lines add the repositories:

```
$ sudo gedit /etc/apt/sources.list
```

add this line to the end of the file:

```
$ deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```

Exit and enter in Terminal:

```
$ wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install dkms
$ sudo apt-get install virtualbox-2.1
```

dkms stands for Dynamic Kernel Module Support which is used to build kernel interfacing between the Ubuntu OS and the Guest OS (if I'm wrong or not quite right here, someone correct me please :)).

The USB controller on the eeePC 1000 doesn't 'pipe' properly through to the Guest OS, thus HDD, Development Boards, Mice with special features aren't recognized in the Guest OS. There is an icon on the bottom of the VirtualBOX Guest OS window that looks like the end of a USB cable. Right-click the icon to get a list of the devices able to be captured by the Guest OS. When I first installed VirtualBOX without these next mods, there weren't any devices listed at all.

Thank you davidgrant.ca for the help! Here's some of his suggestions that I've re-ordered. This is done AFTER the Guest OS has been installed.
Make sure when the following command is entered that <i>your</i> username is listed at the end:

```
$ grep vbox /etc/group
```

The following output should be listed:

<i>vboxusers:x:<gid>:<b>username</b></i>

If the username of the user (you) isn't listed, the user must click System &#8594; Administration &#8594; Users and Groups. Click 'Unlock' and enter the root password, then click 'Manage Groups' and scroll down and click 'vboxusers' then click 'Properties' and make sure the user's username is selected (as well as root, might as well).

Step 2 will be to execute the following commands:

```
$ sudo gedit /etc/init.d/mountkernfs.sh
```

What is going on here? We are editing the USB interface  to use the same id as the vboxusers, which we received as output from the last command line. Place the following after the mount command for /proc, what this does I'm not sure, anyone care too comment <i>why</i> we place the mounting usb devices after the mounting of /proc?

```
domount usbfs "" /proc/bus/usb usbdevfs -onoexec,nosuid,nodev,devgid=<gid>,devmode=664
```

For me the 'gid' is 126, for you it might (probably will be) something else.

Now, reboot.

Tada! If this still doesn't help you, make sure you don't have ANY USB filters assigned in VirtualBOX Settings window. This field should be 'filter-free'.

If there's anything any of you Uber-Ubuntu Brains know anything to add, please do!
:)

---

