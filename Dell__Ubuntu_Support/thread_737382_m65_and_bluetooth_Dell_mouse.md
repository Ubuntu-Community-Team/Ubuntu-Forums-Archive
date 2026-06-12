---
title: "m65 and bluetooth Dell mouse"
date: 2008-03-27
forum: Dell  Ubuntu Support
---

### Post by slipline on 2008-03-27
Hello, I have a dell M65 and the Dell bluetooth mouse and keyboard set. 

I recently installed ubuntu 8.04 and can not get my mouse to connect at all. 

I have tried all of the FAQ and HOW To documents that I can find. 

I have bluez-utils installed. I can find the device with hcitool scan , I have modified the /etc/default/bluetooth file and the bluetooth.config to contain parameters to connect to the mouse such as HIDD_ENABLED=1 and the device MAC mapping in config. 

The bluetooth icon is on the tray, and it can pick it up in the browse tab. Under preferences it sometimes shows up but setting it to trusted or not does  nothing. 

I am completely lost at this point.

---

### Post by HaTaX on 2008-05-05
I followed these instructions:

[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

Where he says "sudo /etc/init.d/bluez-utils restart" you need to replace the "bluez-utils" with "bluetooth" and then it will restart the bluetooth stack.

This worked for me! Hopefully it will for you too.

---

