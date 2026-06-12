---
title: "Wifi problem"
date: 2009-03-13
forum: General Help
---

### Post by chrome123 on 2009-03-13
I had a somewhat old laptop laying around and I installed ubuntu on it, I'm very happy with ubuntu ("first" time user).

Everything runs great on it (even the graphic's stuff (very old GPU so I'm impressed)).

BUT, the wifi doesn't work, I've found out why.

It's the button on the laptop that normally toggles (enable/disable) the wifi in windows, it doesn't work in ubuntu though.
The wifi is therefor disabled.

```
****@Laptop:~$ sudo lshw -C network
[sudo] password for ****: 
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:16:d3:60:9f:b3
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:6b:a9:2c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
```

Can I enable this using a terminal command?

---

### Post by pytheas22 on 2009-03-13
Please run these commands, then wait a few seconds and see if wireless networks appear:
```

sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

If so, we can make the fix permanent.  If not, there are other solutions to try.  In that case, please let me know which version of Ubuntu you're using.

---

### Post by chrome123 on 2009-03-13
I could see the little subsection under the network list before , I just can't see any.

[[IMG]http://img23.imageshack.us/img23/1926/screenshotdesktop.th.png[/IMG]](http://img23.imageshack.us/img23/1926/screenshotdesktop.png)

[[IMG]http://img13.imageshack.us/img13/4041/screenshotyrf.th.png[/IMG]](http://img13.imageshack.us/img13/4041/screenshotyrf.png)

And I know there are networks available in this location (ipod touch, good reception (ipod touch has the worst kind of reception, you have to hold it at a exact position and angle for it to have good reception)).

Also the 
```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```

didn't do anything :(

---

### Post by pytheas22 on 2009-03-13
At the top of this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970") there are two workarounds described.  Please give them a try and let me know if it helps.

Also, which version of Ubuntu are you using?  If you don't know, post the output of:
```

uname -rm
```

---

### Post by chrome123 on 2009-03-13
ubuntu 8.04

2.6.24-23-generic i686

---

### Post by pytheas22 on 2009-03-13
Did you try the workarounds described in the bug report that I linked to in my last post?  Did they work?

---

### Post by chrome123 on 2009-03-13
Nope, the thing is, the wifi isn't a switch, it's a button.

---

### Post by pytheas22 on 2009-03-13
Is there a way in BIOS to make the wireless be always on?  This might be the simplest solution, although there's other stuff to try if BIOS doesn't have an option regarding the wireless (but please check it, because it most likely does).

---

### Post by chrome123 on 2009-03-14
The only options where:

Wifi status on booting [off, last state]

It's now on last state.

---

### Post by pytheas22 on 2009-03-14
Sorry for not getting back to you sooner.

If you still have Windows on this laptop, please boot to it, enable the wireless, then shutdown with the wireless still on.  After the machine has shutdown, reboot into Ubuntu.  Does the wireless work now?  I'm hoping that the 'last state' option in BIOS means that if the wireless card was previously turned on in Windows, it will remain on when you boot to Ubuntu, even if Ubuntu can't control it itself.

Someone in the bug report also mentioned that after pressing the software key to turn the card on, he had to wait about thirty seconds before it actually kicked in.  Further, he wrote that if he pressed the wireless keys more than once, the card would not come on at all.  So please try pressing the keys one time to enable wireless, then wait a minute, and see if the 'sudo iwlist scan' command returns anything.

I'm also wondering if dmesg would contain any useful information.  Please try turning the wireless on, then run the following command and post its output:
```

dmesg | grep -i -e unknown -e radio -e iwl -e wlan
```

---

### Post by chrome123 on 2009-03-15
Only xp (didn't select the right drive during install :o.

pressing and waiting didn't help.

```
sven@Laptop:~$ dmesg | grep -i -e unknown -e radio -e iwl -e wlan
[   41.494086] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   41.494093] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   41.494295] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   41.589305] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   41.590904] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   46.638850] iwl3945: Radio disabled by HW RF Kill switch
[   48.467043] iwl3945: Radio disabled by HW RF Kill switch
[   62.518167] iwl3945: Radio disabled by HW RF Kill switch
[   79.631072] iwl3945: Radio disabled by HW RF Kill switch
[   89.148449] iwl3945: Radio disabled by HW RF Kill switch
[   93.891435] iwl3945: Radio disabled by HW RF Kill switch
[   99.235281] iwl3945: Radio disabled by HW RF Kill switch
[  106.193004] iwl3945: Radio disabled by HW RF Kill switch
[  108.447902] iwl3945: Radio disabled by HW RF Kill switch
sven@Laptop:~$ 
```
If I make a backup of linux now , install xp, then reinstall linux and "place" the backup, would that be exactly the same as linux is now, since I had set a lot of stuff.

---

### Post by pytheas22 on 2009-03-15
hmmm, it seems not to notice at all when you attempt to toggle the wireless on.  I'll keep googling on this (you can too, of course) and see if something else turns up, but I'm not positive that there will be an easier solution than installing Windows again, and then Ubuntu.
> 
If I make a backup of linux now , install xp, then reinstall linux and "place" the backup, would that be exactly the same as linux is now, since I had set a lot of stuff.

Depending on how you make a backup, yes, you should be able to put Linux back in its place with the desired results.  The easiest method would probably be to use [remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys") to make a custom live CD (or bootable USB drive if you prefer), then reinstall Ubuntu with it.  Another approach would be to use [partimage]("http://www.partimage.org/Main_Page") to ghost the Linux partition onto an external drive, then back onto the original drive, but this might be a bit more complicated than using remastersys.

Anyway, I'll keep googling for ways to force the wireless to come on.  If I haven't posted back in a few days, please post again to remind me.

---

### Post by ramjet_1953 on 2009-03-16
Try this, it worked for me:

Open a terminal and enter this command:

```
sudo nano /etc/modprobe.d/iw13945
```

Then add this line to the file:

```
options iw13945 led=1
```

Save the file and re-boot.

Now try pressing the wireless power button and see if things start-up.

[COLOR="Red"]NOTE:[/COLOR] If you don't have the nano editor installed use any editor you like in sudo mode.

Regards,
Roger :D

---

### Post by chrome123 on 2009-03-16
> **ramjet_1953 said:**
> ```
sudo nano /etc/modprobe.d/iw13945
```
```
options iw13945 led=1
```


that actually removed the option of wireless from the list :s

Also the /etc/modprobe.d/iwl3945 was empty.

After doing sudo lshw -C network; the wireless wasn't disabled, it was "unclaimed".

---

### Post by pytheas22 on 2009-03-16
Someone in [this thread]("http://ubuntuforums.org/showthread.php?t=820297&page=3") says that running this command solved the problem of iwl3945 radio not turning on:
```

sudo apt-get install linux-backports-modules-hardy-generic
```

I would give that a try.  You might also want to run this command to reverse the changes you made to the /etc/modprobe.d/iw13945 file, since they didn't work:
```

sudo rm /etc/modprobe.d/iw13945
```

Hopefully your card will be listed as claimed after that, and then, once you install the linux-backports-modules-hardy-generic package and reboot, the radio will finally turn on.

Also, I realized that the file you created before as per ramjet_1953's instructions was named 'iw13945', not 'iwl3945'--note the number '1' in place of the letter 'l', which doesn't make much sense, since the module's name is iwl3945.  This may have been the problem; you might want therefore to type 'sudo nano /etc/modprobe.d/iwl3945' and add the 'options iw13945 led=1' line to that file.

---

### Post by DebugLife on 2009-03-19
I have also this problem. 

Acer TravelMate 3000. WiFi: Intel Pro/Wireless 2200BG

Also the button does not work =(

---

### Post by pytheas22 on 2009-03-19
> I have also this problem.

Acer TravelMate 3000. WiFi: Intel Pro/Wireless 2200BG

Also the button does not work =(

If you boot to Windows, turn the wireless on, shutdown without turning it off and then boot to Ubuntu, does it work?  Do you have an option in BIOS to force the wireless to be always on?

---

### Post by DebugLife on 2009-03-20
It interesting way with Windows, but it doesn't work. BIOS always turn off Wi-Fi, and there is no option responsible for this (as well as other options =\).

---

### Post by pytheas22 on 2009-03-20
DebugLife: what's the output of:
```

cat /sys/bus/pci/drivers/ipw2200/*/rf_kill
```

---

### Post by fieroboom on 2009-03-20
From [launchpad](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/193970):

> WORKAROUND 1:

When killswitch is enabled (wifi off) nm-applet will disable the "[] enable wireless" menu entry.
After turning killswitch off (wifi on), the wifi status led is still off, and no access points are shown in network manager.
Right-clicking on nm-applet, you should see that the "[x] enable wireless" menu entry is now activated.
Disable it and then enable it again. This should bring up the status led and after some seconds all available networks.
No need to modprobe/rmmod in a terminal.

WORKAROUND 2 (If no #1 doesn't cut it for you):
for iwl3945:
]$ sudo rmmod iwl3945; sudo modprobe iwl3945
for iwl4965:
]$ sudo rmmod iwl4965; sudo modprobe iwl4965

And...

> I could find out that wireless will work if you just restart hal (sudo /etc/init.d/hal restart) after you've disabled the kill switch. You can enable/disable the kill switch then without restarting hal every time. I didn't check if it would be enough to restart hal right after booting (without disabling the kill switch first), but I will try this later.

Have you tried any of those methods?
:D
-Paul

EDIT:
Also found [this thread](http://ubuntuforums.org/showthread.php?t=820297&page=3), post #25:
> sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1

---

### Post by DebugLife on 2009-03-26
Thanks very much))) Some magic with rmmod, modprobe, hal restart and ipw2200 forces to work WiFi=) When button would work, it's will be really good!

---

