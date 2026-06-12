---
title: "Cannot fix Update Manager"
date: 2008-09-24
forum: Desktop Environments
---

### Post by smccarthy945 on 2008-09-24
I get the following error when trying to run Update Manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then run 'dpkg --configure -a' and get a segmentation fault. See below. Any help is appreciated: 

root@server01:~# dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-19-generic (2.6.24-19.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up tzdata (2008e-1ubuntu0.8.04) ...
Segmentation fault
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (3.0.28a-1ubuntu4.5) ...
Segmentation fault
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.5); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 3.0.28a-1ubuntu4.5); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
root@server01:~#

---

### Post by frankleeee on 2008-09-24
in the terminal paste sudo dpkg --configure -a  this should take care of it. I see it says root run this in the regular terminal sudo gives you root access for this command and others.

---

### Post by smccarthy945 on 2008-09-24
Tried that and got the same result..

---

### Post by smccarthy945 on 2008-09-24
Actually, the error at the end was a little different. See below:

root@server01:~# sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-19-generic (2.6.24-19.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up tzdata (2008e-1ubuntu0.8.04) ...
Segmentation fault
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (3.0.28a-1ubuntu4.5) ...
Segmentation fault
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.5); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 3.0.28a-1ubuntu4.5); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Trace/breakpoint trap
Illegal instruction
Segmentation fault
Segmentation fault
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
root@server01:~#

---

### Post by frankleeee on 2008-09-24
I think your using the wrong terminal use the one in accessories it looks like your using the root terminal. Using the rot terminal is not advisable unless you realy know what your doing and not applicable to the command your running.

---

### Post by smccarthy945 on 2008-09-24
I logged in with my regular account, tried the accessories terminal and got the same result. I was logged in with the root account before.

---

### Post by frankleeee on 2008-09-24
I am not sure that like the sudo usage if using the root terminal times out or you have to shut down the root access, hopefully somebody else will confirm your needs. If it was me I would just do a restart to make sure I started fresh with the correct terminal.

---

### Post by smccarthy945 on 2008-09-25
Ok so I reboot and login with my regular account and click on accessories - terminal and get the error "There was an error creating the child process for this terminal". I can SSH in but I can't run the terminal from Gnome.

---

### Post by frankleeee on 2008-09-25
I have never figured out that ssh stuff, so I can't help there, in relation to your problem. What I can't figure out is it seems your trying to update through another computer rather than just using the one needing updates with a straight internet connection, is this correct?

---

### Post by smccarthy945 on 2008-09-25
Frank, I have tried this every way possible. I have been doing most of this in Gnome on the local machine. I tried SSH for the hell of it as a last resort.

---

### Post by frankleeee on 2008-09-25
> **smccarthy945 said:**
> Frank, I have tried this every way possible. I have been doing most of this in Gnome on the local machine. I tried SSH for the hell of it as a last resort.

I'm sorry I can't be more helpful, but hopefully a real geek will see the thread and help you, I am just a pseudo geek. Having a child process problem with the terminal is not anything I have ever encountered.

---

### Post by AnRkey on 2008-09-25
First get the latest package lists
sudo apt-get update

Remove any corrupt packages from your local apt cache
sudo apt-get clean

Then check that all dependancies are met with this
sudo apt-get check

if this returned dependancy problems then run
sudo apt-get install -f

Then run this to do all your updates
sudo apt-get upgrade

You should be good to go now, let us know if this worked.

R

---

### Post by smccarthy945 on 2008-09-25
Sorry.. I get the following errors:


smccarthy@server01:~$ sudo apt-get check
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

smccarthy@server01:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

???

---

### Post by smccarthy945 on 2008-09-25
I guess I am reinstalling. Anyone have any suggestions?

---

### Post by frankleeee on 2008-09-25
If you run sudo apt-get autoremove then sudo apt-get autoclean this should clean the corrupted files then run the dpkg-a then the -f commands as listed in the previous posts then sudo apt-get update 
then sudo apt-get upgrade.

---

### Post by smccarthy945 on 2008-09-25
See below:


smccarthy@server01:~$ sudo apt-get autoremove
[sudo] password for smccarthy:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
smccarthy@server01:~$ sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
smccarthy@server01:~$

---

### Post by AnRkey on 2008-09-26
Try fix it before you reinstall, you will only end up with valuable experience.

Try this out > [http://ubuntuforums.org/showthread.php?t=527193&page=2](http://ubuntuforums.org/showthread.php?t=527193&page=2)

Read through that thread, I think the last post might help.

Let us know,

R

---

### Post by smccarthy945 on 2008-09-26
Man, I am ready to throw this box across the room!!!! I still get the dpkg error after I went through all that. When I run the cp command, I get a segmentation fault. 

When I run any basic command, I get a segmentation fault - ping, cp, etc. I had to copy the file through Gnome to complete the copy command but still no luck...

I really need to fix this as I have alot on the box that I would have to move if I have to reinstall. Pleeeeasseee help!

---

### Post by smccarthy945 on 2008-09-26
Ok, I am able to run the apt-get commands now after I removed files from the dpkg directories. So, I think I am making progress.. However, I still cannot run the last upgrade command but this might be a clue. I get a bunch of missing file errors. See the last error.

dpkg: serious warning: files list file for package `pidgin-otr' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-nv' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libsm6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `tracker' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `w3m' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `klogd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dhcp3-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglib2.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpt-1.10.10-plugins-v4l' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `onboard' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnomevfs2-bin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `language-selector-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `wvdial' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `php5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `foomatic-db' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compizconfig-backend-gconf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-plugins-good' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpng12-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libparted1.7-1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-via' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libconsole' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpt-1.10.10' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-sharpzip2.84-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apt-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-geode' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-about' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `evolution-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `udev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapm1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `defoma' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-writer' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpixman-1-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxklavier12' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-security1.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-sharpzip0.84-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-gnome' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `firefox-3.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iptables' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxml-twig-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libqthreads-12' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-headers-2.6.24-16-generic' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `bash' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `make' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `util-linux' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ekiga' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libkrb53' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `bind9' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxcursor1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfonts-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-input-kbd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `update-manager' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmeanwhile1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnome-mag2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmusicbrainz4c2a' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `powernowd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `avahi-daemon' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `reiserfsprogs' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libneon27' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-uno' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-x' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ubuntu-minimal' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `popularity-contest' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apparmor' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hplip' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libfontenc1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libisccfg30' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglew1.5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libopencdk10' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `cpio' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `powermgmt-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `network-manager-gnome' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xsane' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libstdc++6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono1.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `scim' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `x11-xfs-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-i740' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `zip' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `nautilus-sendto' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `apport' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libscrollkeeper0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-system2.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iputils-arping' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libhtml-tagset-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `pulseaudio' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `desktop-effects-kde' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ca-certificates' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `update-notifier-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `strace' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gvfs-fuse' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `vim-tiny' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcdio7' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `usplash-theme-ubuntu' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-server' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fortunes-min' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-ati' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblwres30' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgmyth0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-siliconmotion' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `binutils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `cdparanoia' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-corlib2.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `foomatic-db-hpijs' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `php5-mysql' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-alsa' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gimp-gnomevfs' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-gconf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-corlib1.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-tools' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgmime-2.0-2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `less' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mysql-client-5.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgphoto2-port0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglib2.0-0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libnet-dbus-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgomp1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `wodim' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmono-sqlite2.0-cil' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-video-tseng' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libtext-charwidth-perl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxt6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `readline-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-sound-base' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ttf-opensymbol' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcap1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwpd8c2a' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libapr1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `software-properties-gtk' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `usplash' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libcupsimage2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnutls13' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `o3read' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnome-media0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `netcat' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lsof' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblaunchpad-integration1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblaunchpad-integration0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-power-manager' missing, assuming package has no files currently installed.
363 files and directories currently installed.)
Preparing to replace libc6-i686 2.7-10ubuntu3 (using .../libc6-i686_2.7-10ubuntu4_i386.deb) ...
Unpacking replacement libc6-i686 ...
Preparing to replace xulrunner-1.9-gnome-support 1.9.0.2+build6+nobinonly-0ubuntu0.8.04.1 (using .../xulrunner-1.9-gnome-support_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement xulrunner-1.9-gnome-support ...
Preparing to replace xulrunner-1.9 1.9.0.2+build6+nobinonly-0ubuntu0.8.04.1 (using .../xulrunner-1.9_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement xulrunner-1.9 ...
Preparing to replace firefox-3.0-gnome-support 3.0.2+build6+nobinonly-0ubuntu0.8.04.1 (using .../firefox-3.0-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement firefox-3.0-gnome-support ...
Preparing to replace firefox-3.0 3.0.2+build6+nobinonly-0ubuntu0.8.04.1 (using .../firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement firefox-3.0 ...
Preparing to replace firefox 3.0.2+build6+nobinonly-0ubuntu0.8.04.1 (using .../firefox_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_all.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 3.0.2+build6+nobinonly-0ubuntu0.8.04.1 (using .../firefox-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1_all.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace gdb 6.8-1ubuntu2 (using .../gdb_6.8-1ubuntu3_i386.deb) ...
Unpacking replacement gdb ...
Preparing to replace python-gtkhtml2 2.19.1-0ubuntu7 (using .../python-gtkhtml2_2.19.1-0ubuntu7.1_i386.deb) ...
Unpacking replacement python-gtkhtml2 ...
Setting up libc6-i686 (2.7-10ubuntu4) ...

Setting up xulrunner-1.9 (1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1) ...

Setting up xulrunner-1.9-gnome-support (1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1) ...

Setting up firefox-3.0 (3.0.3+build1+nobinonly-0ubuntu0.8.04.1) ...
Please restart all running instances of Firefox-3.0, or you will experience problems.
Segmentation fault
dpkg: error processing firefox-3.0 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.3+build1+nobinonly-0ubuntu0.8.04.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up gdb (6.8-1ubuntu3) ...

Setting up python-gtkhtml2 (2.19.1-0ubuntu7.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 firefox-3.0
 firefox-3.0-gnome-support
 firefox
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server01:~#

---

### Post by AnRkey on 2008-09-26
Segfaults on top of all of this means only one thing to me, ram issues. Restart your box and do a full ram test with the Ubuntu 8.04 CD. Check that and let us know.

Here is some more info on what segfaults are >> [http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

Later,

R

PS: Hang in there, when it's sorted you will be running an awesome OS

---

### Post by smccarthy945 on 2008-09-26
Thanks for the suggestion. I will run the RAM test tonight. 

You don't have to sell me on Ubuntu - I love it. The only frustrating part is that these type of problems are sometimes hard to solve. 

It is an older box so it wouldn't surprise me if it was a RAM issue. I will let you know.

---

### Post by smccarthy945 on 2008-09-26
Ok, I ran the memory tests from the CD and everything passes. I think this has to do with the base packages being corrupted.

This happened after a power failure so I think something is corrupt. What now?

---

### Post by smccarthy945 on 2008-09-26
Ok, I am not sure what I did but I got the dpkg fix working. So I can now run updates and add and remove packages so thanks for the help!!

I am still getting a segmentation fault in gnome so I was thinking I could remove gnome and reinstall to clean it up. I have a feeling it has something to do with gnome. 

Is there any way I can load without gnome and try ping and see if its related to gnome.

---

### Post by smccarthy945 on 2008-09-26
Well I am happy to report my installation is fixed!!!!

I uninstalled and reinstalled iptools-ping and some other tools and its all working now. Thank you so much for all the help!!!!

---

### Post by AnRkey on 2008-10-01
Thats good news!

Sorry I could not reply for so long, I have been running around a bit these past few days.

Ciao,

R 8-)

---

