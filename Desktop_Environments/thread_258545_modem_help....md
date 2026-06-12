---
title: "modem help..."
date: 2006-09-16
forum: Desktop Environments
---

### Post by maduranga on 2006-09-16
:) hello... i have a huawei dial-up modem.. i'm gettin' this error when i run the command ./configure.

 **"configure : error: cannot find usb-serial.h in kernel sources"**

 How can i overcome this error? plz tell me if u got anyother way to install this modem (HUAWEI ETS2288).. 

---------
maduranga

---

### Post by ramnarayan on 2006-11-29
[QUOTE=maduranga;1505498]:) hello... i have a huawei dial-up modem.. i'm gettin' this error when i run the command ./configure.

 **"configure : error: cannot find usb-serial.h in kernel sources"**

 How can i overcome this error? plz tell me if u got anyother way to install this modem (HUAWEI ETS2288).. 

Hi

Check out

[http://ubuntuforums.org/newreply.php?do=newreply&p=1505498](http://ubuntuforums.org/newreply.php?do=newreply&p=1505498)

all the best,
I am too struggling with setting it up - but it seems to work

ram
ram

---

### Post by chaminga on 2007-05-17
NOTE: The majority of credit of the beneficiaries should go to Sudirikku Mohanjith.

So let's start. According to my knowledge both Suntel and Lanka Bell CDMA phones (perhaps all CDMAs) use HUAEWI ETS1000 Series Fixed Wireless Terminal with the TI USB 3410 cable (mine is a serial to USB cable and I don't know whether there are serial to serials too. However here we assume a serial to usb cable). The problem is with this cable and not with the HUAEWI terminal.

SYSTEM REQUIREMENTS
Linux with kernel above 2.6.
(Check it by command in console uname -a)
(Personally Tested on FC6, should work on any Linux Distribution)

STEP 1
Plug in the Serial to USB cable.
Now in console type command dmesg -c search for the following lines.

ti_usb_3410_5052 1-1:2.0 : TI USB 3410 1 port adapter converter detected
usb 1-1: TI USB 3410 1 port adapter converter now attached to /dev/ttyUSB0

If you see ttyUSB0 in the kernel message then also your modem is detected and you are ready to start, now just jump to STEP 2 and proceed.

If the lines are as follows, you have to do a little bit of coding.

ti_usb_3410_5052 1-1:1.0: TI USB 3410 1 port adapter converter detected
ti_usb_3410_5052: probe of 1-1:1.0 failed with error -5

Now we have to make a rule file in /etc/udev/rules.d/ named 026_ti_usb_3410.rules
In console login as root or use sudo to create the file.

cd /etc/udev/rules.d/
sudo vi 026_ti_usb_3410.rules

In Ubuntu you will be asked for your password. (I don'y know whether it is the same in FC also)
Anyway in FC (or in other distros) type

su

then will be asked for your password.

Here you can use a preferred text editor rather than vi.

Now paste the following lines to the file created.

#TI USB 3410
SUBSYSTEM=="usb_device" ACTION=="add" SYSFS{idVendor}=="0451",SYSFS{idProduct}=="3410" \
SYSFS{bNumConfigurations}=="2" \
SYSFS{bConfigurationValue}=="1" \
RUN+="/bin/sh -c 'echo 2 > /sys%p/device/bConfigurationValue'"

Save and exit.

Now once again plug out your USB/Serial cable and then plug in.
Again type dmesg -c in console.
Check the kernel message and find the following line.

ti_usb_3410_5052 1-1:2.0: TI USB 3410 1 port adapter converter detected
usb 1-1: TI USB 3410 1 port adapter converter now attached to /dev/ttyUSB0

CONGRATULATIONS you have succeeded in STEP 1.

STEP 2
This is about creating a dialup script using wvdial
Now edit your /etc/wvdial.conf

cd /etc
sudo vi wvdial.conf

Following is a sample of a wvdial.conf file

[Dialer ptcl]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = YourUsername
Password = YourPassword
PPPD Options = crtcts multilink usepeerdns lock defaultroute

Important Note: Stupid Mode should be set to 1 otherwise the hash sign # with Dialing phone number will not be treated by wvdial.

This file replaced YourUsername and YourPassword with appropriate username and password, works well with Ubuntu and FC6.

PROBLEM
(Sudirikku Mohanjith has experienced this problem in FC6. But I didn't. So I hope that all Ubuntu users can jump to STEP 3).
When you will connect to ptcl with wvdial ptcl command as a root , it will not browse any page and will disconnect.

You have to set the nameserver in the /etc/resolv.conf .You can get the nameserver IPs from the terminal window when wvdial is trying to connect to your ISP.

Put those two nameserver in /etc/reslov.conf.
Now again as a root in console wvdial ptcl.

STEP 3
Just type
wvdial ptcl

NOTE: In FC6 this command should be executed as root.

So we have come to the conclusion. Try this and post your experiences also regarding this matter.

Finally I would like to end this with the ending as on Sudirikku Mohanjith's email (some more added).

---

