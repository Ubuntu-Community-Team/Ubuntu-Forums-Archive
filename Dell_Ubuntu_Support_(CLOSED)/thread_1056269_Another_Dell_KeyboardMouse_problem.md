---
title: "Another Dell Keyboard/Mouse problem"
date: 2009-01-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bamhm182 on 2009-01-31
EDIT: I got it sorted. I could have sworn I tried this before, but I guess I hadn't...

Anyways, I typed in sudo gedit /etc/default/bluetooth, and than it opened a file that had the HID2HCI_ENABLED=1 line in it, I changed the 1 or 0 and now it works.

As I was typing this, I noticed what I had done wrong the first few times, all the tutorials I had read had told me to put in sudo gedit /etc/bluetooth/hcid.conf. This didn't work for my Dell Bluetooth Keyboard and Mouse.

If anyone else is having this problem, make sure you're typing in "sudo gedit /etc/default/bluetooth" than in there, change HID2HCI_ENABLED=1 or HID2HCI_ENABLED=0.


Original post:
```

I've seen the other threads, followed every single one of them step by step, but nothing is working.

I'm trying to connect my bluetooth keyboard/mouse to my Ubuntu system correctly. Every time I turn on my computer, I have to reconnect my dongle. I've gone in to sudo gedit /etc/default/bluetooth, I didn't go into sudo gedit /etc/default/bluez-utils because it doesn't  exist on my computer apparently. I added 

 device KEYBOARD_ADDR {
     name "Microsoft Wireless Keyboard";
     auth enable;
     encrypt enable;
 }
 
 device MOUSE_ADDR {
     name "Microsoft Mouse";
 }

where KEYBOARD_ADDR and MOUSE_ADDR are my keyboard and mouse MAC IDs. No luck. I've run short on patience and ideas, so I decided to post here. Thanks in advance.

EDIT: Also, where it says 

> If you have followed all the steps above and you find your mouse or keyboard don&#8217;t automatically reconnect, we can fix it. Run the following command in a terminal

sudo gedit /etc/default/bluez-utils

Find the following lines

HIDD_ENABLED=0
HIDD_OPTIONS=&#8221;&#8230;&#8221;

Change them to

HIDD_ENABLED=1
HIDD_OPTIONS=&#8221;--master --connect KEYBOARD_ADDR --connect MOUSE_ADDR --server&#8221;

Now reboot and hopefully they&#8217;ll automatically connect (give them a few seconds to connect after you move the mouse/press a key).


on the tutorials, there is nothing in the bluetooth file, it was empty until I put the MAC ID stuff in there, and that's all that's in there now.
```

---

