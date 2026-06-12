---
title: "ATI Open Source Drivers with Direct Rendering"
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by Kubunteando on 2007-01-06
I have been having lots of troubles with the ATI proprietary drivers in edgy and in dapper.
I use an ATI Mobility Radeon 9000 with 32MB, and the newest and last drivers supported are the 8.28.8 which are then ones in the Ubuntu official repositories.

And I think I am not the only one.
For the ones in the same situation (last supported drivers for your card being 8.28.8)
(You can check: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) )

I would like to know if someone has experienced some of these problems:

1- Cube 2 Sauerbraten becomes really slow after a couple of minutes. No way to play
2- Never Winter Nights gets choppy after playing 1 hour or so
3- Your computer hangs when shutting down Ubuntu
4- Regnum Online crashes or hangs after loading but before start playing

Please, post your model of ATI card and your version of Ubuntu.

I get the 4 of them if I use the ATI 8.28.8.

So I changed to the Open Source Drivers with Direct Rendering  (HW Acceleration):
[www.mesa3d.org](www.mesa3d.org)
dri.freedesktop.org

I have been able to solve 1,2 and 3 , but not 4 so I cannot play Regnum Online.
According to some threads on Regnum Forums, it seems it has not been tested with the Open Source Drivers.

If you have found any other solution let us know. 
Also your comments.

---

### Post by EdThaSlayer on 2007-01-06
Regnum Online works perfectly on my laptops ATI Radeon Mobility 9600(128 mb of vram).
I used the old proprietary drivers, the very easy to install drivers(the ones in the repositories). 

It runs on Dapper Drake though since in Edgy Eft the frame rate drops to like 250 fps MAX(meaning that my Dapper Drake laptops graphics card seems to pump out sooooo much more graphic power than my desktop with its ATI radeon 9600, even though desktop graphic cards are supposed to be twice the speed of a equivalent laptop graphic card).

On my Edgy Eft desktop(with the ATI drivers installed) cube 2 saurenbraten doesn't even start and Regnum Online experiences frequent crashes.

---

### Post by Fitzy_oz on 2007-01-07
After weeks of messing about with the driver I have managed to get Direct 3d Rendering working for the 9600SE.  The problem appeared to be with Kernel Module.  Follow This Guide exactly (This is an extract from the unofficial wiki, it is important to note that only these steps worked for me, NOT, I repeat NOT the entire process"

*Download the ATI driver installer: ati-driver-installer-8.x.x.run (this installer is for 32bit and 64bit systems).

*Install the Tools
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

*Create the install packages
bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper

*Install the packages (Note: This is where the howto broke down for me)
sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb -f
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb -f
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb -f 

*Remove any old Sources:
sudo rm /usr/src/fglrx-kernel*.deb

*Build and Install The module
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

*Edit your xorg.conf and add the highlighted lines if they're not already there:

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
     [COLOR="Red"]   Load    "fglrx[/COLOR]
      [COLOR="Red"]  Load    "dri"[/COLOR]
        Load    "extmod"
        Load    "freetype"
[COLOR="Red"]        Load    "glx"[/COLOR]
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

ection "Device"
        Identifier      "Generic Video Card"
        Driver          [COLOR="Red"]"fglrx"[/COLOR]
        BusID           "PCI:1:0:0"

*Chances are you will need to add this line also:
[COLOR="Red"]Section "Extensions"
        Option "Composite" "Disable"
EndSection[/COLOR]

After you have completed these steps you should be able to reboot and check to see if the driver has initialized by typing #fglrxinfo in a terminal or glxinfo |more should return something like this:


OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600SE Generic
OpenGL version string: 2.0.6234 (8.32.5)


That's It,
May not work for everyone, but I'd tried just about everything else.

---

### Post by Kubunteando on 2007-01-09
I open a ticket complaining about the issues with the ATI drivers 8.28.8, and ATI now AMD says that they don't provide direct support for Laptops and Notebooks. So I should turn to the laptop manufacturer in this case Dell. I will try and see.

The situation is funny since ATI/AMD is the one manufacturing the faulty drivers, and Dell has probably no responsability in fixing the issue...

---

### Post by jinxy1919 on 2007-01-09
xo@xo-desktop:~$ sudo apt-get update
Err [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release.gpg
Could not resolve 'mirror3.ubuntulinux.nl'
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Ign [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas/freenx Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Err [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas/freenx Packages
Could not resolve 'mirror3.ubuntulinux.nl'
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Fetched 6B in 1s (5B/s)
Failed to fetch [http://mirror3.ubuntulinux.nl/dists/...as/Release.gpg](http://mirror3.ubuntulinux.nl/dists/...as/Release.gpg) Could not resolve 'mirror3.ubuntulinux.nl'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...kports/Release](http://us.archive.ubuntu.com/ubuntu/...kports/Release) Unable to find expected entry univ/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror3.ubuntulinux.nl/dists/...86/Packages.gz](http://mirror3.ubuntulinux.nl/dists/...86/Packages.gz) Could not resolve 'mirror3.ubuntulinux.nl'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
xo@xo-desktop:~$ sudo apt-get install module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
module-assistant is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xo@xo-desktop:~$ sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
dh-make is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
linux-headers-2.6.15-27-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xo@xo-desktop:~$ bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
bash: ati-driver-installer-8.29.6.run: No such file or directory
xo@xo-desktop:~$

Ok now everything works up untill bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper when i run that it says no such file or directory and i downloaded it to my desktop cab someone help?

---

### Post by Fitzy_oz on 2007-01-12
xo@xo-desktop:~$ bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper
bash: ati-driver-installer-8.29.6.run: No such file or directory
[COLOR="Red"]xo@xo-desktop:~$[/COLOR]

Ok now everything works up untill bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper when i run that it says no such file or directory and i downloaded it to my desktop cab someone help?[/QUOTE]

I'm pretty sure that ~ means that you in your home directory not your desktop, try cd Desktop immediately after you launch the terminal then try the command again...  (sudo ./ati*.run --buildpkg Ubuntu/edgy).

---

