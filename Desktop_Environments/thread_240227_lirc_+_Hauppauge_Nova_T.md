---
title: "lirc + Hauppauge Nova T"
date: 2006-08-20
forum: Desktop Environments
---

### Post by frying_fish on 2006-08-20
I have a hauppauge Nova T pci card, and would like to get the remote to work with lirc, currently some of the buttons are just detected as regular keyboard events, so i can for example press the power button and up comes the logout option.

The arrow keys and number pad work as you would expect from a normal keyboard, however this is still not my desired actions from the remote.  I want it to work with lirc so I can make certain programs interact with it better, however my attempts so far are failing.

the output from lspci -v relevant to the card are:
```

0000:02:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: Hauppauge computer works Inc. Hauppauge Nova-T DVB-T
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

0000:02:09.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. Nova-T DVB-T Model 909
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

0000:02:09.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
        Subsystem: Hauppauge computer works Inc. Nova-T DVB-T Model 909
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [4c] Power Management version 2

```


I have all the lirc options installed in synaptic, however trying to run irw or irrecord always results in:

```

connect: Connection Refused

```

If anyone else has gotten the remote from this card set up with lirc then please let me know the steps, as I cannot get it to work.

Following this guide:
[url]
http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper
[/url]

I have this as the device
```

I: Bus=0001 Vendor=0070 Product=9002 Version=0001
N: Name="cx88 IR (Hauppauge Nova-T DVB-T"
P: Phys=pci-0000:02:09.0/ir0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 7bb80 0 10000000

```

but following the rest of it leads to setting it up as a keyboard and even some of the options it suggests for running lircd don't work.

Any help is appreciated

---

### Post by frying_fish on 2006-08-20
ok, so a bit more digging and I now have this:

```

# lircd -n -H default -d /dev/input/event4
lircd: lircd(hauppauge) ready
lircd: accepted new client on /dev/lircd
lircd: could not get hardware features
lircd: this device driver does not support the new LIRC interface
lircd: major number of /dev/input/event4 is 13
lircd: LIRC major number is 61
lircd: check if /dev/input/event4 is a LIRC device
lircd: caught signal
Terminated

```

this shows when I run irw in another terminal, so i think this is some progress but if anyone knows more....

---

### Post by jon_benge on 2006-08-20
I have written a guide on installing Lirc for the Nova-T which you can read [here]("http://ubuntuforums.org/showthread.php?t=183545&highlight=lirc")

It's for kubuntu though because ubuntu does not have a IRKICK equivalent. You could probably install IRKICK in ubuntu but you would have to install some kde libs as well

---

### Post by frying_fish on 2006-08-21
Ok this guide has been helpful in someways, it shows that when doing evtest I get a response from the remote and it seems all buttons are mapped, however, lircd seems to only support the "default" driver, it doesn't support dev/input on my system, do you know why this would be?

|This is the result of evtest:
```

sudo evtest /dev/input/event4
Input driver version is 1.0.0
Input device ID: bus 0x1 vendor 0x70 product 0x9002 version 0x1
Input device name: "cx88 IR (Hauppauge Nova-T DVB-T"
Supported events:
  Event type 0 (Reset)
    Event code 0 (Reset)
    Event code 1 (Key)
    Event code 20 (Repeat)
  Event type 1 (Key)
    Event code 28 (Enter)
    Event code 71 (KP7)
    Event code 72 (KP8)
    Event code 73 (KP9)
    Event code 75 (KP4)
    Event code 76 (KP5)
    Event code 77 (KP6)
    Event code 79 (KP1)
    Event code 80 (KP2)
    Event code 81 (KP3)
    Event code 82 (KP0)
    Event code 103 (Up)
    Event code 105 (Left)
    Event code 106 (Right)
    Event code 108 (Down)
    Event code 113 (Mute)
    Event code 114 (VolumeDown)
    Event code 115 (VolumeUp)
    Event code 116 (Power)
    Event code 119 (Pause)
    Event code 128 (Stop)
    Event code 139 (Menu)
    Event code 142 (Sleep)
    Event code 163 (NextSong)
    Event code 165 (PreviousSong)
    Event code 167 (Record)
    Event code 168 (Rewind)
    Event code 174 (Exit)
    Event code 207 (?)
    Event code 208 (?)
    Event code 353 (Select)
    Event code 363 (Channel)
    Event code 365 (EPG)
    Event code 367 (MHP)
    Event code 370 (Subtitle)
    Event code 372 (Zoom)
    Event code 377 (TV)
    Event code 385 (Radio)
    Event code 388 (Text)
    Event code 392 (Audio)
    Event code 393 (Video)
    Event code 398 (Red)
    Event code 399 (Green)
    Event code 400 (Yellow)
    Event code 401 (Blue)
    Event code 402 (ChannelUp)
    Event code 403 (ChannelDown)
    Event code 412 (Previous)
  Event type 20 (Repeat)
Testing ... (interrupt to exit)

```

but when I do 
```

$ lircd --driver=help
Driver `help' not supported.
Supported drivers:
        default

```

So dev/input isn't listed, where would I now go from here?

---

### Post by frying_fish on 2006-08-21
it would appear that that doesn't matter, and I now have lirc working, I must have done something slightly different, but it is all good now, and now I just need to find a correct .lircrc for audacious and I will be set

---

