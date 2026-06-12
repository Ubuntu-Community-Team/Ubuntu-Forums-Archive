---
title: "Wireless &amp; Brightness  Problem Dell Inspiron 14R N4010"
date: 2011-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luckysanj on 2011-10-02
[B][SIZE=3]This is my second time post on ubuntu forum after i didn't get any solution. [/SIZE]
[/B]

[B][FONT=Courier New][B][SIZE=2]Brightness Problem Dell Inspiron 14R N4010 Problems
 Hey Guys,
 I freshly installed ubuntu-11.04-desktop-amd64, ubuntu-11.04-desktop-i386, ubuntu-10.04-desktop-amd64, ubuntu-10.04-desktop-i386 on my laptop Del Inspirion 14  N4010 but in my laptop there is Brightness control problem & wireless problem. I read all  of forum posted matter for brightness & wireless but it didn't work for my laptop. Brightness up down keys moves the brightness slider around but doesn't  change the actual brightness. I am also not able to change the brightness using the power management tool also.This problem is draining my battery life crazy.[/SIZE][/B][/FONT][/B]

**[B][FONT=Courier New][B][SIZE=2]So  now i am very sad about dell insprion N4010 model laptop. The model  comes after N4010 all are verified by ubuntu but why the ubuntu couldn't  verify dell N4010 model laptop why? I don't like windows platform but due to this problem i have to run windows on my laptop. :( [/SIZE]**[/FONT][/B][/B]

 [B][FONT=Courier New][B][SIZE=2]System Information
 Model: INSPIRON N4010
 Service Tag:97P3ZL1
 Express Service Code: 200-564-807-41
 CPU: i3 processor[/SIZE][/B][/FONT][/B]

More information about my Laptop:

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
 00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
 00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
 00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
 00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
 00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
 00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
 00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
 00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
 00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
 00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
 03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
 04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
 ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
 ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
 ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
 ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
 ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
 ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Help will be appreciated Thank you.

---

### Post by mörgæs on 2011-10-02
Normally I don't like this kind of answer, but in this case I actually think that it is worth a try:

Googling
**dell n4010 brightness site:ubuntuforums.org**
gives many pages of hits. Isn't there anything of value?

---

### Post by luckysanj on 2011-10-03
Sorry for that  what you think about my above post...I already wrote that i a have read all the things related with my problem on Ubuntu forum & many post i was got outside the ubuntu forum that also does not work for my laptop...... & my LAN driver is ok. but the main problem is Wireless & Brightness. 

So i saw the verified dell model on ubuntu so my confusion is that there was any problem on Dell Inspirion N4010 Hardware or any other reason was there for not verified Dell Inspirion N4010 model... 

Thanks.

---

### Post by Toz on 2011-10-03
As for brightness, have you tried kamal's kernel? Link: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")?

Reference links:
- [http://forums.linuxmint.com/viewtopic.php?f=49&t=70287]("http://forums.linuxmint.com/viewtopic.php?f=49&t=70287")
- [http://ubuntuforums.org/showpost.php?p=9836234&postcount=2]("http://ubuntuforums.org/showpost.php?p=9836234&postcount=2")
- [http://ubuntuforums.org/showthread.php?p=10017377#post10017377]("http://ubuntuforums.org/showthread.php?p=10017377#post10017377")

---

### Post by luckysanj on 2011-10-04
> **mörgæs said:**
> Normally I don't like this kind of answer, but in this case I actually think that it is worth a try:

Googling
**dell n4010 brightness site:ubuntuforums.org**
gives many pages of hits. Isn't there anything of value?
First of all thanks Dear Toz for your nice response, I have tried it very before many times but that times it wasn't work & now the  brightness problem is ok after following above link & it work but the other problem arise.....i can't able to update any package after install above link file. & i don't able to install any thing else on my laptop & when ever i will try to update the package the following error occur. i choose different location server but the same error shows me ....so what can i do know...is there any guideline for me ...


W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch cdrom://Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Thanks,

---

### Post by Toz on 2011-10-04
Open a terminal and run this command to get the keys again:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

Then again run:
```
sudo apt-get update
```

---

### Post by luckysanj on 2011-10-05
Thank you so much Dear Toz, It works great....but when every time i  restart the laptop the default brightness is high & i manually  manage the brightness with brightness button. How is it happen if any  ideas share with me otherwise it's ok...

And the main other problem on my laptop is wireless. it can't not work i  found one link on ubuntu forum in this  [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490) link with this  [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) driver. I install  on laptop & LAN is ok but the wireless not detected. So if any  guideline it will very helpful for me......

Thanks for your prompt response......

---

### Post by Toz on 2011-10-05
> **luckysanj said:**
> Thank you so much Dear Toz, It works great....but when every time i  restart the laptop the default brightness is high & i manually  manage the brightness with brightness button. How is it happen if any  ideas share with me otherwise it's ok...
Install the program **xbacklight**
Test to see if it works (xbacklight -set <value_as_percentage>), for example:
```
xbacklight -set 75
```
If it works, add the command to your **/etc/rc.local** file just above the line that reads **exit 0**. For example:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/bin/xbacklight -set 75
exit 0

```


> And the main other problem on my laptop is wireless. it can't not work i  found one link on ubuntu forum in this  [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490) link with this  [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) driver. I install  on laptop & LAN is ok but the wireless not detected. So if any  guideline it will very helpful for me......

Thanks for your prompt response......
First make sure that wireless isn't being blocked. Try:
```
sudo rfkill list
```
If it is being blocked, then:
```
sudo rfkill unblock all
```
If still no luck, look here: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

---

### Post by luckysanj on 2011-10-08
Dear Toz,

**I installed xbacklight** & set it with  xbacklight -set 75 but it doesn't affect any thing on laptop. & i keep it on **/etc/rc.local **& same thing happen no effect. 

About Wireless: Wireless isn't being blocked. I use to see for this 

root@planet:~# rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

& I follow this link from 2days [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/) but i am unable to solve.

Here is my Driver info:

root@planet:~# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:5f:cd:85
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:33 memory:f0400000-f043ffff ioport:2000(size=128)

OR MORE

root@planet:~# lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)



If any other guideline or way of doing plz suggest me..

---

### Post by Toz on 2011-10-08
> **luckysanj said:**
> Dear Toz,

**I installed xbacklight** & set it with  xbacklight -set 75 but it doesn't affect any thing on laptop. & i keep it on **/etc/rc.local **& same thing happen no effect.
Ok. What is the result of the following command after the brightness is as you like it?:
```
cat /sys/class/backlight/intel_backlight/acpi_video0/brightness
``` 

> About Wireless: Wireless isn't being blocked. I use to see for this 

root@planet:~# rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

& I follow this link from 2days [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/](http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/) but i am unable to solve.
How far did you get. What did you try?
1. Download the appropriate deb package.
2. Remove previous drivers (sudo apt-get remove bcmwl-kernel-source)
3. Install the driver you downloaded (sudo dpkg -i <file>)
4. Restart the computer (maybe twice)

> I freshly installed ubuntu-11.04-desktop-amd64, ubuntu-11.04-desktop-i386, ubuntu-10.04-desktop-amd64, ubuntu-10.04-desktop-i386 on my laptop Del Inspirion 14 N4010...
Which one are you currently running?
```
cat /etc/lsb-release
```
...and
```
uname -a
```

---

### Post by luckysanj on 2011-10-08
> **Toz said:**
> Ok. What is the result of the following command after the brightness is as you like it?:
```
cat /sys/class/backlight/intel_backlight/acpi_video0/brightness
```

There is not this above path on my laptop after install xbacklight.

These are list of file after install xbacklight on my laptop. 
```

root@planet:~# cat /sys/class/backlight/
dell_backlight/ i915/

root@planet:~# cat /sys/class/backlight/dell_backlight/
actual_brightness  bl_power           brightness         max_brightness     power/             subsystem/         uevent

root@planet:~# cat /sys/class/backlight/dell_backlight/
actual_brightness  bl_power           brightness         max_brightness     power/             subsystem/         uevent

root@planet:~# cat /sys/class/backlight/dell_backlight/actual_brightness 
.bash_history             .gconf/                   linux-kamal-mjgbacklight  .recently-used.xbel       
.bashrc                   .gconfd/                  .profile                  .ssh/                     
.config/                  .gnome2/                  .pulse/                   .synaptic/                
.dbus/                    .gnome2_private/          .pulse-cookie             .wapi/                    

root@planet:~# cat /sys/class/backlight/dell_backlight/bl_power 
.bash_history             .gconf/                   linux-kamal-mjgbacklight  .recently-used.xbel       
.bashrc                   .gconfd/                  .profile                  .ssh/                     
.config/                  .gnome2/                  .pulse/                   .synaptic/                
.dbus/                    .gnome2_private/          .pulse-cookie             .wapi/                    

root@planet:~# cat /sys/class/backlight/dell_backlight/brightness 
.bash_history             .gconf/                   linux-kamal-mjgbacklight  .recently-used.xbel       
.bashrc                   .gconfd/                  .profile                  .ssh/                     
.config/                  .gnome2/                  .pulse/                   .synaptic/                
.dbus/                    .gnome2_private/          .pulse-cookie             .wapi/                    

root@planet:~# cat /sys/class/backlight/dell_backlight/max_brightness 
.bash_history             .gconf/                   linux-kamal-mjgbacklight  .recently-used.xbel       
.bashrc                   .gconfd/                  .profile                  .ssh/                     
.config/                  .gnome2/                  .pulse/                   .synaptic/                
.dbus/                    .gnome2_private/          .pulse-cookie             .wapi/                    

root@planet:~# cat /sys/class/backlight/dell_backlight/power/wakeup 
.bash_history             .gconf/                   linux-kamal-mjgbacklight  .recently-used.xbel       
.bashrc                   .gconfd/                  .profile                  .ssh/                     
.config/                  .gnome2/                  .pulse/                   .synaptic/                
.dbus/                    .gnome2_private/          .pulse-cookie             .wapi/                    

root@planet:~# cat /sys/class/backlight/dell_backlight/subsystem/
dell_backlight/ i915/           

root@planet:~# cat /sys/class/backlight/dell_backlight/subsystem/dell_backlight/
actual_brightness  bl_power           brightness         max_brightness     power/             subsystem/         uevent

root@planet:~# cat /sys/class/backlight/dell_backlight/uevent 
.bash_history             .gconf/                   linux-kamal-mjgbacklight  .recently-used.xbel       
.bashrc                   .gconfd/                  .profile                  .ssh/                     
.config/                  .gnome2/                  .pulse/                   .synaptic/                
.dbus/                    .gnome2_private/          .pulse-cookie             .wapi/   

root@planet:~# cat /sys/class/backlight/i915/
actual_brightness  brightness         max_brightness     subsystem/         
bl_power           device/            power/             uevent      

```> How far did you get. What did you try?
1. Download the appropriate deb package.
2. Remove previous drivers (sudo apt-get remove bcmwl-kernel-source)
3. Install the driver you downloaded (sudo dpkg -i <file>)
4. Restart the computer (maybe twice) I have used this driver for my wireless and lan. If you have any other dirver link as our same model then plz forward me because i have not get any other suitable driver for my model so i used this because of this driver my LAN is working fine but wireless didn't. 
[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)
[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

Now my OS details is: 
```

root@planet:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

root@planet:~# uname -a
Linux planet 2.6.32-23-generic #38~kamal~i915bri~3e SMP Wed Jun 30 10:04:35 PDT 2010 x86_64 GNU/Linux

```

---

### Post by Toz on 2011-10-08
_Brightness:_
After you have the brightness at a comfortable level, post back the results of:
```
cat /sys/class/backlight/dell_backlight/brightness
```
(your previous cat replies don't make sense!!! - try this one) The result should be a value.

_Wireless:_
Looks like you're running the 64-bit version of Ubunbu 10.04. Follow the instructions at this link to get your wireless working: [http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

In a nutshell:
1. Download this file: [http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb")
2. Remove previous drivers:
```
sudo apt-get remove bcmwl-kernel-source
```
3. Install the file you downloaded:
```
sudo dpkg -i bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb
```
4. Reboot.
5. Maybe, reboot a second time (as per the article)

Note: if that doesn't work, there are 2 alternatives listed there.

---

### Post by luckysanj on 2011-10-11
After a long time because of [Toz,]("http://ubuntuforums.org/member.php?u=27546") proper guideline  i have solved my problem & now i am so happy :grin:. 

Now i have install Ubuntu 10.10 68 bit  It works perfectly with wireless & brightness.



And very very thankful to Toz.

---

### Post by Toz on 2011-10-13
> **Toz said:**
> _Brightness:_
After you have the brightness at a comfortable level, post back the results of:
```
cat /sys/class/backlight/dell_backlight/brightness
```
The result should be a value.
Can you please post back this result and we will add it to your /etc/rc.local file so it gets set at each boot.

---

### Post by luckysanj on 2011-10-14
Here is the result:

```

root@planet:~# cat /sys/class/backlight/dell_backlight/brightness
14

```

How i can add it to my /etc/rc.local file so it gets set at each boot.

---

### Post by Toz on 2011-10-14
Edit your /etc/rc.local file:
```
gksudo /etc/rc.local
```
...and before the "exit 0" statement, type in:
```
echo 14 > /sys/class/backlight/dell_backlight/brightness
```

The file should look something like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 14 > /sys/class/backlight/dell_backlight/brightness
exit 0

```

---

### Post by luckysanj on 2011-10-14
Sorry for above my post because the above code only show the output it does not effect with command prompt so now i properly check it & this below code affect brightness with command prompt.
```
echo 734 > /sys/class/backlight/intel_backlight/brightness
```So now I have make /etc/rc.local like this.
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 734 > /sys/class/backlight/intel_backlight/brightness
exit 0

```But it won't work when i again reboot laptop. Any more idea, what wrong with my code. it is better if it take effect from kernel level means first phase of starting pc.
And the file permission of brightness file is 
```

-rw-r--r-- 1 root root 4096 2011-10-14 22:41 brightness

```

---

### Post by Toz on 2011-10-14
In case its a path thing, try instead, the statement:
```
/bin/echo 734 > /sys/class/backlight/intel_backlight/brightness
```

---

### Post by luckysanj on 2011-10-15
> **Toz said:**
> In case its a path thing, try instead, the statement:
```
/bin/echo 734 > /sys/class/backlight/intel_backlight/brightness
```

Thank for you cooperation
Same result as like a above previous code. It effect  only when the system restart & its prompt for log on screen but when i log on with my username & password then it agian goes to high. 

Thanks.

---

### Post by Toz on 2011-10-16
Create a file in your home directory called .xprofile:
```
gksudo gedit ~/.xprofile
```
...with those contents:
```
/bin/echo 734 > /sys/class/backlight/intel_backlight/brightness
```
...save the file and make it executable:
```
chmod +x ~/.xprofile
```

And try again.

---

### Post by luckysanj on 2011-10-16
It won't works for me boss...my username is luckysanj so i create the file inside /home/luckysanj
with
```

luckysanj@planet:~$ vi .xprofile 
/bin/echo 734 > /sys/class/backlight/intel_backlight/brightness

```
```

root@planet:/home/luckysanj# chmod +x .xprofile 

```
Now,
```

root@planet:/home/luckysanj# ll
-rwxr-xr-x  1 luckysanj luckysanj     64 2011-10-16 16:36 .xprofile*

```
& I reastart, but it doesn't effect same result as usual.

Thank you.

---

### Post by Toz on 2011-10-16
Sorry, forgot the following. Add to your /etc/rc.local file, the following command before 'exit 0':
```
chmod 666 /sys/class/backlight/intel_backlight/brightness
```

Then .xprofile should work.

---

### Post by luckysanj on 2011-10-16
:oAfter doing your this i am not able to logon my screen cuz every time when i restart the pc the logon screen will be hang & after a second the system will also be hang.... :(

I think now i have only one choice to reinstall ubuntu OS with Ubuntu 11.4 with 32 bit.

---

### Post by Toz on 2011-10-17
This shouldn't affect the ability for your system to start. Can you start your computer in recovery mode and check your logs - specifically /var/log/syslog and /var/log/dmesg?

---

### Post by luckysanj on 2011-10-18
Sorry Boss, I have reinstall Ubuntu with 11.4 with 32 bit but in 32 bit same problem wireless & lan work fine but the brightness still same as above....
vi /etc/rc.local
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
chmod 666 /sys/class/backlight/intel_backlight/brightness
exit 0
~                    

```




Thanks.

---

### Post by Toz on 2011-10-18
If you type into a terminal the following command:
```
echo 734 > /sys/class/backlight/intel_backlight/brightness
```
...does the brightness change as you expect?

If not, do you get an error message?

---

### Post by luckysanj on 2011-10-18
> **Toz said:**
> If you type into a terminal the following command:
```
echo 734 > /sys/class/backlight/intel_backlight/brightness
```...does the brightness change as you expect?

If not, do you get an error message?

ya it does & I wont get any error but when i re-logon again the brightness will be same as usual. 


Now > Dear TCattitude suggest me to do  change brightness on Battery Properties. I just adjust the brightness in there, and it stay (there separated config for plugged in and on battery status) & it work great which i want.

So very thankful to you  and TCattitude, who help me to  find out the solution about this problem.

Thank you once again. 

:D

---

### Post by TheThakur on 2012-05-07
Hi,
    i am able to adjust the Brightness of the **Dell Inspiron 14R N4010**., but after the restarting of my Lapi Brightness setting again goes to 100% of its setting.

so again need to set the same.

so please help.....

Regards,
Shiv Rajawa

---

### Post by Toz on 2012-05-07
> **TheThakur said:**
> Hi,
    i am able to adjust the Brightness of the **Dell Inspiron 14R N4010**., but after the restarting of my Lapi Brightness setting again goes to 100% of its setting.

so again need to set the same.

so please help.....

Regards,
Shiv Rajawa
Can you please open a terminal window, execute the following commands, and post back the results?
```
cat /proc/cmdline
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

The first command will list your current kernel parameters, and the second will list the current and maximum brightness values for your existing backlight interfaces.

---

