---
title: "[SOLVED] Restricted Mgr/Synaptics/Envy vs. NVIDIA drivers"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by DonDodge on 2008-02-19
MSI MS-7325 v1.0 (K9N4 SLI)
AMD64 X2 5000+ Black Edition
Corsair TWIN 2X2048-6400C4 G
AMI BIOS v.1.5
Win XP Home SP2/Ubuntu 7.10
NVIDIA GeForce 7300 LE (MSI NX7300LE 256 MB)


I've been going around in circles for days trying to install the restricted NVIDIA driver to this new computer and new Ubuntu installation.

Previously I had an old PIII with Intel 80815 chipset using onboard video. Of course, compiz wouldn't run on that one and my Ubuntu installation was problematic and subject to random crashing . 

When I built the new computer, Ubuntu ran and I was very easily able to install the restricted driver using the restricted driver manager and was able to use the entire array of desktop effects... but the installation itself was even more problematic so I had to do a reinstall of Ubuntu.

I did a fresh install and tried to install the nvidia-glx-new by way of the Ubuntu methods. No go - no way.. Went around in circles with that plan.

Another fresh install and try using Envy to get the restricted driver to work. Again, no way. Envy has attempted with numerous combinations and it won't work. I've been goofing with this for three days straight. Yesterday I tried to manually install of NVIDIA-Linux-x86-169.07-pkg1.run that I downloaded from nvidia's website. Didn't work.

I can run Envy from the GUI, the terminal or a black screen prompt and I always wind up at the same place. It detects my card and chooses the proper driver. No problem there.   It's working great to install the driver, configure x and restart the computer but then it gets weird. Ubuntu will not boot and will not even reach a prompt. Just a dead black screen with either a few:starting lines or complete loss of signal to my monitor. Leaving it here for hours will not produce a boot. After that, do a hard reset and get a boot but I reach the insipid low res box with the doublewide X cursor that says my screen and my video card could not be detected. 

After that I'm on the generic low res vesa driver. Then go to the restricted drivers manager and enable driver, see all the messages and do the requisite restart.... always winding up back at the low res box and the vesa driver. After this point, the driver remains enabled and in use in "restricted" but it doesn't work. Attempting to load the "Proprietary" driver in Screens and Graphics always results in a system that won't boot.

Running sudo dpkg-reconfigure -phigh xserver-xorg always takes me back to the nvidia riva tnt driver.

I can edit /etc/default/linux-restricted-modules-common and change the value from:
DISABLED_MODULES="nvidia nvidia_legacy" to
DISABLED_MODULES="nv nvidia_new" and then do a reinstall. Same thing. No boot, then reset, then the low res box, then enable the restricted driver and then I can watch root rewrite linux-restricted-modules-common right before my eyes and the cycle begins again.

How can I fix this? Is it possible to take writing capability away from root for the linux-restricted-modules-common file? If I did this, would this thing have a shot at actually using the driver and the compiz?

Otherwise, the system seems to be as good and stable as it can be. Just no 3D or acceleration from my card.

---

### Post by DonDodge on 2008-02-20
No help on this? Am I posting in the wrong forum?

Ubuntu is now completely updated. No changes in video status.

16 hours of downloading updates - install and do the reboot
reconnect - run sudo envy -t from terminal, envy properly ID's the graphics card, wants no new downloads and  produces no errors
let envy configure x and do the reboot
start up in vesa low graphics mode
enable restricted driver - reboot
no boot, do hard reset
start up in vesa low graphics mode

There seems to be no way out of this loop.

---

### Post by chavanak on 2008-02-20
Wow this really looks odd!! People are praising envy for simplifing the job and here is something new.... Have you tried reinstalling ubuntu... Its a pain in the back but if nothing works and no one else replies, that might be the last option.

---

### Post by DonDodge on 2008-02-20
I installed Ubuntu a few times in attempt to use the common methods of installing the driver.

Envy was first run on a newly installed Ubuntu.

I'm reluctant to start overagain because I've had to do over 24 hours of downloading just to get all the stuff Envy wanted and all the Ubuntu updates. Seems like there should be a way to pull this out of the fire.

---

### Post by DonDodge on 2008-02-21
Hopefully I can get tseliot to come by and have a look. He's probably the only chance I have of identifying the problem. I don't know where to go from here. 

This would be a whole lot less confusing had I not gotten the restricted driver to function so easily on an old and broken Ubuntu installation. On that installation, I merely had to activate "Desktop Effects" and let the system go get what it wanted to make it work. This required a 4.8 mb download and was all done in a very short time. 

It would also be more understandable if I was having any trouble at all running the latest driver in windoze.

The next attempt, from a fresh install, also failed. Here's what I did.

Format partition and install x86 Gutsy. Computer sets up to use the nvidia riva tnt driver.
cp the deb update packages back to /var/cache/apt/archives
Set repositories with software sources and reload
Select, get and install updates with Update Manager
Take a backup image for restoring to pre-Envy status
GDebi install Envy from envy_0.9.10-0ubuntu2_all.deb which wanted additional files from the Ubuntu cd and internet. (Previous installs w/dpkg, GDebi and probably apt-get install)
Verify dependencies.
Run Envy from menu as su
Envy properly detected my graphic card as a GeForce 7300 LE and says it's supported by the latest driver.

Envy ran properly with no errors until reaching this point when it states:
------------------------------------------
Processing triggers for libc6
loconfig deferred processing now taking place
An installer has been detected
md5new: d4d8cd98f00b204e9800998ecf8427e
md5sumold: 26a7f94908bbe07a1110fd78cfa81320
ENVY ERROR: md% error! trying to fetch driver from the website
No installer detected
Download of driver in progress, please wait
--01:15:47--  [http://us.download.nvidia.com/XFree86/Linux-x86/169.09.pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.09.pkg1.run)
	=>  NVIDIA-Linux-x86/169.09.pkg1.run
Resolving us.download.nvidia.com... 88.221.26.48, 88.221.26.43| :80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17,634,730 (17M). [application/octet-stream]
----------------------------------------------
Once the driver is downloaded, Envy proceeds without hesitation or errors, configures the xserver and restarts the computer. From here, the continual loops of failure begin again by either failing to boot or restarting in vesa mode. Enabling the driver in Restricted Driver Manager produces a boot failure.

Here are excerpts from various xorg.conf files:

xorg original
Section "Device"
	Identifier	"nVidia Corporation G72 [GeForce 7300 LE]"
	Driver		"nv"
	BusID		"PCI:5:0:0"
EndSection

xorg after running envy
Section "Device"
	Identifier	"nVidia Corporation G72 [GeForce 7300 LE]"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

xorg after getting computer to boot again
Section "Device"
	#                
	Identifier	"device1"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:5:0:0"
	Screen	1
EndSection

The continual reversions back to vesa mode sometimes disables the restricted driver in "Restricted Drivere Manager" and sometimes leaves the status as enabled and in use. 

Manually resetting the driver back to the original nvidia riva tnt the first time made this change in xorg.conf.
Section "Device"
	Identifier	"Failsafe Device"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:5:0:0"
	Screen	0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Subsequent resetting of the driver back to nvidia riva tnt does this.
Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"

	#                
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Editing the "linux-restricted-modules-common" gives the same result as above. Root always rewrites it immediately. An attempt to lock root out of the file results in root putting a lock on the file so that his changes can't even be viewed.

As usual, all roads lead to low graphics mode/generic vesa driver @ 800x600 when attempting to use the restricted driver. To get a decent resolution I have to manually change back to the nvidia riva tnt driver. 

All iterations of xorg.conf after the original Envy generated file include the lollowing

# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

I get this result when running: sudo dpkg-reconfigure -phigh xserver-xorg

Package `xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg/ is not installed

Running the dpkg-reconfigure of xserver as suggested by xorg.conf results in a computer that won't boot. This sets up a complete loss of signal to the monitor that requires a hard reset. Then it's right back to low graphics mode. Manually selecting the nvidia proprietary driver in 'Screens and Graphics" gives  the same result.... dead computer

I can post the complete output /var/log/envy-installer.log if it may hold pertinent information.

Could I have a corrupted Envy package? 
Could it possibly be a fault with my monitor causing the problems?

---

### Post by DonDodge on 2008-02-29
Figured it out. Beware of Envy.. It's no solution.

---

### Post by pwcabach on 2008-02-29
So what was your solution? 

I've tried all of the recommendations that I could find and still in the black, or low-res mode.

Thanks.

---

### Post by solitaire on 2008-02-29
One thing to try is always set your Resolution to 800x600 before upgrading nVidia drivers with Envy.

It does not look nice but you should be able to get back into the Desktop

Also make sure your Monitor settings are correct after it's been installed ( you'll have to pick the closest make/model if it's not listed) then check the diffrent Hz try a low one say 50Hz then see if you can see a larger range of Screen sizes.

Envy is not the perfect package but it's a good helper if you set things correctly.

If all else fails, Remove all the Nvidia drivers and Envy and install manually :D lol!!

There will usually be a few others giving their hints and tips :D

---

### Post by DonDodge on 2008-02-29
> **pwcabach said:**
> So what was your solution? 



You won't believe me if I tell you but I'll tell you anyway. I formatted the drive that held my 3 week old windoze installation and reinstalled it. 

The next time I booted Ubuntu, the nvidia restricted driver installed straight from the Restricted Drivers Manager and started working. immediately.  Desktop effects enabled without a complaint and then all I had to do was install all the compiz controls,. Now, everything looks good but I'll probably do a fresh install of Ubuntu and get all new updates because I'm afraid of crossover corruption. Earlier this week the windoze made the computer go completely insane.

Apparently XP had a corrupted HAL that started going really bad about the time I did my fiirst new Ubuntu install.  No matter how hard I chased my tail, the corrupted windoze was wacking out the computer so badly the nvidia system couldn't work. 

Strange but true.

---

