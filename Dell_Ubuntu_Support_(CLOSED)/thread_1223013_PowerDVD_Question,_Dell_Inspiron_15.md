---
title: "PowerDVD Question, Dell Inspiron 15"
date: 2009-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jlacroix on 2009-07-25
I got my Dell Inspiron today with Ubuntu preinstalled, but I prefer Kubuntu so I opted for that instead, and installed it on my own. With my Dell came a CD with PowerDVD on it. I probably don't need that and can live without it but I want to check it out anyway. So I inserted the CD and then navigated to /media/cdrom0/pdvd and ran "sudo dpkg -i *.deb" and this is what happens:

```
jeremy@jeremy-desktop:/media/cdrom0/pdvd$ clear                       
jeremy@jeremy-desktop:/media/cdrom0/pdvd$ sudo dpkg -i *.deb
dpkg: error processing libsdl_g.deb (--install):            
 package architecture (i386) does not match system (amd64)  
dpkg: error processing libsdl_t.deb (--install):            
 package architecture (i386) does not match system (amd64)  
(Reading database ...
dpkg: serious warning: files list file for package `pdvdlinux' missing, assuming package has no files currently installed.
167398 files and directories currently installed.)
Preparing to replace pdvdlinux 4.52 (using pcm1118_.deb) ...
Check BIOS information ....
Vendor: Award Software International, Inc.
It is not a Dell System, exit installation
dpkg: error processing pcm1118_.deb (--install):
 subprocess pre-installation script returned error exit status 1
No value set for `/desktop/gnome/powerdvd/autoplay_dvd'
No value to set for key: `/desktop/gnome/volume_manager/autoplay_dvd'
No value set for `/desktop/gnome/powerdvd/autoplay_dvd_command'
rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/tmp.ci/postrm: 27: update-app-install: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 libsdl_g.deb
 libsdl_t.deb
 pcm1118_.deb

```

Is this saying that I have to use Gnome in order to use PowerDVD? Also, for some reason I cannot remove PowerDVD either, and every time I update now it complains about it needing to be reinstalled. :(

Maybe someone can help me out?

Edit: I just now noticed that it's complaining that I use 64-bit. True, I have 4GB of RAM and I don't have a PAE kernel so I run 64-bit and prefer it. Is there a way around that?

---

### Post by gwilson on 2009-09-08
I have the same system and installed Linux Mint 7.  Whenever you use synaptic to install a package, I get an error code saying PowerDVD was not installed properly (although the program runs just fine). Now, I can't uninstall the program or find it anywhere on the computer.

---

### Post by Bucky Ball on 2009-09-08
PowerDVD is for Windows as far as I know. Totally useless in Linux (except using Wine) if this is the case. Look for an Open Source alternative.

---

### Post by gwilson on 2009-09-08
Nope!  There's a Linux version that comes installed under Ubuntu on Dell PCs.  It's also featured on their website.

---

### Post by Bucky Ball on 2009-09-08
I sit comfortably corrected. ;-)

---

### Post by themrfreeze on 2009-09-08
The Dell PowerDVD software is incompatible with 9.04.  Those of us who own Inspiron 15n laptops (with Ubuntu 8.04 preinstalled) found that out when we upgraded.  Check out the "Inspiron 15n" thread for more info.

---

