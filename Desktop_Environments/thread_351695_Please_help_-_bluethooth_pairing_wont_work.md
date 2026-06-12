---
title: "Please help - bluethooth pairing wont work"
date: 2007-02-02
forum: Desktop Environments
---

### Post by mrwooster on 2007-02-02
Hi,

I am having a nightmare trying to get bluetooth to work with my sony k800i.

I am using a belkin usb bluetooth device and have installed kbluetoothd.


I have edited the hcid.conf file so that the pin manager is using /usr/lib/kdebluetooth/kbluepin;

When I try to connect to my phone from my pc, it comes up on my phone, saying unknown wants to access my items, I say ok, it then asks me to pair the two devices, I say yes, it then asks me to enter a passcode on my phone, i enter 1234 and it then says bluetooth connection failed... It never asks me to enter a passcode on my pc.

When I try to pair the two up from my phone, it finds my pc, it asks me to enter a passcode, 1234, it then says 'waiting for other device to enter passcode' and kbluetoothd pops up with a message saying 'host rejected for security reasons' and then my phone says bluetooth connection failed.


PLEASE HELP ;-)

Thanks

Guy

---

### Post by mrwooster on 2007-02-02
I seem to have been able to fix this problem:

Apparently there is a bug in the bluez system which still has not been resolved: [https://launchpad.net/ubuntu/+source/bluez-utils/+bug/56651](https://launchpad.net/ubuntu/+source/bluez-utils/+bug/56651)

I completely uninstalled all bluetooth components and then reinstalled everything apart from the bluez stuff. I then used my phone to add my pc to my devices - no passcode was asked for and the devices paired up fine.

Now everything seems to work.

---

### Post by mtn on 2007-05-18
I finally got this syncing working with my Sony-Ericson K610i A120 Toshiba Laptop with Bluetooth dongle. I followed the instructions for the bug report link above, tho I had to install all the Bluetooth dev packages through Synaptic first. 


Compile passkey-agent like this:

sudo apt-get install build-essential cdbs libdbus-glib-1-dev debhelper

sudo apt-get source bluez-utils

cd bluez-utils-3.1/

sudo ./debian/rules binary

(This builds a deb in ../)

Install that, or cp ./hcid/passkey-agent /usr/bin/ or run ./hcid/passkey-agent

Then installed all the new .deb packages in my home folder. Rebooted, and followed the instructions here [http://ubuntuforums.org/showpost.php?p=1779032&postcount=3](http://ubuntuforums.org/showpost.php?p=1779032&postcount=3)

Thanks all

---

### Post by SuperAndy on 2007-07-19
yep, it works

just dont forget to reboot :P

---

