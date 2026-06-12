---
title: "Ubuntu Hardy Heron installation adventures"
date: 2008-12-29
forum: General Help
---

### Post by michiel33 on 2008-12-29
In this post I will try to log my experiences, good and bad, with installing Ubuntu 8.04 and various applications and utilities. Issues that have not been resolved yet will be marked with :(. Help is greatly appreciated with these issues (current issues are: ms office under wine, scanner)
Hopefully, the following is helpful for some people.

2008-12-25	
Installed Ubuntu 8.04 on Windows laptop. 30 GB for Ubuntu
Tried to install Open Office 3.0 following [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml) this succeeded after changing the word "intrepid" to "hardy" because this procedure was written for Ubuntu 8.10 (Intrepid)

Switched off all visual effects, this made screen updating much better
Installed VLC media player and set it as default for FLV and MP3 files. See [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

2008-12-26
Installed wine: sudo apt-get install wine
Installed MS Office 2000 from CD, seemed ok, but when opening Word I get error: Change preferred owner in ~/.wine/system.reg
Editing this file does not help; it gets overwritten! Question posted on Ubuntu Forum: [http://ubuntuforums.org/showthread.php?t=957265](http://ubuntuforums.org/showthread.php?t=957265)
see also: [http://forums.mozillazine.org/viewtopic.php?f=37&t=708855&start=15\](http://forums.mozillazine.org/viewtopic.php?f=37&t=708855&start=15\)
see also: [https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office)
:( So far no solution!!

Installed open-in-terminal: sudo apt-get install nautilus-open-terminal. This adds a menu item to the right mouse button with which you open a terminal in the pointed to folder, very handy!

2008-12-27

Installed alien: sudo apt-get install alien
This converts. .tar.gz installation files to .deb format.

Installed Epson Perfection V200 scanner. See [http://push.cx/2007/epson-perfection-v100-in-ubuntu](http://push.cx/2007/epson-perfection-v100-in-ubuntu)

sudo apt-get install iscan-plugin-gt-f670_2.0.0-2_i386.deb did not work, but install via GUI worked.

Problem: sane-find-scanner finds scanner but scanimage -L does not find scanner

Edited /etc/sane.d/epson.conf
added:
# Epson VT200 scanner
usb 0x4b8 0x012e
This made Xsane seem to find the scanner
But now I get another error: 
"Error during CMS conversion: Could not open scanner ICM profile:"

[Ringi]("http://ubuntuforums.org/member.php?u=272212") says: "For me, if I uncheck "Preferences / Enable Color Management" this error goes away - and scanner works normally."

Indeed, the ICM message goes away but now if I click Scan, it says "failed to start scanner, invalid argument"
:( Not resolved yet!

Smooth fonts:
gedit ~/.fonts.conf
    <?xml version="1.0&#8243; ?>
    <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
    <fontconfig>
    <match target="font">
    <edit name="autohint" mode="assign">
    <bool>true</bool>
    </edit>
    </match>
    </fontconfig>

see: [http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/enable-smooth-fonts-on-ubuntu-linux/)

2008-12-29
Installed Acrobat Reader, see: [http://ubuntu-tutorials.com/2008/06/23/install-adobe-acrobat-reader-812-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/06/23/install-adobe-acrobat-reader-812-on-ubuntu-804/)
Set associations of pdf files to "acroread". This works well.

Installed MS Office 2007 fonts, see: [http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html](http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html)

Since a few days, I suffered from a strange phenomenon whereby after a few hours, all my USB drives suddenly are dismounted. They could not be brought back by e.g. disconnect/connect and were not visible in the Partition Editor.Then I realised that this coincided with the installation on my Panel of the Disk Mounter tool. So today I removed the Disk Mounter and the problem seems to be over!

---

