---
title: "Wifi Connection drops m1330"
date: 2008-02-23
forum: Dell  Ubuntu Support
---

### Post by goombamd on 2008-02-23
J have a m1330 that came with Vista.  Vista has had so many issues, I recently switched to Ubuntu.  One issue I did not have with Vista was losing Wifi connection. 

Sometimes my Wifi in ubuntu will stay connected for hours, sometimes for 30 mins.  Then, it drops for no good reason and the only way to restore it is by rebooting.  I tried to disable and re-enable wifi, I tried to turn off wifi with the wifi power switch on the laptop and then back on, etc.

When I re-enable wireless or try to connect, it seems that it is unable to find an IP address.  It also asks me to re-provide my wireless key.  I type the correct key, and it tries to connect for a while.. then I get asked for the wireless key again.  

The only solution is to reboot (so far.)  Any help?

P.S. My Hardware Information lists me as having Dell WLAN Switch (i think the on/off button) and an Intel PRO/Wireless 4965 AG or AGN Network Connection

---

### Post by Sam Lars on 2008-02-23
Are you using ndiswrapper or native drivers?
Can you
```
sudo ifdown eth0
sudo ifup eth0
```
where eth0 is your interface?

---

### Post by goombamd on 2008-02-24
native drivers... i'll try ndiswrapper

---

### Post by notwen on 2008-02-24
[This issue]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues") may be affecting your wireless.  The ipw3945 module is really buggy(in Gutsy) and swapping over to the iwl3945 module will correct this.  I was having similar issues w/ my Inspiron 1420n.  Post back if you have any problems w/ the workaround.  =]

---

### Post by goombamd on 2008-02-24
This is what I did... if this doesn't work I'll try ndiswrapper :) Thanks all... Assume this works if I don't repost lol


From [https://answers.launchpad.net/ubuntu/+question/16768](https://answers.launchpad.net/ubuntu/+question/16768)


 Anton Khokhlov said on 2007-12-20:

I got the same problem on my HP 8510p laptop. And found the cure (as I think now)! Ubuntu 7.10 seems to use old version of the intel wireless firmware. All you need is:
- Download the firmware archive from [http://www.intellinuxwireless.org/?p=iwlwifi&n=Downloads](http://www.intellinuxwireless.org/?p=iwlwifi&n=Downloads)
- tar xvf iwlwifi-4965-ucode-what version you got.tgz
- Copy iwlwifi-4965.ucode from the unpacked folder into /lib/firmware/your kernel version/iwlwifi-4965.ucode and /lib/firmware/your kernel version/iwlwifi-4965-1.ucode (you should overwrite two files with the same data)

After that you need to reboot or just to say
rmmod iwl4965
modprobe iwl4965
Now on my computer it have been working for the whole night without any problem. But I can not guarantee it works everywhere.

---

### Post by goombamd on 2008-02-24
OK the post above didn't solve my issues, though apparently it has solved the issues for others.  I just installed the ndis drivers and it seems to be working... but time will tell if the connection drops.

This is how to install the ndis drivers.

1. Search for ndiswrapper in synaptics manager.  Install the 3 items that appear.  It asked me for the ubuntu installation cd, so apparently that's required.

2. Get the WinXP drivers from Intel (I got them here)
[http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=All&OSFullName=All+Operating+Systems&lang=eng](http://downloadcenter.intel.com/download.aspx?url=/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP&agr=N&ProductID=2753&DwnldId=13000&strOSs=All&OSFullName=All+Operating+Systems&lang=eng)

3; Follow the instructions at [http://ubuntuforums.org/showthread.php?t=471794](http://ubuntuforums.org/showthread.php?t=471794)

I had to remove the current driver and replace with the driver I downloaded.  Not sure if that was necessary, but it worked.  If the driver is already installed or you are getting an "invalid driver" message, follow the directions here.

[http://ubuntuforums.org/showthread.php?t=471794&page=3](http://ubuntuforums.org/showthread.php?t=471794&page=3)

or type
**sudo ndiswrapper -r netw4x32 **

and reinstall the driver you downloaded from intel with 

**sudo ndiswrapper -i netw4x32.inf** (while in the directory containing the new driver)

---

