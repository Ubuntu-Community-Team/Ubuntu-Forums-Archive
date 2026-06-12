---
title: "Huawei ETS 2251 Tele+modem"
date: 2008-12-14
forum: General Help
---

### Post by Gayan Kalhara on 2008-12-14
**HI**

[B]I'm using Huawei ETS 2251 modem(telephone suntel CDMA)to access to net...
I'm having probs with it.. Huawei Don't have a Drivers 4 linux. But As i know it can be configured.

I searched google and I found this methord.[/B]

[http://kalpapathum.blogspot.com/2007/03/suntel-and-lanka-bell-cdma-phones.html](http://kalpapathum.blogspot.com/2007/03/suntel-and-lanka-bell-cdma-phones.html)

====================================================================

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
======================================================= =========

[B]SO i try to do this but xubuntu 8.4 seems to not supporting with dmesg -c command ...

ppl who one the filed please help me on this.. I try to configure a another modem driver.. but it too hard for me...

I think you would be kind enough to help me on this...

thanks for reading ... Please reply As Soon As you can [/B]

---

