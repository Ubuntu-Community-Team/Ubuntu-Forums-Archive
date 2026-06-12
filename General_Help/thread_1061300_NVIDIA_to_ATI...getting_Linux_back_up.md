---
title: "NVIDIA to ATI...getting Linux back up"
date: 2009-02-05
forum: General Help
---

### Post by jus71n742 on 2009-02-05
I recently went from an NVIDIA 9800 GTX+ to a ATI 4850 HD and I am trying to get the GUI back.  When I try to I get the expected Failed Xserver and the do you want to debug the server...I tried both yes and no but neither will let me log in even with out a GUI.  I would like to know how to get the drivers installed for linux and at least get to a non GUI session.

---

### Post by ajgreeny on 2009-02-05
Try booting to recovery mode and then choosing xfix, or whatever it is called in your version of ubuntu. It may allow you to get a GUI, even if it is the wrong resolution, but you can then probably install the proper driver for the new card using that.

---

### Post by warp99 on 2009-02-05
Which version of Ubuntu are you using since how xorg is configured has changed in version 7.10, 8.04, and 8.10.

---

### Post by jus71n742 on 2009-02-05
> **warp99 said:**
> Which versus of Ubuntu are you using since how xorg is configured has changed in version 7.10, 8.04, and 8.10.

versus?  I am using 8.10 on this particular computer if that is what you ment.

I will try the recovery mode now.

---

### Post by jus71n742 on 2009-02-05
Also need to know how to remove any NVIDIA Drivers on the system.  I think that is the problem with my Windows partition but IDK for sure.  I was running the latest Driver for an Nvidia 9800GTX+

NVM I got the Drivers uninstalled

Ok so I pulled the NVIDIA drivers off. as far as I can tell....I typed 
```
sudo nvidia-installer --uninstall
```
if I need to do more let me know
Now I am trying to figure out how to get this installed...I am looking back at what I did to get the NVIDIA ones on there but I am not sure how to word the ATI one...should also be completely out of x also right?

---

### Post by warp99 on 2009-02-05
> **jus71n742 said:**
> Also need to know how to remove any NVIDIA Drivers on the system.  I think that is the problem with my Windows partition but IDK for sure.  I was running the latest Driver for an Nvidia 9800GTX+

NVM I got the Drivers uninstalled

Normally you uninstall the Nvidia drivers, the ones directly from Nvidia, using the installation program and adding the --uninstall parameter like so:

```
sudo ./NVIDIA-Linux-x86_64-180.xx-pkg.run --uninstall
```

Of course replacing the Nvidia installer version with the version you installed.

To add the drivers for the ATI cards you only need to install the fglrx packages that include the ATI drivers like so:

```
sudo apt-get install xorg-driver-fglrx fglrx-control
```

Now if you haven't used the installer from Nvidia then the package manager will remove the nvidia-glx drivers and replace them with the fglrx drivers.

Once you do that you should be able to run in reduced video mode, then you can configure the display using the ATI control panel application.

---

### Post by jus71n742 on 2009-02-05
I had package 177.80 in NVIDIA drivers and it is saying that it can not find the package sooo does that mean its gone?  I am attampting to install the ati drivers again.  I did not have the last package you suggested for installation but I do now.

Now I installed the driver again ...this time after a reboot nothing is displayed on the screen at all.

---

### Post by warp99 on 2009-02-06
Even if you had Nvidia drivers installed you would still be able to run the open source ATI drivers. The open source ATI driver should be already installed on your system unless you removed it. Run the following so you can install the open drivers:

```
sudo apt-get install xserver-xorg-video-all
```

That will install all of the video drivers plus any dependencies. Since they're separate they can be installed with the fglrx drivers. Xorg should pick them up and give you reduced video mode so you can configure the fglrx drivers which are the proprietary ones from ATI.

---

### Post by jus71n742 on 2009-02-06
> **warp99 said:**
> Even if you had Nvidia drivers installed you would still be able to run the open source ATI drivers. The open source ATI driver should be already installed on your system unless you removed it. Run the following so you can install the open drivers:

```
sudo apt-get install xserver-xorg-video-all
```

That will install all of the video drivers plus any dependencies. Since they're separate they can be installed with the fglrx drivers. Xorg should pick them up and give you reduced video mode so you can configure the fglrx drivers which are the proprietary ones from ATI.

Already at the newest version.

Now however when I go into linux I get either NO logonscreen or anything after the loading screen or I can't edit the settings for the card.  Says the driver isn't configured correctly.

---

### Post by warp99 on 2009-02-06
Check the log file /var/log/Xorg.*.log to see which driver is attempting to load. Also if you have an xorg.conf file in /etc/X11/ you should rename it since it's most likely configured for the Nvidia drivers.  

Intrepid (8.10) doesn't use an xorg.conf by default, but can use one if installed by a different program.

---

### Post by jus71n742 on 2009-02-08
> **warp99 said:**
> Check the log file /var/log/Xorg.*.log to see which driver is attempting to load. Also if you have an xorg.conf file in /etc/X11/ you should rename it since it's most likely configured for the Nvidia drivers.  

Intrepid (8.10) doesn't use an xorg.conf by default, but can use one if installed by a different program.

I ran the ```
sudo sh *run
```
command and the installer ran again.  this time after I typed ```
aticonfig -- initial -f
``` to wipe the xorg file and maybe then it will reset.

---

### Post by jus71n742 on 2009-02-09
What exactly should I look for. I am not sure exactly what I am looking for.  I see where its loading extensions but like I said...not really sure what I am looking for.

---

### Post by warp99 on 2009-02-09
In your Xorg.0.log you should be looking for this:

```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.47.3
        Module class: X.Org Video Driver
```

And any errors that may give you more information on why the above is not loading correctly. You should also run the following:

```
dmesg |more
```

Checking for errors on why the driver is not loading. Just press the space bar to scroll through the info. And last with the fglrx driver there is a script to gather information on you system named "atigetsysteminfo.sh" which will generate a report. Go through that and check for errors.

---

### Post by jus71n742 on 2009-02-09
> **warp99 said:**
> In your Xorg.0.log you should be looking for this:

```
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 7.1.0, module version = 8.47.3
        Module class: X.Org Video Driver
```

And any errors that may give you more information on why the above is not loading correctly. You should also run the following:

```
dmesg |more
```

Checking for errors on why the driver is not loading. Just press the space bar to scroll through the info. And last with the fglrx driver there is a script to gather information on you system named "atigetsysteminfo.sh" which will generate a report. Go through that and check for errors.

OK thanks...here is what mine says
```

(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5

```
then when I run dmesg |more I see this and I am again guessing as to wether or not its relevant 
```

[   43.992141] ACPI: bus type pci registered
[   43.992220] PCI: Using configuration type 1

```

I have also used the ```
ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/8.10
```
This created a lot of .deb files and I am not sure what needs to be done with them?

and again ...on that last part I am guessing

---

### Post by Yashiro on 2009-02-10
Assuming you've purged nvidia stuff from your machine.

Running:
> ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/**8.10**
will give you the .deb package files. If you're running another build of Ubuntu substitute your build name above. 
Running *sudo ati-driver-installer-9-1-x86.x86_64.run --listpkg* will tell you what names to use.

These are the md5 hashes of the .deb packages if you wish to check.
> 7c2257608a61d56aaeb1997e8a15391c  */home/ati/9.1/fglrx-kernel-source_8.573-0ubuntu1_amd64.deb*
5caa54cca422d80825382438533bf7e0  */home/ati/9.1/fglrx-amdcccle_8.573-0ubuntu1_amd64.deb*
fc16d2ce724d5c44b0cfe5b253ed96ff  */home/ati/9.1/fglrx-modaliases_8.573-0ubuntu1_amd64.deb*
9d9e0470838f39c628b1dfc8823aa168  */home/ati/9.1/libamdxvba1_8.573-0ubuntu1_amd64.deb*
68b4fe530ef0ee1763ba6c44e829b976 * /home/ati/9.1/xorg-driver-fglrx_8.573-0ubuntu1_amd64.deb*

Now make sure that */etc/modprobe.d/blacklist-local *
contains *[COLOR="RoyalBlue"]# blacklist fglrx[/COLOR]*. The hash means it's NOT blacklisted. Which for this file is what we want.
Add lines here to blacklist any nvidia display modules, if you have them installed.

Also check*/etc/default/linux-restricted-modules-common*
contains *[COLOR="RoyalBlue"]DISABLED_MODULES="fglrx"[/COLOR]*
This disables the fglrx module from the Ubuntu repositories.
Supposedly not needed anymore with the new modalias .deb but I have it there from way back anyway.

Reboot and select the recovery mode kernel from grub. Drop into root console.
(Or get root via whatever means you see fit, sudo -i, su - whatever)

If you have an Ati driver already installed do: 
> rmmod fglrx
Skip if you don't.


Now, navigate to the folder where you have those .deb files from earlier.

Run
> apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms ia32libs linux-headers-$(uname -r)
> dpkg -i fglrx-kernel-source_*.deb
dpkg -i fglrx-amdcccle_*.deb
dpkg -i fglrx-modaliases_*.deb
dpkg -i libamdxvba1_*.deb
dpkg -i xorg-driver-fglrx_*.deb
That should be the driver installed now. 

Run
> aticonfig --initial -f 
If you are not upgrading from an older Ati driver xorg config.

Reboot.

[I]This method has not failed for me yet unlike the default install and other scripts I have tried. Some parts here can be done without the need for rebooting. But for tutorials sake just reboot unless you know what you're doing. In which case you don't need this lame tutorial.

Here's the list of commands used.

ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/8.10
apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms ia32libs linux-headers-$(uname -r)
dpkg -i fglrx-kernel-source_*.deb
dpkg -i fglrx-amdcccle_*.deb
dpkg -i fglrx-modaliases_*.deb
dpkg -i libamdxvba1_*.deb
dpkg -i xorg-driver-fglrx_*.deb
[/I]

---

### Post by zika on 2009-02-10
sudo dpkg-reconfigure -phigh xserver-xorg

read the thread: [http://ubuntuforums.org/showthread.php?t=1056070](http://ubuntuforums.org/showthread.php?t=1056070)

---

### Post by jus71n742 on 2009-02-11
Not sure what I did but I do have the screens going.  Now would any one know of a way to still use Compiz Fusion in order to use the cube?  I know I had it going with the dual monitors configured independently but I am not sure about ATI and 3 monitors.
So any help is appreciated.

---

