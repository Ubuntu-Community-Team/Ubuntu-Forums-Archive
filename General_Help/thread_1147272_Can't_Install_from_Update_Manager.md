---
title: "Can't Install from Update Manager"
date: 2009-05-03
forum: General Help
---

### Post by schwhop1 on 2009-05-03
Ubuntu 8.10 reports over 80 updates when I click on the red Update Icon; I click "Install Updates", enter my password,  a window appears that says "Reading Package Information", then the process stops and returns to the Update Manager without doing anything.  

I suspect that whatever this problem is, it also is preventing me from installing new apps, because I get the same failure to install from the Add/Remove process; nor can I install the Ubuntu 9+ upgrade, it cancels as well....

Any ideas?

Thanks,

---

### Post by spiderbatdad on 2009-05-03
please run in terminal and post any errors:```
sudo apt-get update
```
and
```
sudo update-manager
```

---

### Post by schwhop1 on 2009-05-03
No errors, as far as I can tell (I'm new to Ubuntu...).  Both times the linux prompt returned without a response:

omega@omega-desktop:~$ sudo apt-get update
[sudo] password for omega: 
omega@omega-desktop:~$ sudo update-manager
[sudo] password for omega: 
omega@omega-desktop:~$

---

### Post by MaxIBoy on 2009-05-03
Assuming you typed in your password, that's a little odd... almost as if you didn't have dpkg installed or something.


What is the output of this?
```
apropos dpkg
```What is the output of this?
```
apropos apt
```Finally, try running this:
```
sudo apt-get upgrade
```

---

### Post by schwhop1 on 2009-05-03
First command - dpkg:

omega@omega-desktop:~$ apropos dpkg
dpkg (1)             - package manager for Debian
dpkg-deb (1)         - Debian package archive (.deb) manipulation tool
dpkg-divert (8)- override a package's version of a file
dpkg-preconfigure (8) - let packages ask questions prior to their installation
dpkg-query (1)       - a tool to query the dpkg database
dpkg-reconfigure (8) - reconfigure an already installed package
dpkg-split (1)       - Debian package archive split/join tool
dpkg-statoverride (8) - override ownership and mode of files
dpkg-trigger (1)     - a package trigger utility
dpkg.cfg (5)         - dpkg configuration file
omega@omega-desktop:~$ 

Second command - apt: 

omega@omega-desktop:~$ apropos apt
/etc/laptop-mode/laptop-mode.conf (8) [laptop-mode.conf] - Configuration file...
/etc/laptop-mode/lm-profiler.conf (8)  [lm-profiler.conf] - Configuration file...
/usr/sbin/laptop_mode (8)  [laptop_mode] - apply laptop mode settings
apt (8)              - Advanced Package Tool
apt-cache (8)        - APT package handling utility - cache manipulator
apt-cdrom (8)        - APT CDROM management utility
apt-config (8)       - APT Configuration Query program
apt-extracttemplates (1) - Utility to extract DebConf config and templates fr...
apt-ftparchive (1)   - Utility to generate index files
apt-get (8)          - APT package handling utility - command-line interface
apt-key (8)          - APT key management utility
apt-mark (8)         - Utility to sort package index files
apt-secure (8)       - Archive authentication support for APT
apt-sortpkgs (1)     - Utility to sort package index files
apt.conf (5)         - Configuration file for APT
apt_preferences (5)  - Preference control file for APT
aptitude (8) - high-level interface to the package manager
aptitude-create-state-bundle (1) - bundle the current aptitude state
aptitude-run-state-bundle (1) - unpack an aptitude state bundle and invoke ap...
apturl (8)           - graphical apt-protocol interpreting package installer
captoinfo (1)        - convert a termcap description into a terminfo description
debconf-apt-progress (1) - install packages using debconf to display a progre...
gnome-screenshot (1) - capture screen or window and save the image to a file.
laptop-detect (8)    - attempt to detect a laptop
laptop-mode.conf (8) - Configuration file for laptop-mode-tools.
laptop_mode (8)      - apply laptop mode settings
lm-profiler (8)      - laptop mode profiler
lm-profiler.conf (8) - Configuration file for lm-profiler, a profiler for lap...
lm-syslog-setup (8)  - configure laptop mode tools to switch syslog.conf base...
pointer-capture-applet (1) - Creates an area on the panel to capture the pointer
radeontool (7)       - utility to control backlight on radeon based laptops
rapper (1)           - Raptor RDF parsing and serializing utility
sane-scsi (5)        - SCSI adapter tips for scanners
sg_test_rwbuf (8)    - Tests the SCSI host adapter by issuing write and read ...
sources.list (5)     - Package resource list for APT
synaptic (8)         - graphical management of software packages
synaptics (4)        - Synaptics touchpad input driver
synclient (1)        - commandline utitlity to query and modify Synaptics dri...
toshset (1)          - manipulate bios and hardware settings of Toshiba laptops
update-apt-xapian-index (8) - manual page for update-apt-xapian-index 0.15
xvinfo (1)           - Print out X-Video extension adaptor information
omega@omega-desktop:~$ 

Third - the PC hung for a second after the password prompt (my password is blank), then returned the linux prompt:

omega@omega-desktop:~$ sudo apt-get upgrade
[sudo] password for omega: 
omega@omega-desktop:~$

---

### Post by Pengwyn44 on 2009-05-06
I find the quickest way to solve this sort of problem is to back up the Home directory, the Email files and the browser Bookmarks and then reload Ubuntu completely.
If you can afford an external hard drive, clone the hard drive to the external drive when your system is working as you want it to. Then you can get it back quickly if things go wrong.

---

