---
title: "Can't get bluetooth working for 7 months now on inspiron 1525....please help."
date: 2010-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hcamelion on 2010-12-26
I cant get bluetooth to work in Lucid on my inspiron 1525.  I am pretty sure that the bluetooth is on in the bios and windows has not disabled it (or i re-enabled it already).  I am specifically concerned why it seems to be showing up as a usb hub with lsusb.

I have done everything I could find in the forums and google to try and fix this including running the dell patch.  Bluetooth light is not on.

Does anyone know what my issue may be?

output of: sudo dellWirelessCtl --i
```
Libsmbios version : 2.2.13
smbios-wireless-ctl version : 2.2.13
Wireless Info:
    Hardware switch supported
    Hardware switch is On
    WiFi Locator supported
    Wireless Keyboard not supported
    NVRAM Size: 256 bytes
    NVRAM format version: 1

Radio Status for WLAN:
    WLAN enabled at boot
    WLAN supported
    WLAN enabled
    WLAN installed
    WLAN controlled by wireless switch at boot
    WLAN runtime switch control currently enabled
    Status Code: 0

Radio Status for Bluetooth:
    Bluetooth enabled at boot
    Bluetooth supported
    Bluetooth enabled
    Bluetooth installed
    Bluetooth not controlled by wireless switch at boot
    Bluetooth runtime switch control currently disabled
    Status Code: 0

Radio Status for WWAN:
    WWAN enabled at boot
    WWAN supported
    WWAN enabled
    WWAN not installed
    WWAN controlled by wireless switch at boot
    WWAN runtime switch control currently enabled
    Status Code: 2

Wireless Switch Configuration
    WLAN switch control: on
    Bluetooth switch control: off
    WWAN switch control: on
    switch config: not locked
    WiFi locator: enabled
    WiFi Locator config: not locked
```Output of: lsusb
```
Bus 007 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
References:
[http://ubuntuforums.org/showthread.php?t=553151](http://ubuntuforums.org/showthread.php?t=553151)
[http://lists.us.dell.com/pipermail/linux-desktops/2007-March/000260.html](http://lists.us.dell.com/pipermail/linux-desktops/2007-March/000260.html)
[http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714](http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R159805&formatcnt=1&libid=0&fileid=213714)

---

### Post by Ichido on 2011-01-03
I have the Dell 1525 running Ubuntu 10.4.
I wondered recently why I couldn't use my laptop's Bluetooth.  
I went to dell.com and looked up my laptop by it's "Service Tag" and found I do not have a Bluetooth adapter installed even though I do have a Bluetooth LED.
So now I'm looking for a Bluetooth "Dongle" that I can use.

---

### Post by TheHackOps on 2011-01-04
Ichido, Lol that just enforces my belief that dell is handing out false hope :)

---

### Post by hcamelion on 2011-01-06
Hey,

Thanks for the response...not sure if it helps my issue.  I know I have an internal bluetooth installed because it was working right before I switched from windows.

---

### Post by Xanko on 2011-02-11
Finally got the bluetooth on my system working. (Inspirion 1525 with Dell 355 Bluetooth).

First, make sure your bluetooth is enabled in the bios. And then I turned off the bios setting that makes the switch on the right hand side of the laptop from controlling wifi/bluetooh on/off.

Next, I had to boot into windows and follow these instructions.

[http://en.kioskea.net/forum/affich-45863-bluetooth-not-working-in-dell-inspiron-1525]("http://en.kioskea.net/forum/affich-45863-bluetooth-not-working-in-dell-inspiron-1525")
> a. Download the driver at Dell.com: 
- 1. Go to [http://www.dell.com.br](http://www.dell.com.br) 
- 2. Click on the link "Drivers & Downloads" in the end of the site. 
- 3. Select your model ("Laptops", "Inspiron Laptop", "1525") and confirm it. 
- 4. Click on Network. 
- 5. Download the "Wireless 355 Bluetooth Module (Bluetooth 2.0 + EDR)" 
- 6. Save the file "R140135.exe". 

b. Install the driver: 
- 1. Execute the file "R140135.exe". 
- 2. Open the folder "C:\dell\drivers\R140135\3100_216". 
- 3. Execute the file "Setup.exe". 
- 4. When the driver ask you to active your Bluetooth antena, click in "Cancel. 
- 5. Open the folder "C:\dell\drivers\R140135\3100_216\Win32" 
- 6. Execute the file "Inst.exe". 
- 7. Click in "Next" button to begin the installation. 

Note: When the software ask you to active the Bluetooth DO NOT CANCEL. 

- 8. Open the folder "C:\Program Files\WIDCOMM\Bluetooth Software" 
- 9. Execute the file "BTTray.exe". The icon will appear in the system tray (next the clock). 
- 10. Click with the right button in Bluetooth icon and turn it on. 
- 11. The installation will continue automatically. 
- 12. Click in "OK" button to finish 

That is how I solve my problem with my Dell Inspiron 1525 runing Windows 7. It's working perfectly. 


I hope it help you guys.

I had the problem where after installing the bluetooth software I still had no way of enabling the bluetooth (no light) until I manually started bttray.exe and I could enable bluetooth that way. Now the bluetooth is on (and don't ever stop it!).

Booted back into Ubuntu and now I have bluetooth connectivity... Works great for grinding Gran Turismo 5 via sixemu.

---

### Post by oleink on 2013-01-09
> **TheHackOps said:**
> Ichido, Lol that just enforces my belief that dell is handing out false hope :)

Dell is crap unless you're buying their crap used knowing what youre getting is crap and you are installing linux on it to make it less CRAP lol

---

### Post by hcamelion on 2013-01-09
Yes,  I finally moved to a system76 computer as of a few days ago.

---

