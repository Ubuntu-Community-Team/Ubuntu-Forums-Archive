---
title: "Stream Media to XBox 360 with uShare uPNP server on Ubuntu"
date: 2011-05-27
forum: Gaming &amp; Leisure
---

### Post by epyonx1 on 2011-05-27
Basically, we're trying to set up a Universal Plug & Play (uPNP) server that can be used to WIRELESSLY stream videos, music and pictures to your XBox 360 from a network-connected PC.

In General:
STEP 1: Install uShare.
STEP 2: Set up uShare.
STEP 3: Entry in fstab. Make sure the partition(s) which contains the media is auto-mounted.
STEP 4: Add uShare to /etc/rc.local

The Specifics:

STEP 1: Install uShare
a) Go into Synaptic Package Manager & install "ushare" or type in "sudo apt-get ushare" into the terminal



STEP 2: Set up uShare
a) Type in "sudo gedit /etc/ushare.conf" and make sure the options are as follows:
	USHARE_NAME=<Your Server Name> (e.g. sharedfolder)
	USHARE_IFACE=<Your internet interface> (e.g. eth0)(Use System > Preferences > Network Connections to find out)
	USHARE_PORT=49153
	USHARE_DIR=<Shared Folder Path #1>, <Shared Folder Path #2>, etc ...
	USHARE_ENABLE_WEB=yes (To enable use of a web browser to manage shared folders)
	USHARE_ENABLE_XBOX=yes/no (If you have an XBox 360)
	USHARE_ENABLE_DLNA=yes/no (If you have a PS3 or other DLNA devices)
b) Use your router settings to find out which INTERNAL IP address is assigned to your computer. Make sure that address is RESERVED for that computer in the router settings.The web browser interface is optional since you've already edited the .conf file but you MUST go into your router settings to reserve the IP address of your computer and open up the port 49153. You might as well open up other ports as well for XBox Live, such as: 88 (UDP), 3074 (UDP and TCP), 53 (UDP and TCP), 80 (TCP), 1863 (UDP and TCP). For more information, see [http://support.microsoft.com/kb/908874](http://support.microsoft.com/kb/908874))
c) Open up your web broswer and type in http://<The INTERNAL IP Address of your computer>:49153/web/ushare.html (



STEP 3: Entry in fstab
Ubuntu does not always auto-mount a partition until you try to access it (My media is stored on an NTFS partition so it can be accessed by both Windows & Linux), so you have to make sure that it mounts each time on boot.

a) If you do not know the specifics of the partition in which your media will be placed, type in the following in terminal: "sudo gparted"
b) Find the partition you're looking for, right-click, and click "Information"
c) Type into the terminal: "sudo gedit /etc/fstab"
d) Make sure the following is saved into fstab:
	UUID=<The ID # of your Partition (or the corresponding /dev/__)>   <The mount point (e.g. /media/sda1/sharedfolder)>  <type of file system (e.g. ntfs)>  <option (e.g. defaults)>  0  0



STEP 4: Add uShare to /etc/rc.local

Type in:
a) "sudo gedit /etc/rc.local"
b) Make sure your rc.local file looks something like this:
---------------------------------------------------------
#!/bin/sh -e
#
#rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 10 && /etc/init.d/ushare start

exit 0
---------------------------------------------------------


Now you can stream movies, music and pictures from your computer to your 360 with Ubuntu! 
The video database will update automatically upon rebooting. 
You can also manually reload the database with the Web Interface of by typing into the terminal, "sudo /etc/init.d/ushare reload".
Enjoy!

---

### Post by gareth9 on 2011-06-10
I did all the instructions but having a problem that my xbox 360 is telling me that I a firewall maybe blocking the connection. But how could that be since I added my pc's ip address and 49153 in the port forwarding section of my router. I also know that UFW is not set to start at login.. DO you have any suggestions for me or any set I should take to get it to work...i am seeing ushare on the xbox but just cant go any further..Thanks

---

### Post by TyTiger on 2011-09-11
> **gareth9 said:**
> I did all the instructions but having a problem that my xbox 360 is telling me that I a firewall maybe blocking the connection. But how could that be since I added my pc's ip address and 49153 in the port forwarding section of my router. I also know that UFW is not set to start at login.. DO you have any suggestions for me or any set I should take to get it to work...i am seeing ushare on the xbox but just cant go any further..Thanks

If you have the firewall messege comming up, make sure you have USHARE_ENABLE_DLNA set to no
and that you have 
USHARE_ENABLE_XBOX=yes (this is off by default)


```
USHARE_ENABLE_DLNA=no
```
I found having this on (=yes) seems to conflict with the Xbox360 compatibility, turning it off resolved that message for me.

and remember to restart uShare when you change the config and allow it time to index your shared directories.

Also you don't need to touch the firewall on your router as this is only so the outside world can contact computers on your local network, if your Xbox resides on the same network as your uShare box, port forwarding and router configuration is not necessary and doesn't effect your Xbox's ability to contact your uShare box over the local network. If anything it poses a mild security risk.

---

### Post by chromatica86 on 2011-09-15
Is ushare better than ps3 media server?

---

