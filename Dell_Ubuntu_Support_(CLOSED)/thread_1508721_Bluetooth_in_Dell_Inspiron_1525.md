---
title: "Bluetooth in Dell Inspiron 1525"
date: 2010-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gabo.cr on 2010-06-13
I have a Dell Inspiron 1525, I want to activate the Bluetooth.
Reading a few threads I realized I had to upgrade the Bios, so I did that today. I upgraded to the latest version.
The bluetooth is still not working, even when I searched for new hardware devices.
Now, this is what I get using this command:

```
$ sudo dellWirelessCtl --sw_bt 1 --bt 1 
Set runtime settings for Bluetooth

Set runtime switch settings for Bluetooth
	This system does not support runtime control of wireless switch settings.

Radio Status for Bluetooth:
	Bluetooth enabled at boot
	Bluetooth supported
	Bluetooth enabled
	Bluetooth not installed
	Bluetooth controlled by wireless switch at boot
	Bluetooth runtime switch control currently enabled
	Status Code: 2

```

I'm not an expert so I really don't understand what it means the "runtime control of wireless switch settings".
There are a lot of Forums explaining how to activate this, but they use Win*, I don't have that and I don't want to have it, I only use Ubuntu.
I was actually very happy to be able to upgrade the Bios from Ubuntu !
But anyways, any help will be appreciated.

---

