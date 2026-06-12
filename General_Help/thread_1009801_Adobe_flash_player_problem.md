---
title: "Adobe flash player problem"
date: 2008-12-13
forum: General Help
---

### Post by charanpreethu on 2008-12-13
I am using ubuntu 8.04. I installed adobe flash player from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/). I downloaded tar.gz and installed by following the instructions.
Its not working in mozilla.Whenever I open youtube it is asking me to download the player again...

---

### Post by sparky-steve on 2008-12-13
In synaptic, search & install flashplugin-nonfree or from command,

sudo apt-get install flashplugin-nonfree

Restart firefox and away you go.

HTH

---

### Post by iaculallad on 2008-12-13
In addition to:

```
sudo apt-get install flashplugin-nonfree
```

try also installing the libflashsupport, the audio support wrapper for non-free flash plugin:

```
sudo apt-get install libflashsupport
```

---

### Post by charanpreethu on 2008-12-14
i tried this
sudo apt-get install flashplugin-nonfree

i got the msg sayin

sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 191 not upgraded.


Still its not working

---

### Post by aysiu on 2008-12-14
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and post the output back here? ```
sudo updatedb
locate flash
cat /etc/lsb-release
uname -m
dpkg -s flashplugin-nonfree
dpkg -s swfdec-mozilla
dpkg -s mozilla-plugin-gnash
``` That first command may take a few minutes to execute. Be patient.

---

### Post by charanpreethu on 2008-12-14
locate flash
/home/charan/.mozilla/plugins/libflashplayer.so
/home/charan/Desktop/install_flash_player_10_linux
/home/charan/Desktop/install_flash_player_10_linux/flashplayer-installer
/home/charan/Desktop/install_flash_player_10_linux/libflashplayer.so
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/usr/bin/btcflash
/usr/lib/flashplugin-nonfree
/usr/lib/openoffice/program/libflash680li.so
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-nonfree.desktop
/usr/share/app-install/icons/flashblock.xpm
/usr/share/doc/flashplugin-nonfree
/usr/share/doc/flashplugin-nonfree/changelog.gz
/usr/share/doc/flashplugin-nonfree/copyright
/usr/share/icons/HighContrastLargePrintInverse/48x48/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/Human/16x16/devices/media-flash.png
/usr/share/icons/Human/22x22/devices/media-flash-cf.png
/usr/share/icons/Human/22x22/devices/media-flash.png
/usr/share/icons/Human/24x24/devices/media-flash-cf.png
/usr/share/icons/Human/24x24/devices/media-flash-ms.png
/usr/share/icons/Human/24x24/devices/media-flash.png
/usr/share/icons/Human/48x48/devices/media-flash-cf.png
/usr/share/icons/Human/48x48/devices/media-flash-ms.png
/usr/share/icons/Human/48x48/devices/media-flash.png
/usr/share/icons/Human/scalable/devices/media-flash-cf.svg
/usr/share/icons/Human/scalable/devices/media-flash-ms.svg
/usr/share/icons/Human/scalable/devices/media-flash.svg
/usr/share/icons/gnome/16x16/devices/media-flash.png
/usr/share/icons/gnome/16x16/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/22x22/devices/media-flash.png
/usr/share/icons/gnome/22x22/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/24x24/devices/media-flash.png
/usr/share/icons/gnome/24x24/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/32x32/devices/media-flash.png
/usr/share/icons/gnome/32x32/mimetypes/gnome-mime-application-x-shockwave-flash.png
/usr/share/icons/gnome/scalable/devices/media-flash.svg
/usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-x-shockwave-flash.svg
/usr/share/lintian/overrides/flashplugin-nonfree
/usr/share/man/man8/btcflash.8.gz
/usr/share/mime/application/x-flash-video.xml
/usr/share/mime/application/x-shockwave-flash.xml
/usr/src/linux-headers-2.6.24-19/include/asm-arm/nwflash.h
/usr/src/linux-headers-2.6.24-19/include/asm-arm/mach/flash.h
/usr/src/linux-headers-2.6.24-19/include/asm-cris/axisflashmap.h
/usr/src/linux-headers-2.6.24-19/include/asm-mips/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.24-19/include/asm-sparc/jsflash.h
/usr/src/linux-headers-2.6.24-19/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.24-19/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/scb2/flash.h
/usr/src/linux-headers-2.6.24-19-generic/include/config/mtd/scx200/docflash.h
/var/cache/flashplugin-nonfree
/var/cache/apt/archives/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb
/var/cache/flashplugin-nonfree/wgetrc
/var/lib/flashplugin-nonfree
/var/lib/dpkg/info/flashplugin-nonfree.config
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/dpkg/info/flashplugin-nonfree.md5sums
/var/lib/dpkg/info/flashplugin-nonfree.postinst
/var/lib/dpkg/info/flashplugin-nonfree.postrm
/var/lib/dpkg/info/flashplugin-nonfree.prerm
/var/lib/dpkg/info/flashplugin-nonfree.templates


cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

 uname -m
i686

dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.124.0ubuntu2
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>




dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.




dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by aysiu on 2008-12-14
Hm. That's odd. Looks good to me. Maybe remove the /home/charan/.mozilla/plugins/libflashplayer.so and then reinstall the Flash plugin? ```
rm /home/charan/.mozilla/plugins/libflashplayer.so
sudo apt-get install --reinstall flashplugin-nonfree
``` and then restart Firefox?

---

### Post by charanpreethu on 2008-12-14
I am getting this error

HTTP request sent, awaiting response... 404 Not Found
12:10:11 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

---

### Post by aysiu on 2008-12-14
What happens if you go to the Adobe website and instead of selecting the .tar.gz you select the .deb for Ubuntu 8.04?

---

### Post by lordbux on 2008-12-14
hai dude
k ...this is where you have gone wrong .......
no worries .....its simple.

the tar.gz file is only for linux versions below 8 

for the  8.x version of ubuntu u need to download the deb version from here

[http://get.adobe.com/flashplayer/otherversions/](http://get.adobe.com/flashplayer/otherversions/)

**step one: go to the abow link : select operating system as [B]LINUX **from drop down list.

step two: a new drop down will appear : [I]select .deb For ubuntu 8.4+
 [/I] 
step three: click install.

step four: once downloaded double click and activate the package and click install package.[/B]


hope i was right:guitar:

long live open source :lolflag:

pls reply if there is some problem

---------
lordbux 
[email]blaise.crowly@gmail.com[/email]

---

### Post by charanpreethu on 2008-12-14
ya I downloaded n installed .deb ubuntu 8.04


same result its not working  :(

---

### Post by wesmsl on 2008-12-14
Is there anyway to get flash working in 8.04?  Because I'm having the same problem.  I'm seriously considering downgrading because I liked earlier versions of ubuntu much better.  Any thoughts?

---

### Post by 3rdalbum on 2008-12-14
Adobe Flash Player's installer program is undoubtedly the worst, most useless program ever seen on Linux. Don't use it.

Ubuntu's "flashplugin-nonfree" package doesn't contain the plugin, it actually just installs Flash Player from the Adobe website using an unsophisticated script. If the Adobe web server responds in an unexpected way, the script may believe that Flash Player has installed, but it actually hasn't. The script tells the package manager that the installation has occurred successfully too.

From the file listing given earlier in the thread, it doesn't look like the Flash Player has been installed. It should be in /usr/lib/mozilla/plugins. My advice is to go back into Synaptic Package Manager and mark flashplugin-nonfree TO BE REINSTALLED and see what happens. Post any error messages that occur.

---

### Post by charanpreethu on 2008-12-14
I tried reinstalling flash-nonfree.I am getting this error

404 error not found
downloadin failed


Is there anyother way to get flash player workin???

---

### Post by Hairyharry on 2008-12-14
Try [http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz](http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz)

Worked for me

---

### Post by charanpreethu on 2008-12-15
How to install that????

Is ther any one who can solve my problem????

---

### Post by lordbux on 2008-12-15
> **charanpreethu said:**
> How to install that????

Is ther any one who can solve my problem????


extract content

go to extracted folder location
and run 
IF IT IS A .SH FILE
```
sudo sh filename.sh
```
=========
IF IT IS A .BIN FILE
```
sudo chmod +x filename.bin
sudo ./filename.bin
```:popcorn:


hopping to hear good news
long live open source:guitar:

---

### Post by 3rdalbum on 2008-12-15
> **Hairyharry said:**
> Try [http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz](http://home.comcast.net/~ubuntume/getflash10-.10.tar.gz)

Worked for me

Not appropriate for x86.

The other option is what I suggested before - extract the .tar.gz archive from Adobe.com, find the "libflashplayer.so" file inside and put it into /usr/lib/mozilla/plugins/. You need to open a root file browser in order to copy to this location.

I'm puzzled as to why the flashplugin-nonfree script tells you that the file wasn't found. Is your internet connection running okay on Ubuntu?

---

### Post by dkw on 2008-12-15
It's not a user issue -- its an adobe issue.

The package that comes down from the repository is fine, it's just an installer, it tries to wget the file: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Which is where the 404 error is coming from, not ubuntu's fault, not the users fault, adobe's fault. :)

- Dan.

---

### Post by aDarkling on 2009-01-09
It's not a user or an adobe issue -- its a Repository issue.  The flashplugin-nonfree 10.0.1.218 is broken.  It keeps trying to download Flash 9 from Adobe, but Adobe has moved on to version 10.  When the "404 - File not Found" error comes back, Synaptic thinks that it's installed sucessfully. 

If you want to save yourself 5 hours of wasted time, do this:

[LIST=1]
[*]Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
[*]Download the .deb file for Ubuntu 8.04+.  Save it to the Desktop.
[*]Shut down Firefox
[*]Start up Synaptic Package Manager, mark flashplugin-nonfree for **complete removal**, and then Apply.
[*]Restart Ubuntu
[*]Double-click on "install_flash_player_10_linux.deb".  It will open a "Package Installer" window. 
[*]Click "Install Package".
[*]Restart Ubuntu.
[*]Start Firefox
[/LIST]

That did the job for me.  Some of the stuff like restarting the system is probably unnecessary, but I come from WinWorld where _not_ rebooting every 2 steps will usually mess up your install.

I did this on a single-account install.  you might need to pull up a Terminal window & do some sort of "gksudo gdebi-gtk" if you have a multiple-account system.

It'd be great if someone can contact a DevTeam member and explain why it's important to make sure that a highly visible, completely necessary & not understood program like flashplugin-nonfree needs to be checked if people are having problems with it for months on end.  I can't do it -- I'm new here, taking care of 2 crying babies & just lost 5 hours that I'm never gonna get back.  I'm afraid that I might not be civil, and they don't deserve that.

](*,)

---

