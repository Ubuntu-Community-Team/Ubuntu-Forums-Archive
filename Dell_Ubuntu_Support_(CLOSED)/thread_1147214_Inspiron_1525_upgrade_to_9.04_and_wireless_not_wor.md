---
title: "Inspiron 1525 upgrade to 9.04 and wireless not working"
date: 2009-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gbazuin on 2009-05-03
I used the package manager to update from 8.10 to 9.04 and now the wireless isn't working. The blue led is not lit. If I pick 2.6.27.11 from grub it works, but not with the default 2.6.28.11. Please help, thanks.

---

### Post by Minipalmer on 2009-05-04
I also upgraded recently. Though, my wireless light WAS lit up. I got it working. I just made a thread about this, hope it helps.

[http://ubuntuforums.org/showthread.php?t=1148958](http://ubuntuforums.org/showthread.php?t=1148958)

---

### Post by gbazuin on 2009-05-07
Thanks for the tip.
I tried it and it didn't work.
When I did it in 2.6.28.11 I got:
No proprietary drivers are in use on this system.
When I tried it in 2.6.27.11 (the one that was working) I saw the Broadcom driver listed. When I disabled it the wireless led didn't come on.

I also tried:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
I didn't get past the 1st sentence:
Open System > Preferences > Network Configuration.
There is no Network Configuration listed under System > Preferences

It's a dual boot with Vista. I have a 530n and I'd never buy a Dell without Windows. The price is the same and there's no Linux support from Dell. When I tried to get the BIOS updated a couple of months after I bought the 530n I got the phone tag run-around. All the people I talked to on the phone where nice enough it's just they weren't Linux and the email web support kept giving me that number to call.

Anyway what doesn't work:
Webcam & Google Earth: I've given up and use Vista
Sound: I tried the wiki and that didn't help with 8.10 sometimes the keyboard beep would work, one kernel update the all the sound worked "out of the box" and the next kernel update broke the sound again.

---

### Post by Minipalmer on 2009-05-07
Well my wifi stopped working again yesterday in class, haha. But now it's working. I'm not sure what the deal is. I've just been switching my drivers on and off and it randomly works.

I'm planning on doing a clean sweep and installed the Dell Ubuntu 9.04 iso dual booting with Vista.

Have you tried to Dell iso?

---

### Post by gbazuin on 2009-05-07
> **Minipalmer said:**
> 

Have you tried to Dell iso?

Haven't tried the iso. I don't travel that much so just plug it in at home. Don't want to go through the trouble of restoring all my data if I use the iso.

---

### Post by coffeeaddict22 on 2009-05-09
Hi, 
I'm running a Studio 17 and a Inspiron 530 with reasonable success, one dual one triple booting.
What's the problem with wireless?  At a guess, the issue will be the changeover from ndiswrapper to builtin drivers.  Open a terminal, put in the following 2 commands, and post the results back.
```
lshw -C network
iwconfig

```

Additionally, the webcam works fine.  What program are you trying to run it in?

---

### Post by gbazuin on 2009-05-10
> **coffeeaddict22 said:**
> Hi, 
I'm running a Studio 17 and a Inspiron 530 with reasonable success, one dual one triple booting.
What's the problem with wireless?  At a guess, the issue will be the changeover from ndiswrapper to builtin drivers.  Open a terminal, put in the following 2 commands, and post the results back.
```
lshw -C network
iwconfig

```

Additionally, the webcam works fine.  What program are you trying to run it in?

Thanks for the help.

I'm trying to use cheese for the webcam, but that's not really a concern not working.

The wireless I want to get working for next time I travel.
Here's the outputs of the commands:

gary@gary-laptop:~$ sudo lshw -C network
[sudo] password for gary: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e1:c9:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.52 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
gary@gary-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by coffeeaddict22 on 2009-05-12
OK.  If you look at the output of lshw, you&#314;l notice there´s no driver listed for the wireless network... could be a problem.  Is there a proprietary driver listed in System/Administration/Hardware Drivers?  If so, what happens if you enable it?

---

### Post by gbazuin on 2009-05-12
> **coffeeaddict22 said:**
> OK.  If you look at the output of lshw, you&#314;l notice there´s no driver listed for the wireless network... could be a problem.  Is there a proprietary driver listed in System/Administration/Hardware Drivers?  If so, what happens if you enable it?

When I do:
System/Administration/Hardware Drivers
I get:
No proprietary drivers are in use on this system.

And none are listed in the box below.

On the kernel that works the Broadcom driver is listed and it works when it's enabled, doesn't work when not enabled.

---

### Post by coffeeaddict22 on 2009-05-12
OK.  Need to figure out why the driver isn't there.  If you've got a clean hard drive (ie not too much of your own files) a reinstall is sometimes quicker.
If you're willing to play, first have a look to see what's loaded.  ```
lsmod
``` will list all the modules; the ones of most interest are any that look like wireless drivers, especially ndiswrapper.

Just to confirm, when you look in System/Administration there is no option of "Network tools"?  And System/Preferences has nothing under "Network Configuration"?

---

### Post by gbazuin on 2009-05-12
> **coffeeaddict22 said:**
> OK.  Need to figure out why the driver isn't there.  If you've got a clean hard drive (ie not too much of your own files) a reinstall is sometimes quicker.
If you're willing to play, first have a look to see what's loaded.  ```
lsmod
``` will list all the modules; the ones of most interest are any that look like wireless drivers, especially ndiswrapper.

Just to confirm, when you look in System/Administration there is no option of "Network tools"?  And System/Preferences has nothing under "Network Configuration"?

Thanks for helping with this. I don't want to reinstall because it still works with kernel 2.6.27-11-generic (and Vista) just not with 2.6.28-11-generic. I'm learning more about Linux so that's a good thing. BTW I retried cheese for the webcam in 9.04 and it works. So that got fixed from 8.x.

I did a uname -r >lsmod.bsd; lsmod >>lsmod.bad from 28 and >lsmod.ok from 27. I also did a lsmod | sort good and bad and a diff --side. I mored them to a text file and attached it (I hope).

 more lsmod.bad lsmod.ok lsmod.diff >lsmod.txt

---

### Post by coffeeaddict22 on 2009-05-13
OK can't see anything obvious... what does ```
LSPCI -v
``` return? In particular, can you post back the stuff under the Broadcom?  ```
lspci -v |grep Broadcom -B15 
```should do it.

---

### Post by gbazuin on 2009-05-13
> **coffeeaddict22 said:**
> OK can't see anything obvious... what does ```
LSPCI -v
``` return? In particular, can you post back the stuff under the Broadcom?  ```
lspci -v |grep Broadcom -B15 
```should do it.

Thanks again. The -B in grep is new to me so learning something new every day. Did you mean -A to get stuff after? Anyway that's what I did, but also did the lspci and more'd the one that's ok and one that's bad to the attached txt file. (txt was 21k over the txt limit so I gzip'd it).

I also looked at the broadcom.ko files they're different for the older one that works and the new one that's bad.

gary@gary-laptop:/lib$ find . -name broadcom.ko -ls
2360714   16 -rw-r--r--   1 root     root        14832 Apr 16 20:42 ./modules/2.6.28-11-generic/kernel/drivers/net/phy/broadcom.ko
6488098   16 -rw-r--r--   1 root     root        14804 Apr  1 15:47 ./modules/2.6.27-11-generic/kernel/drivers/net/phy/broadcom.ko

---

### Post by coffeeaddict22 on 2009-05-13
Really dumb question, but the card is turned on, isn't it?  There'll be a switch on the side of the laptop somewhere.
 
The problem is you seem to have a card, and a driver; for some reason, they're not connecting.

Have you looked through the output of ```
dmesg
```
Another place to check is /var/log/messages; the easiest place to start (it's a LONG file) would be the last few lines just after a boot up, then (if nothing looks suspicious) try ```
cat /var/log/messages |grep Broadcom -C5
```

---

### Post by gbazuin on 2009-05-13
> **coffeeaddict22 said:**
> Really dumb question, but the card is turned on, isn't it?  There'll be a switch on the side of the laptop somewhere.
 
The problem is you seem to have a card, and a driver; for some reason, they're not connecting.

Have you looked through the output of ```
dmesg
```
Another place to check is /var/log/messages; the easiest place to start (it's a LONG file) would be the last few lines just after a boot up, then (if nothing looks suspicious) try ```
cat /var/log/messages |grep Broadcom -C5
```

Switch is on. In Grub if I select 2.6.28-11-generic it doesn't work the blue led doesn't come on if I boot into 2.6.27-11-generic the blue light comes on and it finds my Linksys. I boot back and forth a lot to try to figure out what's different between bad and ok. I looked at /var/log/messages and nothing there about Broadcom.  It hasn't even been written to the last couple of times I've rebooted. I tar'd the dmesg output (too long for txt attachment). 

tar cvf dmesg.tar dmesg.bad dmesg.ok

The .ok is from 2.6.27-11 and .bad from 2.6.28-11.

Thanks again, Gary

---

### Post by coffeeaddict22 on 2009-05-14
If you boot into the new setup, and plug in a wired connection, are there any restricted drivers visible in System/Administration/Hardware Drivers then?

---

### Post by gbazuin on 2009-05-14
> **coffeeaddict22 said:**
> If you boot into the new setup, and plug in a wired connection, are there any restricted drivers visible in System/Administration/Hardware Drivers then?

I pulled out the Ethernet cable, powered up and no restricted drivers showed up under System/Administration/Hardware plugged in the cable and still no drivers. I did see Broadcom mentioned in /var/log/jockey.log so I did the works and no works into .bad and .ok tar'd them and attached it. Nothing about Broadcom in the other log files from today.

---

### Post by coffeeaddict22 on 2009-05-14
Next thing I'd do is try installing the Broadcom drivers- they're at [this site]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by gbazuin on 2009-05-14
> **coffeeaddict22 said:**
> Next thing I'd do is try installing the Broadcom drivers- they're at [this site]("http://www.broadcom.com/support/802.11/linux_sta.php")

Got it!! Thanks for your help and patience.

Here's what I did went to [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

read the readme.txt file so as not to plagiarize I won't paste it here but just what step numbers I did.

step 1 and 2
step 3
Downloaded the 64 bit version, confusing because I've run a 32 bit operating system on a 64 bit processor (I think) and from the description a 64 bit machine gets the type 64 download file. That didn't work so I downloaded the 32 bit version
step 4
step 5
which got me to having a wl.ko in the directory I made in step 1

didn't find any drivers in the next set of steps 1 and 1a so put wl.ko into 
/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless
did the step 3 (depmod) and 4 (modprobe wl) and my blue led came on and it found my home network.
I rebooted and led came on and network connected so it's fixed.

---

### Post by coffeeaddict22 on 2009-05-14
Excellent.
If you get bored, have another look in lshw -C network; you'll see what's different.  Another nice trick is nm-tool; it shows you what the network manager can see, so is good if you're travelling.
If you're not sure of the type of Linux you're running, ```
uname -a
``` shows the lot.  In your case, there's a bit at the end with x86_32 (I think- this machine's on 64 bit and I'd have to kick the kids off to see what the 32 bit one says exactly) that tells you what you're running.

---

