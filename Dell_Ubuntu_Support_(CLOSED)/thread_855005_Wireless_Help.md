---
title: "Wireless Help"
date: 2008-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dmf2501 on 2008-07-10
Wireless Card:

Dell Wireless 1500 Draft 802. 11n WLAN Mini-card.

The Ubuntu terminal application detects the card, but for some reason can't detect wireless signals. I suspect that I'm missing the right driver. 

Can anyone help?

Edit: I have the latest version of ubuntu installed as an application.

---

### Post by falcon61102 on 2008-07-11
If you could, post thre results to:
```
lspci
```
and then type in and post the results of:
```
lshw -C network
```

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> If you could, post thre results to:
```
lspci
```
and then type in and post the results of:
```
lshw -C network
```

Results:

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)




00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

---

### Post by Kevbert on 2008-07-11
Please check out this [[COLOR="Red"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560") on how to configure your Broadcom BCM4328 Rev 01.

---

### Post by PinkFloyd102489 on 2008-07-11
That link is actually only half right. The link you're looking for is in that post.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)


Do these things:

```
sudo apt-get purge ndiswrapper-common ndiswrapper-utils-1.9 wpasupplicant && sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 wpasupplicant
```

That's just to clean out and make a fresh start.

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

```
Blacklist the native driver.


```
wget http://myspamb8.googlepages.com/R151517-pruned.zip
unzip R151517-pruned.zip
```
Fetch the drivers.

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```
Install the drivers.



If you do "lshw -C network" and it says "module=ssb" under the wireless, then do this.

```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy 
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```




I know this works, it's what I did on my Inspiron 1720 which has the bcm4328 rev 03 in it.

---

### Post by dmf2501 on 2008-07-11
Okay so apparently my installation of ubuntu can't find nidswrapper:

sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9

---

### Post by PinkFloyd102489 on 2008-07-11
Do "sudo apt-cache search ndiswrapper". I believe that's the correct command for the utils. Try enabling all repositories.

---

### Post by dmf2501 on 2008-07-11
dmf@dmf-laptop:~$ sudo apt-cache search ndiswrapper
[sudo] password for dmf: 
linux-ubuntu-modules-2.6.24-19-generic - Ubuntu supplied Linux modules for version 2.6.24 on x86/x86_64
dmf@dmf-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-utils-1.9
dmf@dmf-laptop:~$ 

still can't find it

---

### Post by falcon61102 on 2008-07-11
Ubuntu is looking in your CD to try to find it.  Make sure you either have the disc in your you have online access through wired with the repositories selected.  These options can be set through the Snyaptic Package Manager.

---

### Post by falcon61102 on 2008-07-11
And I made a typo on some earlier code.  Try this:
```
lshw -C Network
```
And post the results... it may save you some work in the long run.

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> And I made a typo on some earlier code.  Try this:
```
lshw -C Network
```
And post the results... it may save you some work in the long run.

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:76:11:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes


Also, I have ndiswrapper installed. What now?

---

### Post by PinkFloyd102489 on 2008-07-11
Run the commands in my previous post. Trust me, it works. Im posting from the laptop that I did it on. :p


> 
Do these things:

```
sudo apt-get purge ndiswrapper-common ndiswrapper-utils-1.9 wpasupplicant && sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 wpasupplicant
```

That's just to clean out and make a fresh start.

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

```
Blacklist the native driver.


```
wget http://myspamb8.googlepages.com/R151517-pruned.zip
unzip R151517-pruned.zip
```
Fetch the drivers.

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```
Install the drivers.



If you do "lshw -C network" and it says "module=ssb" under the wireless, then do this.

```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy 
sudo rmmod ssb
sudo rmmod ndiswrapper]
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

---

### Post by dmf2501 on 2008-07-11
Maybe I'm misunderstanding the code, but isn't [http://myspamb8.googlepages.com/R151517-pruned.zip](http://myspamb8.googlepages.com/R151517-pruned.zip) a url? If I can't get on the internet, how am I supposed to get something off of a website?

---

### Post by falcon61102 on 2008-07-11
Were you able to get ndiswrapper installed?

---

### Post by falcon61102 on 2008-07-11
> **PinkFloyd102489 said:**
> Run the commands in my previous post. Trust me, it works. Im posting from the laptop that I did it on. :p

The drivers are already installed for the device so about half these steps shouldn't be necessary.  If ndiswrapper is installed, all he needs to do is get rid of Module=ssb and load ndiswrapper which the second half of your code will do.

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> Were you able to get ndiswrapper installed?

Yes

---

### Post by falcon61102 on 2008-07-11
Check out this thread... I started posting on the top of page two.  Also there are further references about midway down on that page.

[http://ubuntuforums.org/showthread.php?t=851465&page=2](http://ubuntuforums.org/showthread.php?t=851465&page=2)

This will help you remove the Module ssb and replace it with ndiswrapper which will load your drivers.

Let me know if it works out or with any questions.

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> Check out this thread... I started posting on the top of page two.  Also there are further references about midway down on that page.

[http://ubuntuforums.org/showthread.php?t=851465&page=2](http://ubuntuforums.org/showthread.php?t=851465&page=2)

This will help you remove the Module ssb and replace it with ndiswrapper which will load your drivers.

Let me know if it works out or with any questions.

Okay, so in summary, I try this? :

sudo gedit /etc/modprobe.d/blacklist

sudo modprobe -r ssb

sudo modprobe ndiswrapper

sudo rmmod ssb

sudo modprobe ndiswrapper

gksudo gedit /etc/modules

---

### Post by falcon61102 on 2008-07-11
yeah... I'll explain what each line is doing:

You want to blacklist ssb
```
sudo gedit /etc/modprobe.d/blacklist
``` 

Type "blacklist ssb" in the last line and save the file... then close and proceed.  Format should look like the others in that file.  Don't worry about lines starting with #.

The stop the module ssb from running. 
```
sudo modprobe -r ssb
```

(you only use sudo rmmod ssb if sudo modprobe -r ssb doesn't work first.)
```
sudo rmmod ssb
```

Load the module ndiswrapper
```
sudo modprobe ndiswrapper
```

Make ndiswrapper load at startup
```
gksudo gedit /etc/modules 
``` 
Here again you're going to have to add a line to the file.  Simply add "ndiswrapper" to the last line, save and close.  Be sure not to include the quotes for both this and the blacklist file.

Sometimes with the modprobe -r command the module won't stop so you need to do the rmmod command.  If you don't receive an error after the modprobe -r you should be fine to continue.  If you receive an error, try the other one.

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> yeah... I'll explain what each line is doing:

You want to blacklist ssb
```
sudo gedit /etc/modprobe.d/blacklist
``` 

Type "blacklist ssb" in the last line and save the file... then close and proceed.  Format should look like the others in that file.  Don't worry about lines starting with #.

The stop the module ssb from running. 
```
sudo modprobe -r ssb
```

(you only use sudo rmmod ssb if sudo modprobe -r ssb doesn't work first.)
```
sudo rmmod ssb
```

Load the module ndiswrapper
```
sudo modprobe ndiswrapper
```

Make ndiswrapper load at startup
```
gksudo gedit /etc/modules 
``` 
Here again you're going to have to add a line to the file.  Simply add "ndiswrapper" to the last line, save and close.  Be sure not to include the quotes for both this and the blacklist file.

Sometimes with the modprobe -r command the module won't stop so you need to do the rmmod command.  If you don't receive an error after the modprobe -r you should be fine to continue.  If you receive an error, try the other one.

I blacklisted ssb, but still neither of those two commands work. For the modprobe one I get "FATAL:Ssb is in use" and for the other one I get "FATAL: SSB is being used by b44".

---

### Post by falcon61102 on 2008-07-11
Ok, go up to the post wher PinkFloyd has all those commands.  In the last set of code he posted, run the first four and then go to sudo modprobe ndiswrapper and continue from there where i left off.  If that works, you will also have to blacklist the bcm43xx series... add blacklist bcm43xx to that same file as the other one.

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> Ok, go up to the post wher PinkFloyd has all those commands.  In the last set of code he posted, run the first four and then go to sudo modprobe ndiswrapper and continue from there where i left off.  If that works, you will also have to blacklist the bcm43xx series... add blacklist bcm43xx to that same file as the other one.

Okay, all that's done. Now what? I still can't detect connections.

---

### Post by falcon61102 on 2008-07-11
Try a Restart.  If that doesn't work, run and post the output of:
lshw -C Network agian

---

### Post by falcon61102 on 2008-07-11
Also when you said that ndiswrapper was installed, did you at that time install the driver for your card?

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> Also when you said that ndiswrapper was installed, did you at that time install the driver for your card?

No, how do you install the driver?

---

### Post by PinkFloyd102489 on 2008-07-11
And you answer your question, an ethernet connection would be good.

---

### Post by dmf2501 on 2008-07-11
> **PinkFloyd102489 said:**
> And you answer your question, an ethernet connection would be good.

What do you mean? I'm dual booting ubuntu, and wireless works fine as long as I run windows. Are you talking about the pruned.zip file? Should I transfer that over to ubuntu using a flash drive?

For some reason I'm not longer able to save changes to the blacklist file.

---

### Post by falcon61102 on 2008-07-11
Download the driver in Windows.  Save it to a flash drive or to a shared space that you can get to in Ubuntu.  Then go to Ubuntu and install the driver using the steps PinkFloyd has written out... sorry, when you said you had ndiswrapper installed, i figured you installed the driver as well...

---

### Post by falcon61102 on 2008-07-11
Once you get into Ubuntu start where it says to unzip the drivers.  Also when you run ndiswrapper, make sure you are in the folder that contains those drivers just so it knows where to find them... then as PinkFloyd has written out use:

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

once you load the drivers, run
```
lshw -C Network
```
and you should see Module=(whatever driver name) and you should also be able to see your network access points at that time.

---

### Post by falcon61102 on 2008-07-11
PinkFloyd you see anything else I'm missing?

---

### Post by dmf2501 on 2008-07-11
Wait wait wait, so what exactly do I do after I unzip the file? All I did was extract the drivers in an untitled folder on desktop. When I try to run the code, it just says something like "bcmwl5.inf not found in line 219 of ndiswrapper" or something. Am I missing something obvious here?

---

### Post by falcon61102 on 2008-07-11
Yeah, you need to cd to that folder and run it from there or run sudo ndiswrapper -i ~/Desktop/Whatever/Driver.inf

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> Yeah, you need to cd to that folder and run it from there or run sudo ndiswrapper -i ~/Desktop/Whatever/Driver.inf

Are you sure that's the right format? I typed ndiswrapper -i ~/Desktop/untitled folder/bcmwl5.inf in terminal and all it gave me was instructions on how to use the ndiswrapper command.

---

### Post by falcon61102 on 2008-07-11
Well, I was just guessing where you had your driver, but yeah the base command is still sudo ndiswrapper -i (driver).  Try using cd (location) to navigate to the folder on your desktop and running it from there.  Either way, you just need to tell ndiswrapper where to locate and install your driver from.

---

### Post by dmf2501 on 2008-07-11
So 

cd ~/Desktop/untitled folder/bcmwl5.inf

Then

ndiswrapper -i ~/Desktop/untitled folder/bcmwl5.inf

?

---

### Post by falcon61102 on 2008-07-11
If you cd to it then you shouldn't need all the folder info but yeah, that looks about right... Just go:

cd ~/Desktop/untitled folder/

Don't put the file name on the end of that one...  when using cd you don't specify files, just folders.

---

### Post by dmf2501 on 2008-07-11
> **falcon61102 said:**
> If you cd to it then you shouldn't need all the folder info but yeah, that looks about right... Just go:

cd ~/Desktop/untitled folder/

Don't put the file name on the end of that one...  when using cd you don't specify files, just folders.

I got the wireless internet to work. Thank you both for helping me.

However, for some reason ubuntu can't seem to connect to my router if I use a WPA Personal encryption method, but I guess that'll be for another day.

---

### Post by falcon61102 on 2008-07-11
Not a problem, glad I could help... If you do a couple searches throughout the Forum you'll find some threads about using WEP and WPA security.

---

### Post by lunkupe on 2008-07-12
hii i also had the same issue with ma inspiron e1405.u need to run the updates.somewhere then after that go to system>administration>hardware drivers and it will work fine so give it a shot.if it does not work get back to me

---

### Post by falcon61102 on 2008-07-12
If you can't get online while in Ubuntu, it's kind of hard to run the updates.  Now that he can get online though, I'm sure that won't be a problem

---

### Post by PinkFloyd102489 on 2008-07-12
That's why you use a back up ethernet connection for working on it when wireless is down. Also, did you do the wpasupplicant stuff?

---

