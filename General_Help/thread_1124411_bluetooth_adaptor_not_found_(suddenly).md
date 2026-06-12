---
title: "bluetooth adaptor not found (suddenly)"
date: 2009-04-13
forum: General Help
---

### Post by yosibeck on 2009-04-13
I am using Jaunty on Toshiba Laptop Satellite.
I have been using Ubuntu since Hardy with my bluetooth Microsoft 5000 mouse without problems.
Always after booting up the bluetooth icon appeared up on top.
Also after upgrading to Jaunty bluetooth worked.
Today suddenly the  bluetooth icon does not appear, as if the adaptor is not present. Under preferences -> bluetooth the settings are: only display when adaptor present, as I have always had it.
When doing Preferences -> Bluetooth Control and then clicking the icon and choose turn radio on, I get: "radio startup failed. Resource temporarily unavailable"
(I should add that I have a dual boot system with Ubuntu and Windows and in windows bluetooth works well, so there's no hardware problem.)
I have tried to uninstall everything connected to bluetooth and than re-installing, but to no avail.
No bluetooth icon and of course my mouse is useless.
Anyone who can suggest solutions?
Thanks

---

### Post by antikristian on 2009-04-13
In the terminal try
```
sudo modprobe btusb
dmesg | tail
```

And tell us what happens:)

---

### Post by kostkon on 2009-04-14
Try to reset your bluetooth adapter and see if that will make any difference.

Firstly, in a terminal, give
```
hcitool dev
```
to list all your bluetooth adapters/devices, the output will be in the form of
```
Devices:
        hci0    XX:XX:XX:XX:XX:XX
```
Assuming that you only have one bluetooth device, then to reset it give
```
sudo hciconfig hci0 reset
```

---

### Post by yosibeck on 2009-04-14
Hi Antikristian:
I did as you said.
After "sudo modprobe btusb" I go straight back to the cursor.
Then after "dmesg | tail" I get the following output:
```
[   79.788299] wlan0: authenticate with AP 00:1b:9e:d8:0b:ee
[   80.805782] wlan0: authenticate with AP 00:18:6e:11:c3:2c
[   80.807375] wlan0: authenticated
[   80.807379] wlan0: associate with AP 00:18:6e:11:c3:2c
[   80.809832] wlan0: RX AssocResp from 00:18:6e:11:c3:2c (capab=0x471 status=0 aid=1)
[   80.809835] wlan0: associated
[   80.843237] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   91.476015] wlan0: no IPv6 routers present
[  511.160627] Bluetooth: Generic Bluetooth USB driver ver 0.3
[  511.160675] usbcore: registered new interface driver btusb
```

Hi Kostkon,
Doing "hcitool dev" just lists: "Devices:"   with no further details
Doing "hciconfig hci0 reset" gives me the output: "Can't get device info: No such device" 

As I mentioned, in Windows the adaptor works fine.

I'm really stuck with this and appreciate any advice.

---

### Post by yosibeck on 2009-04-14
The strange thing is - if i cold boot into Ubuntu I have the above problem.
BUT - if I first boot into Windows (Vista) and then make a restart (soft boot) into Ubuntu, the bluetooth works.
It is as if Windows knows to turn it on and then Ubuntu after a soft boot know to use it.
I certainly am not looking forward to always first booting into Vista...
I like my Ubuntu much better.
When bluetooth works I get the following outputs:
```
yosibeck@yosibeck-laptop:~$ dmesg | tail
[  126.568298] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[  126.570535] input: Microsoft Bluetooth Notebook Mouse 5000 as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/bluetooth/hci0/hci0:42/input9
[  126.579480] generic-bluetooth 0005:045E:0700.0001: input,hidraw0: BLUETOOTH HID v1.00 Mouse [Microsoft Bluetooth Notebook Mouse 5000] on 00:03:7A:EE:ED:82
[  173.080467] wlan0: authenticate with AP 00:18:6e:11:c3:2c
[  173.094477] wlan0: authenticate with AP 00:18:6e:11:c3:2c
[  173.096540] wlan0: authenticated
[  173.096549] wlan0: associate with AP 00:18:6e:11:c3:2c
[  173.099039] wlan0: RX AssocResp from 00:18:6e:11:c3:2c (capab=0x471 status=0 aid=1)
[  173.099043] wlan0: associated
[  173.120506] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

```
yosibeck@yosibeck-laptop:~$ hcitool dev
Devices:
	hci0	00:03:7A:EE:ED:82
```

I wish I knew how to make Ubuntu turn on the adaptor itself.
After looking on the internet I see there is a problem with Toshiba laptops. The toshset module does not recognize half of the existing Toshiba laptops and therefore bluetooth cannot be turned on by the command:
toshset -bluetooth on

The workarounds that are suggested here and there don't solve the problem.
Any help is welcome.

---

### Post by billybag on 2009-04-16
I to am unable to get the bluetooth icon to appear, as well. "always display icon" is selected in my options.

I am using Intrepid.

I use a Dell XPS m1530. Bluetooth has worked fine in the past with ubuntu.

---

### Post by antikristian on 2009-04-16
Okay, my final thoughts on the matter would be the following:

First modprobe btusb
Then try toshset -bluetooth on
if this doesn't work
Check to see if there is a switch on your computer that disables bluetooth
(maybe windows ignores it somehow)

People have had problems with toshset, not sure if this is still the case, see this post and solution:
[http://ubuntuforums.org/showthread.php?t=986075](http://ubuntuforums.org/showthread.php?t=986075)

Look for howtos specific for your laptop or a similar laptop on one of these
[http://tuxmobil.org/toshiba.html](http://tuxmobil.org/toshiba.html)
[http://www.linux-on-laptops.com/toshiba.html](http://www.linux-on-laptops.com/toshiba.html)
[http://linux.toshiba-dme.co.jp/linux/](http://linux.toshiba-dme.co.jp/linux/)

---

### Post by Stevko on 2009-05-06
Do you have BLUETOOTH_ENABLED=1 set in /etc/default/bluetooth? I had similar "problem" - dmesg showed bluetooth connected and module loaded, but applet icon did not show and setting the variable helped. (maybe I switched it off myself but that is not important now)

---

