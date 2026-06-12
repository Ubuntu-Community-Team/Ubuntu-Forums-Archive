---
title: "bluetooth on dell latitude d830"
date: 2007-10-31
forum: Dell  Ubuntu Support
---

### Post by nicola76b on 2007-10-31
Hi all,
my integrated bluetooth device (Vista - Internal Dell 360 Bluetooth Card) not work under gusty
I've just posted on ubuntu italian forum but they didn't find a solution..
It seems all ok, if I power-on hardware switch for wifi/bluetooth on laptop, wifi works and BT icon appears on gnome Desktop.
Open a shell:

```
hciconfig 
hci0:   Type: USB
        BD Address: myAddress ACL MTU: 310:10 SCO MTU: 64:8
        UP RUNNING PSCAN 
        RX bytes:701 acl:0 sco:0 events:24 errors:0
        TX bytes:346 acl:0 sco:0 commands:23 errors:0
```

or

```
hcitool dev
Devices:
        hci0    myAddress
```

In short, seems work, but if I serch near devices, or from devices search PC it doesn't find anything (also if I set property that anyone can see it..).

I had similar problem on winzozz Vista, that I resolved by click on BT icon and set "turn on BT". So...

How can I turn on BT in linux?!?!?!
I hate that something works in win and not in linux...

Thanks a lot,
by
-Nicola

---

