---
title: "Error connecting to blackbarry with Barry"
date: 2009-06-22
forum: General Help
---

### Post by TheoryWeary on 2009-06-22
Firstly, I wasn't sure where to put this so feel free to move it if there is a better location.

I'm trying to use Barry to backup my blackberry curve 8330, and later to sync my calendar with evolution using multisync. I believe the same problem is stopping me from doing both things, so I'm posting both error messages with the hope that someone will have experience with one of them. 

First, when i try to connect with barry:

```
brendon@ubuntu:~/Desktop/bbtether$ sudo barrybackup
Desktop: error getting command table
Sent packet:
    00000000: 06 00 0a 00 40 00 00 01 00 00                    ....@.....

Response packet:

```
However, if I used the the barry4all.sh script it successfully increases the USB power and charges the blackberry.

When attempting to connect with multisync I get the following error:

```

brendon@ubuntu:~/Desktop/bbtether$ msynctool --sync blackberry
Synchronizing group "blackberry" 
Member 2 of type barry-sync had an error while connecting: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed
Member 1 of type evo2-sync just connected
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to connect one of the members
Error while synchronizing: Unable to connect one of the members

```Thanks to anyone who can point me in the right direction; I'd be perpetually lost without the forums. :D

---

### Post by TheoryWeary on 2009-06-24
anyone?:(

---

### Post by allanmills on 2009-07-30
I am having the same problem as the OP mentioned when trying to use barry for the first time to communicate with my Blackberry.  This is the only place I've seen anything remotely resembling this problem.

Just hoping some Blackberry user might see this and reply or point to a resource.

Thanks for any help!  I'm loving my Kubuntu!

---

### Post by pvicc on 2009-08-12
I am also having the same problem. Once we overcome, i think all will sync well. I have BB 8900 with ubuntu jaunty.

---

### Post by JCampy on 2009-08-26
Found a solution that worked for me on the Suse boards.  (Solution edited for Jaunty - some distros put all udev rules under /etc/udev/rules.d).

sudo mv /lib/udev/rules.d/10-blackberry.rules /lib/udev/rules.d/65-blackberry.rules

Something, something, mumble rule 50-blah needs to run first. :)  Tried it, it worked, good enough for me.  You'll need to restart udev and reconnect or reboot.  I tried a udev restart, and didn't think about reconnecting until after I rebooted, so the reboot may or may not be required.

---

### Post by c001os on 2009-09-14
Hi all!

I have the following error 

Member 1 of type barry-sync had an error while getting changes: Desktop: unexpected command of 0x41 instead of expected 0x40
Member 2 of type evo2-sync just disconnected
Member 1 of type barry-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members


can anybody help me?

thx

---

### Post by kneewax on 2009-09-15
not sure if you are still having this issue - I was as I tried to configure Barry over the past few weeks.  I discovered taht upgrading to Barry-0.15 fixed the issue - barry-0.14 ships with Jaunty.

I still can't sync my task list - but I'm working on it!

---

### Post by Elludium_Q-36 on 2010-01-05
In the past, I've taken Barry from packages.debian.org and it worked well enough on Hardy.  Other problems had me reinstall Kubuntu on the system and I tried v13 / v 14 from various sources with poor results.

Complete removal and installing again with synaptic was not helpful as it did not download but used locally cashed installation files.

I downloaded and installed the files from packages.ubuntu.com and now I'm back to where I had been another time...

kubuntu@kubuntu:~$ ls /dev/ttyU* /dev/ttyS* /dev/ttyA*
ls: cannot access /dev/ttyU*: No such file or directory
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3
kubuntu@kubuntu:~$ barrybackup                              
Usb::Error caught in main:                                  
(-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed

kubuntu@kubuntu:~$ bcharge                                                                      
Scanning for Blackberry devices...
Found device #034...adjusting charge setting
usb_control_msg failed: code: -1, error sending control message: Operation not permitted

usb_control_msg failed: code: -1, error sending control message: Operation not permitted
...no Pearl adjustmentDetecting possible kernel driver conflict, trying to resolve...
Can't find Mass Storage interface, assuming 0.
usb_detach_kernel_driver_np() failed: could not detach kernel driver from interface 0: Operation not permitted
usb_set_configuration() failed: could not set config 1: Operation not permitted
...done
kubuntu@kubuntu:~$ btool
Usb::Error caught: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed

Some suggest copying udev rules from /lib/udev/rules.d/  to /etc/udev/rules.d/  Mine is named 10-blackberry.rules  contents follow:

#
# Blackberry devices
#
# Note: the following rules may appear wasteful, in that bcharge is run
#       twice: once for changing the mode, and once again after the
#       device resets itself to enter this mode.  This is required
#       in order to support older kernels (approx. 2.6.20 to 2.6.22) with
#       CONFIG_USB_SUSPEND enabled.  The second time bcharge is run
#       is when the -p argument comes into play, adjusting the device's
#       autosuspend settings.
#
# Note2: the SUBSYSTEM and ENV{DEVTYPE} checks are to prevent bcharge from
#       running each time a new endpoint is discovered by udev.
#       Both SUBSYSTEM and ENV{DEVTYPE} are included so that the version
#       of udev on your system doesn't matter.
#

#
# Older devices that only use 0x0001 (no USB Mass Storage)
#
BUS=="usb", SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="0001", SYMLINK+="bb-%k", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge -p %p"

BUS=="usb", ENV{DEVTYPE}=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="0001", SYMLINK+="bb-%k", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge -p %p"

#
# Newer devices with USB Mass Storage, 0x8004 + 0x0006 + 0x0004.
#

BUS=="usb", SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="0006", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge"
BUS=="usb", SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="8004", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge"
BUS=="usb", SUBSYSTEM=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="0004", SYMLINK+="bb-%k", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge -p %p"

BUS=="usb", ENV{DEVTYPE}=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="0006", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge"
BUS=="usb", ENV{DEVTYPE}=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="8004", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge"
BUS=="usb", ENV{DEVTYPE}=="usb_device", ACTION=="add", SYSFS{idVendor}=="0fca", SYSFS{idProduct}=="0004", SYMLINK+="bb-%k", GROUP="plugdev", MODE="0660", RUN="/usr/sbin/bcharge -p %p"

***************
********
***

Now the Readme in /etc/udev/rules.d/ is as follows:

The files in this directory are read by udev(7) and used when events
are performed by the kernel.  The udev daemon watches this directory
with inotify so that changes to these files are automatically picked
up, for this reason they must be files and not symlinks to another
location as in the case in Debian.

Packages do not generally install rules here, this directory is for
local rules.  If you want to override behaviour of package-supplied
rules, which can be found in /lib/udev/rules.d, you can do one of
two things:

 1) Write your own rules in this directory that assign the name,
    symlinks, permissions, etc. that you want.  Pick a number higher
    than the rules you want to override, and yours will be used.

 2) Copy the file from /lib/udev/rules.d and edit it here; you
    should generally only do this if you want to prevent a program
    from being run.


Files should be named xx-descriptive-name.rules, the xx should be
chosen first according to the following sequence points:

 < 60  most user rules; if you want to prevent an assignment being
       overriden by default rules, use the := operator.

       these cannot access persistent information such as that from
       vol_id

 < 70  rules that run helpers such as vol_id to populate the udev db

 < 90  rules that run other programs (often using information in the
       udev db)

 >=90  rules that should run last

**************
*********
***

So that suggests that mere copying files Code: cp  as some recommend, is futile.

Taking packages from other sources can be less than favorable or adding Debian as a package can cripple synaptic and apt if done incorrectly.

Maybe I'll dump V14 and see if all the packages for V15 are on packages.debian.org and manually download them on my 2Kb/second iDEN connection but I had hoped someone had the answer...

---

### Post by JohnGalt2010 on 2010-02-06
I installed barrybackup-gui 0.14-2.1ubuntu1 today with the new 2.6.31-19 kernel installed.  

I too was also getting the following error that **TheoryWeary** noted earlier:
```
$ barrybackup
Usb::Error caught in main:
(-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed
```From the RedHat Bugzilla, I found the following:> Nick Boldt                                                  2009-01-05 11:48:11 EST

<snip>
                          I sent my concerns to Petr Machata, who responded thus:

<snip>

>  - look at the output of /sbin/lsusb, which bus and device your
> blackberry is connected to
>  - under root, chmod a+rwx /dev/bus/usb/<bus>/<device>

<snip>This worked for me.

Update:  It seems that my bus number stays the same, but my device number changes as I attach and detach my phone.  I can still run barrybackup as root, but that is not what I am wanting to do.

---

### Post by Elludium_Q-36 on 2010-03-17
Barry is the only reason I "downgraded" from 8.04 to 9.04 and it seems to have been a mistake as 9.94 has been pretty buggy AND thusfar I haven't been able to use Barry.

Using my old BB as a modem would have been helpful too.

I'm crossing my fingers that 10.04 is not so buggy and hope to do a fresh install and am looking for another brand of smart-phone that's open-source/linux friendly.  The BB will make a nice paperweight.

---

### Post by Blackhawke on 2010-05-16
> **Elludium_Q-36 said:**
> Barry is the only reason I "downgraded" from 8.04 to 9.04 and it seems to have been a mistake as 9.94 has been pretty buggy AND thusfar I haven't been able to use Barry.

Using my old BB as a modem would have been helpful too.

I'm crossing my fingers that 10.04 is not so buggy and hope to do a fresh install and am looking for another brand of smart-phone that's open-source/linux friendly.  The BB will make a nice paperweight.

Well... I just upgraded to 10.04 LTS and the problem still exists for Barrybackup (though bcharge works just fine.) However, changing the permissions on on the appropriate USB bus device to 777 as suggested above is a hack that works. Unfortunately I'm finding no guidance on how to create a UDEV rule that will allow barrybackup to work. :(

---

### Post by marcottebj on 2010-07-20
It took some research, but I found the solution to the problem, and I thought others might benefit as well (since this thread kept coming up in my google searches)

1. open a terminal window
2. type btool -M (you should get the operation not permitted error if you're having this problem)
3. type the command "lsusb" to get a listing of all usb devices plugged into your system
4. Find the one listed as Research In Motion and write down everything you see listed for that device
5. in the terminal, enter "gedit /etc/udev/rules.d/10-blackberry.rules" (without quotes)
6. Here, I copied the top two entries (four lines) under newer devices with USB storage
7. I pasted what I had copied at the bottom of that page, and verified (or modified) the part in both entries: SYSFS{idVendor}=="ofca" (ofca should represent first part of the ID from the lsusb command that you wrote down)
8. Next I modified the part of the script (both entries): SYSFS{idProduct}=="0004" (in my case I had to change it to SYSFS{idProduct}=="0008" (the number should correspond to the last part of the ID right of the colon from the LSUSB command that you wrote down)
9. Save the file
10. Reboot the udev service (or just restart your machine)

In my case everything worked, and I did not have any further permission issues. The blackberry device syncs perfectly every time.

---

### Post by csuarezmtz on 2010-07-28
@marcottebj

I tried to follow your guide, however found some problems, i can't paste anything in the rules folder it says i have no permissions on my laptop. My device keeps booting when i connect it. It's a bb curve 8530 and im using ubuntu 10.4 LTS

---

### Post by marcottebj on 2010-10-12
for step 5, try using "sudo gedit /etc/udev/rules.d/10-blackberry.rules"
 
That should fix your permission issue

---

### Post by roymilner2001 on 2010-11-27
Thank you! I've been trying for over a week to figure out how to make this work. I'm finally online with my blackbberry as a modem. I really appreciate you posting this.

---

### Post by Kaspar001 on 2010-12-12
Hello,
I'm trying to make a backup of my blackberry on ubuntu. I am using ubuntu 10,04 with a gnome interface. I have installed barry following the synaptic packages manager. When I am connecting my blackberry it is recognised by the computer but barry is not opening. I can also not find this programme in the panel of programmes of the computer. Can anyone tell me how to open and/or to use this backup programme?
Thanks a lot.

---

