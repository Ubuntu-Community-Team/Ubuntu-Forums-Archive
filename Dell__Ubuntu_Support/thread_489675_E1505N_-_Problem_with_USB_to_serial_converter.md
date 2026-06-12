---
title: "E1505N - Problem with USB to serial converter"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by Chasoid on 2007-07-01
I have an Insprion E1505N pre-loaded with Ubuntu Feisty.

I bought a Rosewill RCW-601 USB to serial adapter.  I use it to connect to a ham radio device (it lets me do "digital modes", such as PSK31).

My problem:  the RCW-601 often "disconnects."  It is configured as /dev/ttyUSB0, but sometimes the program that I use (gMFSK) throws an error, telling me that /dev/ttyUSB0 is no longer there.  :(

Is there a command-line command that I can use to reset the RCW-601?  Unplugging the RCW-601 USB cable and plugging it back in sometimes resets it.  So does a cold reboot.  But if I could use the command line to reset it, I'd save a bit of time.

(Of course, ideas on how to get it to not drop in the first place are welcome as well!)  :D

Thanks!

---

### Post by neptho on 2007-07-01
Hi Charlie,

Have you checked for any error messages for overruns or other issues in your logs?  

You can open a terminal and try either (or both) of the following and look for messages when it drops out:

```
%sudo tail -f /var/log/dmesg
%sudo tail -f /var/log/messages
```

---

### Post by Chasoid on 2007-07-02
Thanks... I should have put some log file output in the original post.  My bad.  :redface:

More detail:  I'm connecting my E1505N to an MFJ-1275 Sound Card Radio Interface which, in turn, is connected to my ham radio.

The USB to serial interface starts out at /dev/ttyUSB0.  When the problem happens, sometimes it has been mysteriously changed to /dev/ttyUSB1.  Then it dies and comes back yet again as /dev/ttyUSB0.

It's a real problem, since this happens when I'm trying to transmit to another ham operator.  My radio will transmit a few characters and then die because the converter has a problem.


Here are some lines from /var/log/debug: (my computer's name is "liz")
```
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.382598] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_if0'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.385289] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.387240] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_usbraw'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.679072] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.728656] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_serial_usb_1'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.755774] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_if0'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.756505] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_usbraw'). 

```
Here are some lines from kern.log
```

Jul  2 10:10:20 liz kernel: [  248.932000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jul  2 10:10:20 liz kernel: [  248.932000] usb 2-1: USB disconnect, address 3
Jul  2 10:10:20 liz kernel: [  248.932000] pl2303 2-1:1.0: device disconnected
Jul  2 10:10:21 liz kernel: [  249.044000] usb 2-1: new full speed USB device using uhci_hcd and address 4
Jul  2 10:10:21 liz kernel: [  249.204000] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 10:10:21 liz kernel: [  249.204000] pl2303 2-1:1.0: pl2303 converter detected
Jul  2 10:10:21 liz kernel: [  249.208000] usb 2-1: pl2303 converter now attached to ttyUSB1
Jul  2 10:10:30 liz kernel: [  258.356000] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
Jul  2 10:11:27 liz kernel: [  315.344000] cnxthsf_OsEventWaitTime(f7bd07a0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT
Jul  2 10:12:48 liz kernel: [  396.604000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jul  2 10:12:48 liz kernel: [  396.604000] usb 2-1: USB disconnect, address 4
Jul  2 10:12:48 liz kernel: [  396.604000] pl2303 2-1:1.0: device disconnected
Jul  2 10:12:48 liz kernel: [  396.716000] usb 2-1: new full speed USB device using uhci_hcd and address 5
Jul  2 10:12:48 liz kernel: [  396.876000] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 10:12:48 liz kernel: [  396.880000] pl2303 2-1:1.0: pl2303 converter detected
Jul  2 10:12:48 liz kernel: [  396.880000] usb 2-1: pl2303 converter now attached to ttyUSB0
Jul  2 10:13:28 liz kernel: [  436.168000] pl2303 ttyUSB1: pl2303 converter now disconnected from ttyUSB1
Jul  2 10:13:53 liz kernel: [  461.368000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jul  2 10:13:53 liz kernel: [  461.368000] usb 2-1: USB disconnect, address 5
Jul  2 10:13:53 liz kernel: [  461.368000] pl2303 2-1:1.0: device disconnected
Jul  2 10:13:53 liz kernel: [  461.480000] usb 2-1: new full speed USB device using uhci_hcd and address 6
Jul  2 10:13:53 liz kernel: [  461.640000] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 10:13:53 liz kernel: [  461.640000] pl2303 2-1:1.0: pl2303 converter detected
Jul  2 10:13:53 liz kernel: [  461.644000] usb 2-1: pl2303 converter now attached to ttyUSB1
Jul  2 10:20:01 liz kernel: [  829.636000] cnxthsf_OsEventWaitTime(f7bd07a0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT

```

And here are a few lines from syslog:
```

Jul  2 10:12:48 liz kernel: [  396.880000] usb 2-1: pl2303 converter now attached to ttyUSB0
Jul  2 10:12:48 liz NetworkManager: <debug info>^I[1183389168.927426] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial'). 
Jul  2 10:12:48 liz NetworkManager: <debug info>^I[1183389168.974309] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_serial_usb_0'). 
Jul  2 10:12:49 liz NetworkManager: <debug info>^I[1183389169.000076] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_if0'). 
Jul  2 10:12:49 liz NetworkManager: <debug info>^I[1183389169.020231] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_usbraw'). 
Jul  2 10:13:28 liz NetworkManager: <debug info>^I[1183389208.178425] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_serial_usb_1'). 
Jul  2 10:13:28 liz kernel: [  436.168000] pl2303 ttyUSB1: pl2303 converter now disconnected from ttyUSB1
Jul  2 10:13:53 liz kernel: [  461.368000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Jul  2 10:13:53 liz kernel: [  461.368000] usb 2-1: USB disconnect, address 5
Jul  2 10:13:53 liz kernel: [  461.368000] pl2303 2-1:1.0: device disconnected
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.382598] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_if0'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.385289] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.387240] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_usbraw'). 
Jul  2 10:13:53 liz kernel: [  461.480000] usb 2-1: new full speed USB device using uhci_hcd and address 6
Jul  2 10:13:53 liz kernel: [  461.640000] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 10:13:53 liz kernel: [  461.640000] pl2303 2-1:1.0: pl2303 converter detected
Jul  2 10:13:53 liz kernel: [  461.644000] usb 2-1: pl2303 converter now attached to ttyUSB1
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.679072] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.728656] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_serial_usb_1'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.755774] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_if0'). 
Jul  2 10:13:53 liz NetworkManager: <debug info>^I[1183389233.756505] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2303_noserial_usbraw').

```

Thanks again!

---

### Post by Chasoid on 2007-07-02
Almost forgot... here are some lines from dmesg:
```

[  248.932000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  248.932000] usb 2-1: USB disconnect, address 3
[  248.932000] pl2303 2-1:1.0: device disconnected
[  249.044000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[  249.204000] usb 2-1: configuration #1 chosen from 1 choice
[  249.204000] pl2303 2-1:1.0: pl2303 converter detected
[  249.208000] usb 2-1: pl2303 converter now attached to ttyUSB1
[  258.356000] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[  315.344000] cnxthsf_OsEventWaitTime(f7bd07a0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT
[  396.604000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  396.604000] usb 2-1: USB disconnect, address 4
[  396.604000] pl2303 2-1:1.0: device disconnected
[  396.716000] usb 2-1: new full speed USB device using uhci_hcd and address 5
[  396.876000] usb 2-1: configuration #1 chosen from 1 choice
[  396.880000] pl2303 2-1:1.0: pl2303 converter detected
[  396.880000] usb 2-1: pl2303 converter now attached to ttyUSB0
[  436.168000] pl2303 ttyUSB1: pl2303 converter now disconnected from ttyUSB1
[  461.368000] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[  461.368000] usb 2-1: USB disconnect, address 5
[  461.368000] pl2303 2-1:1.0: device disconnected
[  461.480000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[  461.640000] usb 2-1: configuration #1 chosen from 1 choice
[  461.640000] pl2303 2-1:1.0: pl2303 converter detected
[  461.644000] usb 2-1: pl2303 converter now attached to ttyUSB1
[  829.636000] cnxthsf_OsEventWaitTime(f7bd07a0/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT

```

And here are some lines from /var/log/messages:
```

Jul  2 10:10:20 liz kernel: [  248.932000] usb 2-1: USB disconnect, address 3
Jul  2 10:10:20 liz kernel: [  248.932000] pl2303 2-1:1.0: device disconnected
Jul  2 10:10:21 liz kernel: [  249.044000] usb 2-1: new full speed USB device using uhci_hcd and address 4
Jul  2 10:10:21 liz kernel: [  249.204000] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 10:10:21 liz kernel: [  249.204000] pl2303 2-1:1.0: pl2303 converter detected
Jul  2 10:10:21 liz kernel: [  249.208000] usb 2-1: pl2303 converter now attached to ttyUSB1
Jul  2 10:10:30 liz kernel: [  258.356000] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
Jul  2 10:12:48 liz kernel: [  396.604000] usb 2-1: USB disconnect, address 4
Jul  2 10:12:48 liz kernel: [  396.604000] pl2303 2-1:1.0: device disconnected
Jul  2 10:12:48 liz kernel: [  396.716000] usb 2-1: new full speed USB device using uhci_hcd and address 5
Jul  2 10:12:48 liz kernel: [  396.876000] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 10:12:48 liz kernel: [  396.880000] pl2303 2-1:1.0: pl2303 converter detected
Jul  2 10:12:48 liz kernel: [  396.880000] usb 2-1: pl2303 converter now attached to ttyUSB0
Jul  2 10:13:28 liz kernel: [  436.168000] pl2303 ttyUSB1: pl2303 converter now disconnected from ttyUSB1
Jul  2 10:13:53 liz kernel: [  461.368000] usb 2-1: USB disconnect, address 5
Jul  2 10:13:53 liz kernel: [  461.368000] pl2303 2-1:1.0: device disconnected
Jul  2 10:13:53 liz kernel: [  461.480000] usb 2-1: new full speed USB device using uhci_hcd and address 6
Jul  2 10:13:53 liz kernel: [  461.640000] usb 2-1: configuration #1 chosen from 1 choice
Jul  2 10:13:53 liz kernel: [  461.640000] pl2303 2-1:1.0: pl2303 converter detected
Jul  2 10:13:53 liz kernel: [  461.644000] usb 2-1: pl2303 converter now attached to ttyUSB1

```

Whew!  I looks like the same sort of messages are being displayed in more than one log file.  Not sure why that is.  :?:

---

### Post by rhmeyer50 on 2007-07-05
Charlie,
I am pretty new to Ubuntu my self; but, as a ham also, you might do the usual RF toroidal chokes on your audio and usb port lines coming in and out of your computer. It could be RFI causing the ports to change.  Also try grounding your computer case to the station ground. GL HTH
73,
Rob WA9UAA

---

### Post by eastburn on 2007-07-11
I have a similar problem.  I'm also having problems using a USB/serial converter.  I'm using Ubuntu 7.04 with an AMD 1.6 G processor and 512 Mb mem, long forgot what brand of USB/serial converter I'm using.  Also  using a Belkin USB hub.  In my case when I hook up the converter (into the hub) and watch the /dev file I can see the ttyUSB0 file flash on the screen then disappear.  This behavior continues until I unplug the converter.  When I check the /var/log/messages file I see that the converter is recognized then disconnected and the pair of messages repeats until I unplug the converter.  I have tried just plugging into a open USB port on the back of the computer, but i still have the same problem.

I to  thought it might me a grounding problem and tried several times to get a good ground.  No change in the converter problem.  

I fired up another linux OS (PCLinuxOS 2007) and plugged the converter in, watched the /dev file and observed that the /dev/ttyUSB0 file was established and is stable (again using the hub).  So the problem seems to be with the Ubuntu OS.  

So were do we go from here?

---

### Post by eastburn on 2007-07-13
Found something that works.  Check out my write up over in the hardware forum. Its titled "Fix for brltty interfering with USB devices."  This worked for me.  Discovered the fix while reading the Ubuntu Bug forum.  This problem affects all Ubuntu products.  I have not seen this bug in other Distros so far.

---

### Post by Chasoid on 2007-07-14
eastburn - Thanks very much for the reply.  I've made the changes to the file and will try this fix the next time I'm at the location where my radios are at (late July or early August, hopefully).

I was using a RCW-601 USB to serial converter.  I just ordered a "Keyspan" USB to serial converter, which I've read is better.  (Comments on the RCW-601 indicate that it's prone to flakyness).  :rolleyes:

So... I'll report how the fix affects my RCW-601 and also how well the Keyspan converter works with/without the fix.

73,
N0ZC

---

### Post by newpants2003 on 2007-07-25
> **Chasoid said:**
> eastburn - Thanks very much for the reply.  I've made the changes to the file and will try this fix the next time I'm at the location where my radios are at (late July or early August, hopefully).

I was using a RCW-601 USB to serial converter.  I just ordered a "Keyspan" USB to serial converter, which I've read is better.  (Comments on the RCW-601 indicate that it's prone to flakyness).  :rolleyes:

So... I'll report how the fix affects my RCW-601 and also how well the Keyspan converter works with/without the fix.

73,
N0ZC

please post your result, i have the same problem.

---

### Post by Chasoid on 2007-07-25
Will do!  The Keyspan USB to serial converter arrived safe and sound.  It works without any configuration on my part with my Garmin GPS unit.

I'll have to wait until I travel to the place where I have my ham radios to see if it fixes the problem I was having.  I'll be sure to post the results.

Fingers crossed!  :D

---

### Post by newpants2003 on 2007-07-26
Found solution!!!! (at least for me)

[http://ubuntuforums.org/showthread.php?t=428778](http://ubuntuforums.org/showthread.php?t=428778)


if you watching the /dev folder in natural when you plug in the converter, you can see the ttyUSB0 show up for 2 seconds and disappeared.
i think this is a buy in ubuntu. people say they dont have this problem in other distribution.

---

### Post by Chasoid on 2007-09-02
The "Keyspan" USB to serial converter works with my radios!!!  I arrived at this QTH (location) a couple of days ago and have used it for multiple QSOs (conversations) without incident.

So... I no longer have the problem of losing my serial connection whenever I transmit.  This converter was a bit more money (it's priced at $34.99 plus shipping), but it's worth it.

For the record, I got the " KEYSPAN USB High Speed Serial Adapter Model USA-19HS".

I hope this helps.

73s,
N0ZC

---

