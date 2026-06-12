---
title: "Help Setting up Wireless on ubuntu 8.10"
date: 2009-04-14
forum: General Help
---

### Post by sb360 on 2009-04-14
Hey, I am very new to linux, ubuntu and this forum.
I am using a HP pavilion DV5 1111ea If my memory serves me correctly and I have no idea where to start with setting up the wireless. I have set up a dual boot system with vista and ubuntu 8.10 (I think). After some searching I have done this, as was suggested in another thread. 

> sam@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
sam@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

sam@ubuntu:~$ 




Thanks in advance for any help and sorry that I am totally useless when it comes to linux, hopefully I will get on top of it as so far I really like the feel and performance Ubuntu is giving me.

Edit: Sorry I noticed afterwards that this should have gone in networking and wireless section. Is it possible to move this thread ?

---

### Post by RedSingularity on 2009-04-14
Is it a USB wireless adapter?

---

### Post by sb360 on 2009-04-14
No its a built in card, Only a 4 month old laptop.

---

### Post by RedSingularity on 2009-04-14
Ohh ok post the output of ifconfig.

---

### Post by RedSingularity on 2009-04-14
And go [HERE](http://sourceforge.net/projects/madwifi/) and download the madwifi drivers.  Unzip them to your desktop and tell me the name of the unziped folder when its put on your desktop.

---

### Post by sb360 on 2009-04-14
Ifconfig gave me this : > sam@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:2f:ac:d0  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe2f:acd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109220911 (109.2 MB)  TX bytes:4175890 (4.1 MB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:428 (428.0 B)  TX bytes:428 (428.0 B)

sam@ubuntu:~$ 




And do I need madwifi drivers, there was a free driver update called "Support for Atheros 802.11 wireless LAN cards" That I installed when I first installed Ubuntu

---

### Post by RedSingularity on 2009-04-14
Oh good than keep that.

Are you connected via a wire right now?

---

### Post by sb360 on 2009-04-15
Yea i'm just connected directly to the router at the moment.

---

### Post by RedSingularity on 2009-04-15
Did you already check System>Admin>Hardware drivers?  

PS:  Did you download that package i put in the link?

---

### Post by sb360 on 2009-04-15
Yea I have installed drivers from system>admin>hardware-drivers so I didnt get the one you linked to. Will I need those as well ?

---

### Post by RedSingularity on 2009-04-15
Yea.  Only if the ones you activated in Hardware Drivers dont allow you to get a wireless connection going.  Doesnt look like those did the job so download the other package and extract the contents to the desktop.

---

### Post by sb360 on 2009-04-21
Ok I have downloaded those and extracted to desktop, what should I do now.

---

### Post by blueturtl on 2009-04-21
Not meaning to hijack your thread, but many notebook/laptop computers actually have internal USB buses too, so your wireless adapter could in fact be USB even though it's "integrated".

I recommend checking the output of 'lsusb' to see if your card appears there instead.

Also, optionally you could check [these alternate instructions]("http://linuxwireless.org/en/users/Download") for updating your wireless modules in Ubuntu.

Works wonderfully, and doesn't mess up any currently working drivers/configuration.

edit: Sorry Shadow121 for stepping on your toes.

---

### Post by sb360 on 2009-04-21
Nothing appearing on my lsusb output that looks like a wireless card, I'l try your instructions now, Thankyou for the reply.

---

### Post by RedSingularity on 2009-04-21
> **blueturtl said:**
> 
edit: Sorry Shadow121 for stepping on your toes.


Oh feel free to jump in any time i dont mind :)

---

### Post by RedSingularity on 2009-04-21
Looks like its an atheros driver.  The Madwifi should take care of that.

Do do you still have a madwifi folder on the desktop?

---

### Post by sb360 on 2009-04-21
Yep I still have the folder

---

### Post by RedSingularity on 2009-04-21
In the terminal type "cd /home/user name/Desktop/name of the madwifi folder"

Then type ./configure
Then make
Then sudo make install

Tell me if you get errors in the "make" part.

---

### Post by sb360 on 2009-04-21
Its saying no such file or directory after the first part, I tried doing it without the madwifi folder but same thing again.

---

### Post by prem1er on 2009-04-21
Don't just copy and paste the command there are parts where you have to add what is on your machine.  You have to enter your user name where it says '/user name/'.

---

### Post by sb360 on 2009-04-21
Yea ive done all that, changed the username for the correct user name and correct file name.

---

### Post by prem1er on 2009-04-21
Do you know how to use 'tab complete'?  Start typing the location you are trying to get to and hit the tab key it should fill in the correct location if you are spelling things incorrectly.

---

### Post by sb360 on 2009-04-21
Ok I got the first part working, I was missing the space after cd.
now I can't get the ./configure bit to do anything.

Sorry im useless as this.

---

### Post by prem1er on 2009-04-21
What do you mean you can't get it to do anything?  Is there an error or is there just no output after you hit enter?

---

### Post by sb360 on 2009-04-21
Its the no such file or directory one again.

---

### Post by prem1er on 2009-04-21
Is the file still a .tar file? Or have you untared it already? Do this for me.

cd /home/user name/Desktop
and post the results of

ls -lrt

---

### Post by sb360 on 2009-04-21
I dont think it is a tar anymore, This is what I get when I do the above 


drwxr-xr-x 14 sam sam 4096 2008-02-13 05:14 Madwifi
-rw-r--r--  1 sam sam 2707 2008-10-09 17:00 ccsm.desktop
drwxr-xr-x  8 sam sam 4096 2009-03-31 13:02 Phun

---

### Post by prem1er on 2009-04-21
Do.

```
cd Madwifi
```

then,

```
make
```

then,

```
make install
```

---

### Post by sb360 on 2009-04-21
Ok thats all done, but im still not  getting a wireless connection, Are there setup procedures I need to go through ?

---

### Post by RedSingularity on 2009-04-21
Did the make install work?  Did you get a completion?

---

### Post by sb360 on 2009-04-21
Yea Ive got it installed, all seemed to go fine.

---

### Post by RedSingularity on 2009-04-21
Restarted the computer and looked under Hardware Drivers?

Oh and post ifconfig again so we can see if there are any packets being moved.

---

### Post by sb360 on 2009-04-22
The hardware drivers dont seem to have changed :s 

and ifconfig says this : 

eth0      Link encap:Ethernet  HWaddr 00:23:8b:2f:ac:d0  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe2f:acd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:635756 (635.7 KB)  TX bytes:66044 (66.0 KB)
          Interrupt:250 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8056 (8.0 KB)  TX bytes:8056 (8.0 KB)

---

### Post by RedSingularity on 2009-04-22
Wow i see no other drivers for your card.  MadWifi was the closest thing to it.  You should file a bug report on that card.  The people there may fix it for you or (If they cant) add the driver to future distributions of ubuntu.

---

### Post by nothingspecial on 2009-04-22
You`ve got to load the driver

```
sudo modprobe ath_pci
``` for a session

or

```
gksudo gedit /etc/modules
```

add ```
ath_pci
``` to the end of the file

save close reboot

And your wireless driver will load everytime you boot your laptop

---

### Post by sb360 on 2009-04-22
Right I did the last one and rebooted. Still dont get anything from the ping test wirelessly.

---

### Post by Saint_ on 2009-04-22
Alright, I've been following this thread (and looking at countless others), I've also followed all the steps, etc (and other tutorials) and I'm having the exact same problem as sb360. I've been holding off on actually making a post, figured I could get it figured on my own lol, but **** was I wrong. I'm returning all the same values and errors as sb360 as well, our problem is identical. So, figured I'd throw my 2 cents in, you aren't alone bro!

Edit: Though, I've seen people posting success stories as well, so suffice to say I'm a tad bit confused. Btw might as well add in some tech specs here: 

Dual booting ubuntu/windows 7
AMD Turion(tm) X2 Ultra Dual-Core 2.1ghz
4 gigs of RAM
Radeon HD 3200 Graphics

---

### Post by nothingspecial on 2009-04-23
Ok as I can't tell how the madwifi process has gone we`re going to try a different route.

First go to system > administration > hardware drivers and disable anything related to wireless and atheros in there.

Then ```
sudo apt-get install linux-backports-intrepid-generic
```

Now go back to /etc/modules

```
gksudo gedit /etc/modules
```

Either remove ```
ath_pci
``` from the file or put a # infront of it.

Then add ```
ath5k
``` to the end of the file.

Save, close, reboot.

This will change the driver you are using. You should now have wireless. If you don`t post back and try to give any information as to what you have done apart from these 2 processes to get your wireless working. If you have followed other tutorials there may be some conflicts. Nothing we can`t get over though.

---

### Post by sb360 on 2009-04-23
Thanks for all the help, Im not at my laptop now but I will try it as soon as possible and update soon.

@ saint  glad to know its not just me, hopefully we will both get it sorted soon.

---

### Post by Saint_ on 2009-04-23
Yo Nothing, thanks for the reply bro. Alright so when I entered ```
sudo apt-get install linux-backports-intrepid-generic
```

My konsole returned 

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-intrepid-generic

So I'm not sure what's up with that.

---

### Post by RedSingularity on 2009-04-23
Here try this command  

sudo apt-get install linux-backports-modules-intrepid

---

### Post by nothingspecial on 2009-04-23
Edit ******[COLOR="Red"]Hey try shadows post above before this[/COLOR]

Ok seems the package has changed since I last did this.

First do ```
uname -a
```

that`s uname not unname only one n (common mistake;))
to check which kernel version you have. It should return something like this
```

Linux saint-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux
```

It`s the 2.6.27-11 number that we`re interested in. It might say 2.6.27-9 or 2.6.27-7.

Then type sudo apt-get install 
```
linux-backports-modules-2.6.27-11-generic 
``` changing the number for your kernel if you need to.

Then carry on.

---

### Post by Saint_ on 2009-04-23
K, Shadow this is what my konsole returned when I entered the command you posted:

saint@saint:~$ sudo apt-get install linux-backports-modules-intrepid
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-backports-modules-intrepid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

And Nothing, when I followed your instructions, this is what I got:

saint@saint:~$ uname -a
Linux saint 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux
ssaint@saint:~$ sudo apt-get install linux-backports-modules-2.6.27-11-generic
[sudo] password for saint:
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-backports-modules-2.6.27-11-generic is already the newest version.
linux-backports-modules-2.6.27-11-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

So, i'm not sure if that intrepid "1 not upgraded" is for the new Jaunty update or what (pure speculation).

---

### Post by nothingspecial on 2009-04-23
Does it work if you add the ath5k driver to /etc/modules as in my previous post?

---

### Post by Saint_ on 2009-04-23
No, just rebooted to try to test it, and it's still not picking up any wireless signals. So far, what I've done was follow the steps @ [http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo) and I've also tried some different things I've found around the forums here. I'm also using Wicd, I don't know if that would conflict with any other drivers trying to act, etc. But hey I've got to head off to school for a few hours, so I'll catch up on this when i get back. thanks again for all the help, its much appreciated.

---

### Post by nothingspecial on 2009-04-23
Ah wicd.              Excuse me but im posting on my cell phone.         Somewhere in wicd s preferences, you have to specify the device as wlan0.  If you cant figure out where, ill be home in 30 mins. I can Post normally then. Cheers.

---

### Post by nothingspecial on 2009-04-23
Sorry about my previous post. Didn`t see the bit about school,just read up to wicd and thought that might be it. I didn`t realize you`d be away for a few hours. Anyway ....

Click on the wicd icon in your panel, choose preferences. Where it says "wireless interface" (second one down) type wlan0.

If that doesn`t fix it we`ll have to try something else tommorow (where I am)

I`ll be asleep by the time schools out.

Hope that does it.

---

### Post by Saint_ on 2009-04-23
It's all good man. Alright, so here we encounter yet another problem, wlan0 isn't anywhere to be found. ```
ifconfig
``` returns the following: 

eth0      Link encap:Ethernet  HWaddr 00:1e:68:89:99:3d  
          inet addr:192.168.0.67  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe89:993d/64 Scope:Link             
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1             
          RX packets:580 errors:0 dropped:1816606522 overruns:0 frame:0  
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:255871 (255.8 KB)  TX bytes:27990 (27.9 KB)
          Interrupt:252

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1700 (1.7 KB)  TX bytes:1700 (1.7 KB)

And that's it. And i've also gone about trying to install the madwifi drivers, etc. but encounter module problems while using the command make. At one point I do believe I got it installed, but the end effect didn't really seem to do anything.

Edit: LOL thank god i re-read your post. I put wlan0 as the wireless interface and Wicd is now picking up and connecting to wireless networks (WHOOT!). But my network is secured via WEP and when i enter the network key, it tries connecting but gets hung on "Obtaining IP". but damn man, thanks for everything, you're a scholar of linux. Ive been trying to get this working for like 3 days now lol, was starting to lose hope.

Edit2: Ok, now it wont even get to 'obtaining ip' it just says "putting interface down" and kinda...stops

---

### Post by sb360 on 2009-04-23
I got mine working, I used sudo apt-get install wicd and then it seemed to work fine for me. I also upgraded to jaunty jakolope before doing this and now its working.

---

### Post by Saint_ on 2009-04-23
Ah, very nice man. Yeah mines working great except this whole unable to obtain the ip of my network deal, but i'll get it sorted one way or another. Thanks for all the help, everyone who posted on this thread, good ****.

---

### Post by sb360 on 2009-04-23
Actually its not working and im just a tard, It said connected but was still the wired connection, Just me being stupid. But at least my laptop is picking up my wireless connection now. I think the main problem is the fact that my router is hardwired with stupid settings thanks to o2. So i might swap back to the old router and see if that works.

---

### Post by Saint_ on 2009-04-23
Haha, it's all good man it happens to all of us. Are you using wicd? If so, what happens when you try connecting to a wireless network?

---

### Post by sb360 on 2009-04-23
same as you, gets to the Ip bit and then just gives up and says not connected.

---

### Post by Saint_ on 2009-04-23
Hm, yeah...hopefully someone can hit us with an answer to that one soon.

---

### Post by sb360 on 2009-04-23
Yea I think I can probably get it sorted with a new router, but maybe if your having the same problem, that alone wont fix it, Il have to play with it tomorow

---

### Post by Saint_ on 2009-04-23
Yeah tbh I think it's just a problem with wicd, because I can connect to any unsecured network I'm around, it's just the secured ones where it gets hung up on 'obtaining ip'

---

### Post by Saint_ on 2009-04-23
Yo! Just connected to an encrypted wireless network (finally..). sb360, what you gotta do is fool around with a _combination_ of your encryption types (which are located under the connection you're trying to connect to) i.e. WEP (Hex), WEP (Passphrase), WPA 1/2 (Passphrase), etc **AND** your WPA Supplicant Driver (Located: Wicd > Preferences). The combination that worked for me was: 
WPA Supplicant Driver - Wext  
Encryption type - WEP (Hex)

So, that's how I got it working. Thanks to everyone who posted in this thread, without your advice I would still be stuck in the living room wired to the router. sb360, hope this helps you man, good luck to ya.

PEACE!

---

