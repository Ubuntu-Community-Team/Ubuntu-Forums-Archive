---
title: "Migrating from MS Windows to Ubuntu (detailed)"
date: 2006-05-19
forum: Desktop Environments
---

### Post by vinfred on 2006-05-19
This document describes how I installed my Ubuntu (Breezy) system using GNOME. in a Microsoft Windows environment.

Goals
====
Basic intallation (needs building a driver (RT61) for a PCMCIA wireless card using WEP)
Use of a Microsoft Windows 2003 server as a DHCP server
Access shares in the Windows environment (without being integrated into the Windows Domain)
Synchronize time with a local ntp server
Create X sessions (Gnome) from a Microsoft Windows NT Workstation (using cygwin and xdmcp)

As being completely newbie to linux, I looked at many notes, documentations to produce that document.
I'm conscious that the same goals can be achieved using differents methods.
Some of the methods I used are probably not using the supported Ubuntu/Debian way. But ... it works !...

As I'm working on an Ubuntu French version, some of the menus or titles may differ slightly from what you see. Forgive also my poor English.

Introduction
============
You should be able to use a web browser, and read documentation written in English.
You must understand basic terminology and concepts for TCPIP networking and computing in general.
You must be prepared to find many documents, notes, Forum postings describing how to achieve a particular task. Some are very good, other are incomplete, obsoletes or do not match the Ubuntu environment. Even the present document is most probably incomplete
Generally, you will have to collect several documents to find exactly how to proceed (You've been warned).
Remember also that Ubuntu is Debian based, and, if you don't find what you're looking for, search for more information into Debian sites and pages.

Some pointers:
==============
[http://www.ubuntu.com/](http://www.ubuntu.com/)
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)
[http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)
[http://www.us.debian.org/doc/manuals/reference/reference.en.html](http://www.us.debian.org/doc/manuals/reference/reference.en.html)
[http://us5.samba.org/samba/](http://us5.samba.org/samba/)


Environment
===========
This is the environment I used to write this procedure. You may proceed in a different environment, but, in this case, this document will provide only part of what you have to do.

You need to have access to a machine where you can download an iso image and burn it.
The target PC must have a CD reader and be able to boot from it.
The target PC must have a network connection to internet. If your plan to use a wireless connection, it would be advisable to have temporarily a wired connection (at least to save time and headackes)
You should know the IP address of your DNS server(s)
If using a fixed IP address, you must know what address you will use, your network mask and your gateway address. (ensure this address is not used by another machine)

Preliminary work
=============
Do a web search for ubuntu and mark the home page in your web browser
Get the install CD (Breezy Badger) iso image and burn it
I recommend also to get the live CD and burn it

Work now on the target machine
=========================
Boot the live CD
This will help you in verifying your basic hadware is recognized (CPU, mouse, keyboard, disk, network interface) and can be used and let you figure out what might cause nightmares to get it working. Try different commands and applications, verify network connectivity.

Boot the install CD and answer the basic questions asked (you need there a basic understanding on disks as well as networking: Don't be afraid! these are really basic)

Start first customizations
===================
Boost your web browser performances (Firefox)
---------------------------------------------------------------
This step is not absolutely required. But it will help in achieving your task quickier.
Applications->Internet->Firefox Web Browser 
In the Navigation toolbar URL field enter about:config . 
Use the Filter field to change the following parameters: 
network.dns.disableIPv6 - Set the Value parameter to true. 
network.http.pipelining - Set the Value parameter to true. 
network.http.pipelining.maxrequests - Set the Value parameter to 8. 
network.http.proxy.pipelining - Set the Value parameter to true. 
Restart Mozilla Firefox

Define your connectivity options :D 
--------------------------------------------
If you're connected behind a proxy, you'll need to specify it for Firefox, Synaptic and apt

Firefox: Tools -> options - general tab - network (same as Window Internet Explorer)
Synaptic: categories -> preference - network tab 
(enter as username:Password@proxy.com if the proxy is password protected, proxy.com if not. Specify the port)
apt: sudo gedit /etc/apt/apt.conf
include the following (again, if the proxy is not password protected use proxy.com:Port syntax)
----------------------------------
ACQUIRE {
   retries "3";
   http {
      proxy "http://username:Password@proxy.com:Port/";
   }
};
----------------------------------
exemples 
"http://JohnDoe:Secret@myproxy.com:8080/"
or
"http://myproxy.com:8080/"

Select the required depots (Universe, Multiverse ...)
=======================================
Synaptic: Categories - Depots. Click on "Parameters" "User interface" select "view sources of deactivated SW"
Select all binaries and sources (Officially Supported)
Select all binaries Universe Multiverse
Deselect the CD (unless you want to keep the CD in the drive)

(the sources may be useful if you need to build/rebuild a kernel, a kernel module or a driver)

You may get other depots (especially PLF, multimedia packages, wine ...) 
by connecting to [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
then either in entering the depots with synaptic or copying the resultant file to /etc/apt/sources.list after saving a copy of the original file
cd /etc/apt
sudo cp sources.list sources.list.save
sudo cp your_source_list sources.list

Now protect your system using a Firewall (Universe)
========================================
# Synaptic: search for firestarter and install it
# Modify your firewall as needed: 
sudo firestarter
# make the necessary changes and exit firestarter
# (if authorizing a network, use the following syntax:  network_address/mask
# Ex: 192.168.0.0/16 where 16 is the number of bits of the network mask)
# Generate the appropriate scripts to get it started at boot time with your parameters.
sudo firestarter --generate-scripts
# see documentation at [http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

Now update all your installed packets
=============================
System - administration - update manager: select all updates
Apply changes
As you'll get a new kernel, reboot your system after all updates have been applied.

===========================================================
Your system is now (hope)fully operational with a wired network connection
===========================================================
A few tricks
============
Reinstall the latest version of Firefox:
-------------------------------------------------
See intallation instructions at [https://wiki.ubuntu.com/FirefoxNewVersion?action=show&redirect=FireFox](https://wiki.ubuntu.com/FirefoxNewVersion?action=show&redirect=FireFox)
You might also want to add firefox extensions and a download manager .
Within Firefox: tools - Extensions -get other extensions
Look at the top 10 and install whatever you need. I recommend Fasterfox, Flashgot, NoScript, Adblock
Install a download manager. I use GNOME Gwget: sudo apt-get install gwget # (Universe)

Automatix
---------------
You may want to install Automatix (Breezy only) see features at [http://doc.gwos.org/index.php/Automatix](http://doc.gwos.org/index.php/Automatix)

Restarting GNOME without rebooting
---------------------------------------------------
# save and close all open applications
# use Ctrl-Alt-Backspace shortcut keys to restart GNOME
#  or
   sudo /etc/init.d/gdm restart

Boost your CD
--------------------
sudo hdparm -d1 /dev/cdrom
sudo cp /etc/hdparm.conf /etc/hdparm.conf.sav
sudo gedit /etc/hdparm.conf
#append the following lines to  /etc/hdparm.conf
/dev/cdrom {
       dma = on
}

Automatically turn on Num-Lock when GNOME starts (Multiverse)
-----------------------------------------------------------------------------------------
sudo apt-get install numlockx
cd /etc/X11/gdm/Init
sudo cp Default Default_backup
sudo gedit Default
# find the line (it should be the last one)
# exit 0
# add the following lines above the "exit 0" line

if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi

# save and exit
The change will take effect the next time you log in to GNOME.

Switch to console mode
--------------------------------
Ctrl-Alt-F1 to Ctrl-Alt-F6 to access one of the 6 available consoles
Ctrl-Alt-F7 to return to Desktop mode

Install/Uninstall a ".deb" file
-------------------------------------
sudo dpkg -i package_file.deb #install package
sudo dpkg -r package_name #uninstall package

Convert an .rpm file to .deb file
-----------------------------------------
sudo alien package_file.rpm

Run Xman (X Manpages)
----------------------------------
MANPATH=$('manpath');export MANPATH
xman

# create a small script with the 2 lines above, change it's permission (chmod +x your_script_file)
# Use Applications - System tools - Application menu editor to add this script to a menu

Install Debian menus (Universe)
------------------------------------------
sudo apt-get menu-xdg
sudo update-menus

HERE START THE TROUBLE (Wireless Networking) :twisted: 
=========================================
Some wireless cards are supported natively by Ubuntu 5.10 (Breezy) and work out of the box.
Some (should I say most) wireless cards can be installed using ndiswrapper see [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)
(ndiswrapper lets you install a Microsoft Windows Network Driver on linux)
Some wireless cards can be installed by (re)building a driver (generally in beta version, either available from sourceforge or the card manufacturer or the chipset manufacturer or ...

To make the things really simple (!!!), cards manufacturer use different chipsets depending on the revision level of the card. (example: D-LINK DWL-G630 rev C doesn't use the same chipset as revision E1)
Some chipsets are supported other are not! Not all manufacturers provide a linux driver for their card, nor provide full specifications for the linux community.

Finally, when you buy a card, the revision level is never mentionned onto the box. You discover that your card revision level is not documented when you open the box, or when plugging the card in.

For all these reasons, don't spend too much time in trying to find which wireless card you should buy. Choose a manufacturer whose most cards are supported, select a card which is known to work and pray to get a supported revision level/chipset.

A very good starting point to choose your card would be
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
and, for the cards that are supported thru ndiswrapper
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Remember also that once you've obtained network connectivity using your wireless card, you should be careful on the way to make it work at boot time. Especially, PCMCIA cards, should be started with hotplug mapping, because the card manager is started after the network interfaces during the boot sequence. 
For this reason, you cannot use wireless-tools GUI with PCMCIA wireless cards (it adds "auto xx0" to the /etc/network/interfaces).
In case of doubt, You really should read the documentation about network configuration available at 
[http://www.us.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.us.debian.org/doc/manuals/reference/ch-gateway.en.html)

Identify your card
==============
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)
explains how to identify your card and much more...
Have a look at [http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)
Should you need to use ndiswrapper, have a look at [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

Should you need to (re)build a network driver here is an example:

Get the required packages to (re)build a kernel or a kernel module
=================================================
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
sudo apt-get install linux-tree

sudo apt-get install sysutils
(sysutils is providing dos2unix utility which is required to parametrize a Ralink RT61 driver)
linux-tree is required only if you need to (re)build a kernel or module. It's not required to rebuild ndiswrapper.


Building the RT61 driver
===================
The steps for building another driver would be approximately the same

# cd to your home directory
mkdir RT61
cd ./RT61
# download the RT61 for linux driver from [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)
# extract the files
tar -zxvf  RT61_Linux_STA_Drv1.0.3.0.tar.gz
cd ./RT61_Linux_STA_Drv1.0.3.0_200512230/Module
# have a look at the readme (the following is mainly extracted from there)
cp Makefile.6 ./Makefile
make all
sudo mkdir /etc/Wireless/RT61STA/
sudo cp rt2561.bin /etc/Wireless/RT61STA/
sudo cp rt2561s.bin /etc/Wireless/RT61STA/
sudo cp rt2661.bin /etc/Wireless/RT61STA/
# edit the rt61sta.dat according to the documentation provided into the readme
# Specify your SSID (SSID=) Your network type (NetworkType=Infra) your channel, 
# Authorization (Authmode=WEPAUTO) your encryption  (EncrypType=WEP) and your 
# WEP key (Key1Str=xxxxxxxxxxxxx)
# don't modify other configuration items if you don't understand what they act upon
sudo gedit rt61sta.dat
#convert the file to binary format
fromdos -f  rt61sta.dat
sudo cp rt61sta.dat /etc/Wireless/RT61STA/rt61sta.dat
# disconnect the ethernet wire and plug the card in (if PCMCIA)
# (avoid potential conflicts in getting the ethernet wire plus the wireless card
# on the same network)
# copy the module into your kernel modules tree (create the directory if it doesn't exist)
sudo mkdir /lib/modules/'uname -r'/kernel/drivers/net/wireless
sudo cp rt61.ko /lib/modules/'uname -r'/kernel/drivers/net/wireless
sudo depmod
sudo modprobe rt61
#the module should now be loaded. verify it
sudo modprobe -l|grep rt61

# Activate the network (exemple using dhcp)
ifconfig ra0 up #if using a fixed address use ifconfig ra0 inet your_ip up
dhclient ra0
# You should be connected. :-)

You could now remove all files related to rt61 in your home directory
However, if you get a new kernel version, you may have to rebuid your driver again!
I recommend to keep the RT61 directory unless disk space in an issue.

# Now make it work at boot time
# Don't use make install as it would not be the supported Debian way to install the module
# Put an alias to associate ra0 to rt61 module in any file in /etc/modprobe.d
sudo echo "alias ra0 rt61"> /etc/modprobe.d/rt61
#edit your /etc/network/interfaces after keeping a clean copy
cd /etc/network
sudo cp interfaces interfaces.sav
sudo gedit interfaces
# the mapping hotplug section should look like
mapping hotplug
   script grep
   map eth0
   map ra0
# add the following line
iface ra0 inet dhcp #or iface ra0 inet your_ip
# if you've run the wireless tools GUI (system - administration - Network) you'll find a line with
auto ra0
# delete or comment out this line if your card is a PCMCIA card (avoid to try and start it before card manager is started)
# you don't need to add all these informations related to your SSID and key as everything is already defined into /etc/Wireless/RT61STA/rt61sta.dat
# save and exit

I recommend to reboot your system now. You should have network connectivity using your wireless card.

Microsoft Windows integration
=============================

NTP
===
Time synchronization.
Within a Windows 2003 domain, You'd better to get all nodes synchronized
Modify the /etc/ntp.conf file to include the server (see comments in the file)

cd /etc
sudo cp ntp.conf ntp.conf.sav
sudo gedit ntp.conf
#comment the line "server ntp.ubuntulinux.org"
#add the following line (as many lines as ntp servers you want to use)
server your_ntp_server_ip_address
restart your ntpd daemon (or wait for next reboot to get synchronized)

DHCP
=====
When getting a lease from the Windows DHCP server, the DNS must be updated to reflect the new address.
modify the /etc/dhcp3/dhclient.conf in adding the following lines

cd /etc/dhcp3
cp dhclient.conf dhclient.conf.sav
sudo gedit dhclient.conf
# Add the following lines to it
# This is most likely not the supported way, but it seems to work
# At least I can connect to my ubuntu machine without specifying it's IP address (What I wanted to achieve)

request subnet-mask, broadcast-address, time-offset, routers
   domain-name, domain-name-servers, host-name,
   netbios-name-servers, netbios-scope;
interface "eth0" {
send fqdn.fqdn "mynodename";
send fqdn.encoded off;
send fqdn.server-update on;
require subnet-mask,domain-name,domain-name-servers,routers;
}

X Terminal
=========
The idea is to keep working on my Windows NT Workstation for most of my tasks and being able to connect and work onto my Ubuntu machine where needed

MS Windows side
-------------------------
Install Cygwin on your Windows system ([http://www.cygwin.com/](http://www.cygwin.com/)) 95/98/NT/2000/XP
Cygwin is free software published under GNU General Public License.
During the installation process, develop X11 section, select xorg-x11-base and complete the installation.
edit \Cygwin\usr\X11R6\bin\startxdmcp.bat (on the disk where cygwin is installed)
locate the "SET REMOTE_HOST=" line and add your Ubuntu machine name there.
ex: SET REMOTE_HOST=myubuntu
locate the line that starts XWin and modify it as follow
%RUN% XWin -query %REMOTE_HOST% -scrollbars -lesspointer -clipboard -swcursor
save and exit.

GNOME side
------------------
You will have to modify your GNOME configuration to accept xdmcp connections from your windows workstation.

cd /etc/gdm
sudo cp gdm.conf gdm.conf.sav
sudo gedit gdm.conf
#locate the line "RemoteGreeter=/usr/lib/gdm/gdmlogin" and remove the comment sign if any
#locate the "[xdmcp]" section
Enable=true
HonorIndirect=true
#save and exit
restart gdm or reboot your system
you might have to modify your firewall (firestarter) configuration to accept X connections (ports 6000-6015) and xdmcp (port 177)

By running the script startxdmcp.bat on the windows side you should be able to establish a connection to your Ubuntu system and start an X login session.
Once connected, unlike with VNC, you will notice almost no performance degradation.

SAMBA
=======
My goal there was to be able to access files on shares on the Windows 2003 servers, from my ubuntu machine without integrating the machine into the domain, nor providing shares to the domain.
The inconvenience here is that you have to provide your password several times to access a share (once to access to the domain controller and once to access the
share on the server itself)
Modify your /etc/samba/smb.conf file

cd /etc/samba
sudo cp smb.conf smb.conf.sav
sudo gedit smb.conf
# In the [global] section update the "workgroup= MSHOME" line to
workgroup = MYDOMAIN
# I have also modified the name resolve order
name resolve order = lmhosts hosts dns wins bcast
# save and exit
restart samba or reboot

You might have to modify your firewall (Firestarter) configuration (ports 137-139 and 445)
You should be able to access shares on the windows domain by their names.
define printers that are shared from windows machines ...

Next step would be to fully integrate the machine to the windows domain.
refer to samba documentation ([http://us5.samba.org/samba/)](http://us5.samba.org/samba/)). But this was not my goal here.

Enjoy Ubuntu :mrgreen:

---

### Post by vinfred on 2006-05-19
You can also enable XDMCP as explained in [http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)


> 
1. Enable XDMCP
System->Administration->Login Screen Setup
Tab Security->Enable XDMCP
Tab XDMCP--> You can disable "Honor Indirect Requests"


---

