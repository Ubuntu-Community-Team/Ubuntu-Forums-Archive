---
title: "Unable to install USB Bluetooth"
date: 2009-05-21
forum: General Help
---

### Post by Lockheed on 2009-05-21
I bought this bluetooth dongle: [http://www.amazon.com/Bluetooth-USB-Micro-Adapter-Dongle/dp/B001EBE1LI/ref=pd_cp_e_0_img/184-3601878-8278044?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-41&pf_rd_r=1XH7AJ7BYWY0H2N9AXF1&pf_rd_t=201&pf_rd_p=413863501&pf_rd_i=B000LZN7PE](http://www.amazon.com/Bluetooth-USB-Micro-Adapter-Dongle/dp/B001EBE1LI/ref=pd_cp_e_0_img/184-3601878-8278044?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-41&pf_rd_r=1XH7AJ7BYWY0H2N9AXF1&pf_rd_t=201&pf_rd_p=413863501&pf_rd_i=B000LZN7PE)

In XP everything is fine and dandy. Windows 7 detects the device but cannot install any drivers (no wiacomm, no bluesoleil, no windows drivers). 

In ubuntu, nothing happens after plugging it in. It supposed to be automatically detected, but it doesn't. Bluetooth icon never appears.

I know it's cheap but that's all I have and since it works in XP why wouldn't it work in Ubuntu? 
I'd appreciate any suggestions.

---

### Post by LowSky on 2009-05-21
plug it in, reboot, then run this command


```
lsusb
```

if its installed it will be there, just post the result and we will let you know

---

### Post by Lockheed on 2009-05-21
Here it the printout:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by Lockheed on 2009-05-22
Anyone?

---

### Post by Lockheed on 2009-05-23
I would really appreciate some help with that. Is there really no way to use it in Ubuntu??

---

### Post by fragos on 2009-05-23
The only device that is discovered is an RF dongle for a mouse. If you have a Logitech MX1000 wireless mouse that's what I see. If not your dongle is RF and not bluetooth. lsusb will show every connected USB device. try lsusb with the dongle plugged in and with it removed.

---

### Post by Lockheed on 2009-05-24
Some updates: I do have Logitech MX610 mouse and this is its wireless dongle.

Now, I have 3 USBs in my laptop. On in the top-right corner (where my mouse receiver sits in) and two in the left-bottom corner (where I tried plugging the BT dongle).

If I use one of the left ones for BT, it doen't get detected but they do detect my mouse receiver. If I plug the BT to the top-right corner, this is what I get:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 025: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 024: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

So it is being detected only by this top-right corner port BUT this USB port is excusively for mouse as any other location of the receiver is not really acceptible.

How do I go about enabling the other two USB ports to recognize the BT? They work wiht this BT in windows.

---

### Post by fragos on 2009-05-24
Where did you get the idea that a particular USB port was researved for the mouse? I doubt this is true. I have seen some high speed devices have problems with USB hubs, probably a power issue. Being a low speed device the mouse will easily work in an unpowered hub and certainly will in any direct port on your computer. You might try again with the laptop on AC power to see if that changes the situation. Very strange behavior indeed.

---

### Post by Lockheed on 2009-05-24
This is purely my idea that comes out of egrgonomics. Plugging  mouse receiver into any other USB port will be highly inconvenient for me and will hamper its reception.

So, can someone help me solve the problem of low power USB Bluetooth not being recognized on 2 out of 3 USB ports?

---

### Post by Lockheed on 2009-05-26
Bump

---

### Post by kmitnick on 2009-05-26
so when you connect the BT stick in place of the mouse reviever does the BT icon appears and works???
if so then the issue is about the usb only

---

### Post by Lockheed on 2009-05-26
No, the BT icon never comes up but that might be because I rearranged my taskbar and not it is on the bottom of the screen. However, all other tray icons work as they should.

Let me summarize:
1. BT dongle works in all USB ports in Windows XP.
2. In Ubuntu 9.04 x64 "lsusb" see the device only when plugged into the right top USB. In the two usb on the left side of the notebook USB dongle is not being detected. However, mouse receiver works just fine in all USB ports just as external USB disks and everything else.
3. BT icon doesn't appear even if I plug the BT dongle in the right USB socket. Also, even if I set the icon to appear always (not only when the device is connected) it does not show up.

---

### Post by fragos on 2009-05-26
I have no more help to offer. Although the question as originaly stated implies a different problem than you have. Consider restating your problem in a new post and you may get some help.

---

### Post by Lockheed on 2009-05-26
Alright, there is **development**!

It turned out that the USB dongle was poorly built. I reassembled it and not it's being detected in all USB ports.

So now the only problem is that Ubunto is not starting Bluetooth application or whatever it is it should start when Bluetooth is being connected. There is no tray icon.

---

### Post by fragos on 2009-05-27
Check System-> Administration-> Services to see if "Bluetooth device management" is there and checked. In Add/Remove Applications, search for bluetooth. You'll want "Bluetooth Analyzer" and "Bluetooth File Sharing" installed.

---

### Post by Lockheed on 2009-05-28
Thanks for the reply.
I had a look and everything you mentioned is checked.

---

### Post by fragos on 2009-05-28
You may have a dongle that uses a bluetooth chip set not supported by Linux. My dongle is a TRENDnet and it works well. Having had bluetooth working for years I haven't kept up on chip set compatability. You may be able to find some compatability tables with Google. All bluetooth functions between Ubuntu and my Nokia N810 work well with different and lesser levels of function with other devices like a Palm E2. There's a number of bluetooth protocols for different functions and some devices only support a subset.

---

### Post by Lockheed on 2009-05-28
```
ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```
I searched online if this devices is compatible with linux and indeed every entry I found says it is. 

I am at a loss...

---

### Post by fragos on 2009-05-28
It appears you're running a 64bit version, mine is 32bit. That may make a difference as the drivers for 32 and 64 bit are different. You could run Synaptic and do a full search on "blue". With few exceptions, like KDE vs Gnome, everything maked as distro supported with the small Ubuntu logo should be installed. Also open System-> Preferences-> Bluetooth and check the visibility setting and if there is "Friendly name". This is also a place to initiate the pairing of devices, aka "Known devices".

---

### Post by Lockheed on 2009-05-28
Well, I had everything with U installed. 
I went to Bluetooth and, just for the fun of it, tried pairing with my headset - and, what do ya know, it was detected and paired successfully.

But the bluetooth icon still is nowhere to be seen even though I have it set to "Always show".

Anyway, thanks for you help so far!

---

### Post by fragos on 2009-05-29
Always visible for bluetooth refers to the bluetooth radio and not the icon. Clearly your problem is not bluetooth but the display of the icon in the applet bar. Since you've only paired with a headset that icon serves no purpose as it provides access for sending and browsing files -- headsets don't have this feature.

---

### Post by Lockheed on 2009-05-31
Hmmm, I think it is something else.

System/Preferences/Bluetooth

Now, it says 
- "Never display icon"
- "Only display when adaptor present"
- "Always display icon"

Even if I select the last one, I never see any BT icon in my taskbar.

---

### Post by blissfulpenguin on 2009-06-01
mkay.  i've been following your thread.  i don't know much about BT Support on the backend, but the frontend is different.  It looks like when you selected "Always display" for the BT Icon, it should have showed up in your "notification area."  So, I guess the next step is ensuring that you have a notification area.  If you already have other icons showing up, like fusion-icon for example (normally i say pidgin here, but it's got some message docking thing now), then we need to look at other options, such as the backend, some of which  i can talk you through.

let's say you don't have a notification area.  right click the panel and add "notification area."  mkay if you already do, then open a root terminal and type:
```
/etc/init.d/bluetooth start

```
if this solves the problem, you need to look at System->Admin->Services->bluetooth (daemon?).  if there is no entry, you can add it manually, just ask we can churn out the instruction.

or better yet:
```
ps -e | grep bluetooth
```

that command should show you if a process with the string "bluetooth" is running.

if not, you may want to verify through synaptic that you have all the bluetooth installed that you want/need.

.':now, just for the sake of curiosity i would like to know when your problem is resolved, b/c i'm experiencing some backend issues:'.

thanks! and good luck!

p.s.  there's a screenshot of services dialog & lots of different packages for bt support in there.  like i said, don't know much, but hopefully the screenshots will prove worthwhile.

---

### Post by Lockheed on 2009-06-01
Thanks. I still did not solve the problem.

1. I have notification area and this is what sits there: Opera, uTorrent, WiFi, PulseAudio Volume, CheckGmail.
2. "/etc/init.d/bluetooth start" started just fine but did not fix anything
3. ```
~$ ps -e | grep bluetooth
 3615 ?        00:00:00 bluetoothd
```

---

### Post by mulluysavage on 2009-06-11
Hi everyone,

I also have a bluetooth dongle that checks out as "Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI Mode)" with lsusb. However, the software I am using to manage the dongle, Bluesoleil, returns "Bluetooth Hardware is not Found" when I try to turn on Bluetooth. Is there something else I can do to get it operating?

Ubuntu 8.04 LTS 

thanks

---

### Post by mulluysavage on 2009-06-11
Oh and I don't seem to have System>Preferences at all. Is there another way to access this dialog in 8.04?

---

### Post by mulluysavage on 2009-06-11
Now I've tried Blueman which does not recognize this dongle either.

---

### Post by Lockheed on 2009-06-12
Does your dongle get listed on the list of devices connected through USB?

---

### Post by mulluysavage on 2009-06-12
Yes when I run lsusb it is listed

---

### Post by fragos on 2009-06-12
Being listed in lsusb doesn't mean there is an appropriate driver for the bluetooth chip set in your dongle. I don't know if it's still this way but in the past not all chip sets were supported in Linux.

---

### Post by mulluysavage on 2009-06-12
I guess it's a possibility that this usb dongle is not supported in linux, what led me to believe that it is is that the software that came with it is Bluesoleil for Windows, and when I went to the web site they specifically had software for ubuntu 8.04, which I'm running, and which also does not recognize the dongle.

---

### Post by mulluysavage on 2009-06-12
I have found other indications that this chipset is supported: 

[http://ubuntuforums.org/showthread.php?t=1149443&highlight=cambridge+silicon+radio](http://ubuntuforums.org/showthread.php?t=1149443&highlight=cambridge+silicon+radio)

I have also followed the instructions in this thread to disable HCI mode to no avail.

---

### Post by mulluysavage on 2009-06-12
How about if I run the Bluez applet? Will that help me? Will I then have access to configuration controls? I can't seem to figure out how to do that.

---

### Post by Lockheed on 2009-06-13
Well, the chipset is supported as I found out online and, besides, my dongle works. The problem is it is somewhat useless because it is nearly impossible in liunux to use it with bluetooth headset.

---

### Post by fragos on 2009-06-13
Install bluez-btsco for headset support. Works with my Plantronics headset.

---

### Post by t4thfavor on 2009-06-19
Same chip, same issue, All I had to do to get it working again was go into system -> administration -> services and unckech/recheck the bluetooth item. I didn't even have to restart, as the blue light started blinking almost immediatly.


uname -a
Linux AMD64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

lsusb
Bus 003 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


Just pm me with a link to this thread, and a question (if you have any), and I will make sure it gets posted back here.

---

### Post by Lockheed on 2009-06-22
> **fragos said:**
> Install bluez-btsco for headset support. Works with my Plantronics headset.

I installed it but what do I do next? I cannot find it in the menus.

---

### Post by fragos on 2009-06-22
There won't be anything in the menues. Just pair your headset and it's protocol will be recognized by the bluetooth driver. There's nothing to configure.

---

### Post by Lockheed on 2009-06-22
Right. So how do I set it for use with Skype or as general in/out audio device?

---

### Post by fragos on 2009-06-22
The N810 checks for what's available and should use bluetooth if the headset is on and networking on the tablet selected.

---

### Post by Lockheed on 2009-06-22
No, no. I mean, how do I set the bluetooth headset to cooperate with Ubuntu in appliances like Skype?

---

### Post by fragos on 2009-06-22
Excuse me. Start Skype-> <Ctrl>O-> Sound Devices

---

### Post by Lockheed on 2009-06-22
Yes, I am aware of this menu but none of the options there makes my BT work.

---

### Post by t4thfavor on 2009-06-26
mulluysavage said,

"Hi you were helping me on this thread:


[http://ubuntuforums.org/showthread.php?t=1166376&page=4](http://ubuntuforums.org/showthread.php?t=1166376&page=4)

I don't seem to have a
system -> administration -> services
What can I do?

also now I am trying to get it to work with a different dongle see below

uname -a
2.6.24-24-generic #1 SMP Wed Apr 15 15:54:25 UTC 2009 i686 GNU/Linux

Bus 004 Device 002: ID 19ff:0309
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 003: ID 05ac:0306 Apple Computer, Inc. Apple Optical USB Mouse [Fujitsu]
Bus 001 Device 001: ID 0000:0000"



run gksu services-admin from the commandline, and then start the bluetooth service. I found your thread because I had the same dongle. It now works flawlessly. 

Again, my kernel
Linux AMD64 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux

My dongle
Bus 003 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

All I did was reenable the bluetooth service. If you need anymore info, please feel free to ask me.

---

### Post by fragos on 2009-06-26
I don't seem to have a
system -> administration -> services
What can I do?
------------------------------------
right click Applications and select Edit Menus to insure that the box for services is checked.

---

### Post by t4thfavor on 2009-06-26
Or run gksu services-admin from a commandline...

---

### Post by fragos on 2009-06-26
IMHO, gksudo is a better choice.

---

### Post by gerkin on 2009-06-26
I have the same bluetooth dongle and can report all the same problems in Jaunty

Bus 003 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

It works perfectly on my Eeepc900 running Intrpid based Crunchbang but as yet I have not been able to get it to work on Jaunty despite trying every posted "fix" I could find in the forums & googling

I'll post a solution if I find it

gerkin

---

### Post by mulluysavage on 2009-06-27
> **fragos said:**
> I don't seem to have a
system -> administration -> services
What can I do?
------------------------------------
right click Applications and select Edit Menus to insure that the box for services is checked.

I don't have this option in the Edit Menus dialog - I think all of this is because i'm running xcfe4

---

### Post by mulluysavage on 2009-06-27
> **t4thfavor said:**
> Or run gksu services-admin from a commandline...

any idea why running services-admin from both gksu and gksudo result in all greyed-out options with no way to select any services and deal with them? I tried sudo as well same result

---

### Post by gerkin on 2009-07-01
I have 2 of theses dongles with the same chip and I have found that they work perfectly in Intrepid and Crunchbang (Intrepid based) - including a fresh Crunchbang install on my Eeepc 900 yesterday to confirm this still the case

I have been unabel to get them to work on Jaunty or LinuxMint 7 (jauntybased) as yet

I understand from googling and various forums that there has been some changes in the bluetooth stack

I'm still trying to find a fix so I can update to Jaunty etc.


cheers................gerkin

---

### Post by pbitreras on 2010-01-11
i try with this module: **btusb**
This work for me.


BR,

---

