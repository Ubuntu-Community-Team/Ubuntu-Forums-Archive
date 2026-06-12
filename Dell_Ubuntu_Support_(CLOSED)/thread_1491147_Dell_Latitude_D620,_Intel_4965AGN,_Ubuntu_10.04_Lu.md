---
title: "Dell Latitude D620, Intel 4965AGN, Ubuntu 10.04 Lucid"
date: 2010-05-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kate9954 on 2010-05-23
Hello, everyone.  

I recently installed Ubuntu 10.04 onto a Dell Latitude D620, and I was never able to get my wireless working at all.  I've read a number of threads concerning this, and it would appear that I am not alone in my difficulties in this regard.  The following will probably work with most any supported hardware (and the D620), but I have only tested it on this system.

The symptoms are that the wireless card refuses to turn on.

First of all, the root of a great many D620 problems is in the BIOS.  The very first step is to ensure a couple of things.  I can't give specifics, because there are different BIOS versions and the actual commands may differ.  You need to ensure that wireless is enabled, and that the wireless switch is set to control the internal wireless card.  I set mine to control wireless only, as my Dell does not have built in Bluetooth.

If you have the BIOS set up correctly, the wireless card will turn on (if the switch is on) about the time you log in.  And the LED will light up.  Most likely, however, you will still be unable to connect - it is worth a try, though.

Assuming you could not connect:

Next, install wicd:

*sudo apt-get install wicd*

The first thing your system will do on a fresh install is go get the source repository into your listing.  Just repeat the above command to install the software.

NOTE:  It is critically important to successfully install wicd - and pay attention to be sure that you have - before removing your network manager, as removing the network manager first will leave you without any network at all, wired or otherwise.

Then, ***after ***a successful wicd install, and before attempting to connect or rebooting, do the following:

[I]sudo apt-get purge network-manager-gnome

[/I]And then:

*sudo apt-get purge network-manager*

The native Gnome network manager conflicts with wicd, so it has to go, hence the above commands.  Reboot at this point. 

Once you have booted up with wicd installed, a left click on the wicd panel icon will start a scan.  You will be presented with a list of available wireless access points.  Choose yours and click the box to connect automatically.  You can use the properties button to set up your network if you use a static IP and/or (I certainly hope) wireless security - then just click connect.  

Congratulations.  Your wireless is now working - mine is now working flawlessly.  And believe me, I tried a lot of other stuff first - all except for *ndiswrapper* and/or backporting, neither of which I particularly wanted to do.

Best of luck,

Kate
*MCSE in Linux Recovery*

---

### Post by mikewhatever on 2010-05-23
Wicd is a good network-manager, and installing it in Ubuntu used to remove the network-manager packagers. Apparently, that's not the case with Lucid.
Thanks for sharing.

---

### Post by kate9954 on 2010-05-23
Thank you, LOL.  Very much a Linux newbie - but learning . . .

Kate

---

### Post by faheyd on 2010-11-19
> **kate9954 said:**
> Hello, everyone.  

I recently installed Ubuntu 10.04 onto a Dell Latitude D620, and I was never able to get my wireless working at all. 
....

Best of luck,

Kate
*MCSE in Linux Recovery*

Kate, I've been dinking with this problem for a week on my HP 2700T CTO laptop with the 3945AGN intel chip with ubuntu 10.10 maverick. (which worked in 10.04 perfectly fine).
Your solution, is the only solution that worked. All the other threads die in frustration.

Key words:  3945 intel wireless AGN
sudo lshw -C network
 *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:4a:44:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

KATE, THANK YOU!

---

### Post by jhogan on 2011-03-29
Thanks. This worked on my Latitude D630 with the 4965agn NIC. It's funny, a week ago when I installed Lucid on this machine, I installed wicd (as it is my preferred network manager) and wireless worked up until I restarted it, then it didn't work until I remove the other network managers as the article indicates.

---

### Post by seierson on 2011-04-08
Hi Gang,

I have a D630 and have an Intel Wifi Link 5300.  I haven't tried this at home to see if it provides a more reliable connection or not, but the very fact that it's capable of turning off my wireless when I plug into a wire at home is enough of a reason for me to switch to WiCD.  

Removing network-manager required me to go into recovery mode at the boot menu, then drop to root shell prompt (without network support).  After running

apt-get purge network-manager

I also ran:

apt-get autoremove to get rid of some no longer required dependency.  

Thanks,
Christian Blackburn

---

### Post by sikshady on 2011-04-11
this solved also my problem on xps m1330:
[http://ubuntuforums.org/showthread.php?p=10649734#post10649734](http://ubuntuforums.org/showthread.php?p=10649734#post10649734)
thanks a lot

---

