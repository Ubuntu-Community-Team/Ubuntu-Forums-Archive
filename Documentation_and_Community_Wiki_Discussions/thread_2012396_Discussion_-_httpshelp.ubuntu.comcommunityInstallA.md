---
title: "Discussion - https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriv"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)

Support threads should be posted in normal forums.

Thank you.

---

### Post by SuperFreak on 2013-10-18
Where do I find support for this . When I issue command sudo ./MultiBootUSB.sh I get command not found. As far as I can tell extracting the script does not create a folder called MultiBootUSB and if I create that folder with the Debian and usr folders in ith with executable priviledges it still doesn't work

---

### Post by heehau2 on 2014-06-12
Love the switch to .deb format! Would be nice if you changed the instructions to match, though, for poor fellas like the guy above me.

There is one problem in the .deb file, in that it repackaged pyudev. That's already installed on my system, so there is a conflict that cannot be resolved. Any chance you could update the package to include pyudev as a dependency?

---

### Post by Darth Riker on 2014-12-05
I built a usb drive with the 14.04.1-desktop-i386 distros of Ubuntu, Lubuntu, and Xbunutu using MultiBootUSB for Windows.

When I boot from the drive - I need to use the "forcepae" flag (as outlined here: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)). However, when I scroll down to the distro I want to load, and press [Tab], I don't see a line that ends with "quiet" or "quiet splash --" for me to then add "forcepae".

The reason I need to use "forcepae" is because when trying to load, say Ubuntu, I receive the message:

> ERROR: PAE is disabled on this Pentium M (PAE can potentially be enabled with kernel parameter "forcepae" - this is unsupported, may cause unknown problems, and will taint the kernel)
This kernel requires the following features not present on the CPU: pae
Unable to boot - please use a kernel appropriate for your CPU.

If I were to load just one distro to the USB (using Pen Drive Linux's USB Installer as outlined here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)) then I am able to bring up the line to enter "forcepae" and boot successfully.

My system is as follows:

Dell Inspiron 8600 Notebook (currently running Windows XP SP3)
Intel Pentium M 745 1.8GHz
1 GB RAM
128MB ATI Mobility Radeon 9600

---

### Post by Darth Riker on 2014-12-05
Doh! Sorry. I resolved my own issue.

After selecting the distro I wanted to load - I didn't press a key to bring up the Advanced Welcome Page Options! (as outlined here: [https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)).

Once I was able to bring up those I options, I then highlighted the option to "Try ...", pressed F6, then Esc, then was able to type in forcepae and press enter. Booted up successfully.

---

