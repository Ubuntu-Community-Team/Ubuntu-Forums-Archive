---
title: "Bluetooth problems with Inspiron 6400"
date: 2007-09-17
forum: Dell  Ubuntu Support
---

### Post by Kave N on 2007-09-17
Hello!

I'm experiencing problems with finding the bluetooth-device. I've tried to communicate with it both in KDE and Gnome-interface. It still doesn't work. When I  press the Fn and F2 button nothing happens.  I've tried to restart the bluetooth-device to and this is the message I get. 

> kave@kave-laptop:~$ hciconfig hciX reset
Can't get device info: No such device


Thankful for help.

Kave

---

### Post by Linicks on 2007-09-17
I presume bluetooth is ON in bios?  I turned it off, but I guess that could be set off as default.

Nick

---

### Post by sr20ve on 2007-09-17
removed

---

### Post by 6tangos on 2007-09-29
Hi,
I recently purchased a Dell Inspiron 6400 with Ubuntu pre-loaded, everything is great except the Bluetooth - the system doesn't find the device, 
it would appear that I'm having the similar problems to Kave N.

When doing, 
hciconfig reset
message "Can't get device info: No such device"

Bluetooth is enabled within the Bios
There is no apparent hot key combonation to turn Bluetooth on...
(Fn + F2 enables/disables WiFi card)
The Bluetooth LED is NOT lit

Any help would be much appreciated!

Thanks

---

### Post by Mavtech on 2007-09-29
I have a Dell E1505 with the internal Dell 355 Bluetooth.  The directions in the below thread got my Logitech V270 working perfectly.

[http://ubuntuforums.org/showthread.php?t=468467&highlight=Logitech+v270](http://ubuntuforums.org/showthread.php?t=468467&highlight=Logitech+v270)

---

### Post by Arne_M on 2007-10-01
same problem inspiron 6400 with feisty. It seems to be a general bug.
bluetooth is definetly enabled in the bios. And I believe to have seen the Bluetooth LED light when using windows (before I installed Ubuntu).

I also called 
/etc/init.d/bluetooth restart
at the beginning.

I attached the list *lshw* prints maybe it's some use for someone.

---

### Post by Arne_M on 2007-10-01
ohh jeah and another thing:

> hcitool dev
Devices:

so it doesn't find any devices :(

---

### Post by Arne_M on 2007-10-02
ok I did some researching in the net, but unfortunately I wasn't very successful.
Somewhere it said, that the ability to switch bluetooth on and of is causing the problems (e.g. if you turned it on in windows and the reboot it will continue to work - can't test that, I've only got ubuntu installed). To solve that problem a program called *dellWirelessCtl* is needed with which this should be able to be switched.
Unfortunately this program is included in *libsmbios-bin_0.13.6_1_i368.deb*, which is a package for gutsy and not for feisty as I would need. So when trying to install the gutsy-package I get incompabilities (something with gcc). If I try to compile the sourcecode and install with checkinstall I also get an error.
Was anyone of you able to create the package for feisty?

Non the less I will try to compile it again tomorrow, I believe there was a cleaner way to create .deb packages than checkinstall.

---

### Post by Arne_M on 2007-10-03
Ok now I was able to build and install the new package, but somehow I get the following errormessage, when I try to execute one of the commands of that package:

Could not instantiate SMBIOS table.


Edit:
Ok, solved this one. I wasn't root, so it seems, only root can read bios stuff (mmh makes sense actually ;) )

So lets see, if I can get it working :)

---

### Post by sr20ve on 2007-10-03
removed

---

### Post by Arne_M on 2007-10-04
interesting - this means, there's probably a package I need to install to get it to work hmm... (is currentliy downloading the cd)

with the dellWirelessCtl I can switch Bluetooth on and off. At least seems to do this, because I get 3 more USB devices, if I switch it on. But somehow no hci device is created.

Bus 004 Device 007: ID 0a5c:4500 Broadcom Corp.
Bus 004 Device 008: ID 0a5c:4502 Broadcom Corp.
Bus 004 Device 009: ID 0a5c:4503 Broadcom Corp.

One of these devices gets classified as a USB hub and the other two as mouse and keyboard. I have no idea what this means.

Arne

---

### Post by Arne_M on 2007-10-04
bluetooth also doesn't work with Ubuntu Ultimate 1.4 ( I used the Cd-version ). lsusb actually prints the same as in feisty.

According to my previous post, I think the device is enabled, but somehow the driver doesn't link the hci device to the usb :(

---

### Post by Arne_M on 2007-10-04
just a stupid thought: Is it possible, that the hci device gets only created, if a bluetooth device is near by?

---

### Post by BigDaddy-CF- on 2007-10-07
Don't know if this will help you or not but I have a Dell XPS m1710 with the internal 355 bluetooth module(Bluetooth 2.0 + EDR). I only recently attempted and succeded in connecting  a bluetooth device to it in Ubuntu([ExpressCard Media Remote for Bluetooth]("http://ubuntuforums.org/showthread.php?t=87919")) using the instructions at the beginning of that thread. However I'm using Gutsy Gibbon and have been since tribe 5. I can't promise anything but maybe the gutsy beta and a little research will go a long way for you.

---

### Post by xidahs on 2008-02-29
OK this is as far as I got with bluetooth on my inspiron 6400 with gusty. I have not tried bluetooth with windows as I installed ubuntu the day I got it.
In the bios bluetooth is enabled and set to be activated using Fn+F2
I tried installing bluetooth packages kbluetooth etc and realised the bluetooth wasn't enabled.
I discovered the need for  dellWirelessCtl so I installed the libsmbios-bin 
```
sudo apt-get install libsmbios-bin
```
I tried```
 sudo dellWirelessCtl --boot --sw_bt 1
```
and it complained about dcdbas so i did
```
sudo modprobe dcdbas
```
then 
```
sudo dellWirelessCtl --boot --sw_bt 1
```
then did 
```
sudo dellWirelessCtl -i   
```  
and got the output

Libsmbios version      : 0.13.6
dellWirelessCtl version: 0.3.0
Wireless Info:
        Hardware switch not supported
        WiFi Locator not supported
        Wireless Keyboard not supported
        NVRAM Size: 0 bytes
        NVRAM format version: 0

Radio Status for WLAN:
        WLAN supported
        WLAN installed
        WLAN enabled
        Status Code: 0

Radio Status for Bluetooth:
        Bluetooth supported
        Bluetooth not installed
        Bluetooth enabled
        Status Code: 2

Radio Status for WWAN:
        WWAN not supported
        Status Code: 3

Wireless Switch Configuration
        WLAN switch control off
        Bluetooth switch control on
        WWAN switch control off
        switch config not locked
        WiFi locator disabled
        WiFi Locator config not locked

BIOS Boot-time settings (new interface):
        Wireless_Switch_Cellular_Control_Enable: (NOT SUPPORTED)
        Wireless_Switch_Cellular_Control_Disable: (NOT SUPPORTED)
        Wireless_Switch_Bluetooth_Control_Enable: 1
        Wireless_Switch_Bluetooth_Control_Disable: 0
        Wireless_Switch_Wireless_LAN_Control_Enable: 0
        Wireless_Switch_Wireless_LAN_Control_Disable: 1
        WiFi_Locator_Enable: (NOT SUPPORTED)
        WiFi_Locator_Disable: (NOT SUPPORTED)
        Cellular_Radio_Enable: (NOT SUPPORTED)
        Cellular_Radio_Disable: (NOT SUPPORTED)
        Bluetooth_Devices_Enable: 1
        Bluetooth_Devices_Disable: 0
        Wireless_LAN_Enable: 1
        Wireless_LAN_Disable: 0

BIOS Boot-time settings (old interface):
        Radio_Transmission_Enable: (NOT SUPPORTED)
        Radio_Transmission_Disable: (NOT SUPPORTED)
        Wireless_Device_Disable: (NOT SUPPORTED)
        Wireless_Device_App_Control: (NOT SUPPORTED)
        Wireless_Device_App_Or_Hotkey_Control: (NOT SUPPORTED)

When I hit Fn+F2 I get Bluetooth disabled  from sudo dellWirelessCtl -i
When I enter
```
 hcitool scan 
```
I get:
 Device is not available: No such device

So now I'm stuck any input would be appreciated

---

