---
title: "Dell Vostro 3550 unknown &quot;Video Bus&quot; device."
date: 2012-10-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zuker on 2012-10-04
Hi all!
I have Dell Vostro 3550 laptop with core i3 and Ubuntu 12.04.1 installed. And there is some strange issue: continuous generation of keypress event which looks like "^@" symbols combination in console and causes graphical interface flickering (not entire display, but windows and cursor), but when external monitor is plugged everything changes dramatically: flickering stops and monitors start to turn off and on in various resolutions.
Experimentally I've found that this issue is caused by "Video Bus" input device:
```

$xinput --list --long
&#8627; Video Bus                               	id=8	[slave  keyboard (3)]
	This device is disabled
	Reporting 1 classes:
		Class originated from: 8. Type: XIKeyClass
		Keycodes supported: 248

```
When device is disabled by following command:
```
xinput set-prop 8 "Device Enabled" 0
```
everything becomes ok.

Here are some details:
```

$xinput --watch-props 8
Device 'Video Bus':
	Device Enabled (140):	0
	Coordinate Transformation Matrix (142):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Product ID (257):	0, 6
	Device Node (258):	"/dev/input/event7"
	Virtual Device (259):	1

```

```

$cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0

```

```

$lsinput -v
/dev/input/event7
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x6
   version : 0
   name    : "Video Bus"
   phys    : "LNXVIDEO/video/input0"
   bits ev : EV_SYN EV_KEY

```

Thanks!

---

### Post by zuker on 2012-10-10
Bug on lanchpad reported: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063658](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063658)

---

### Post by Alexislavie on 2012-10-18
Hi,
I've got the same computer, (Intel Core i5, dual gpu (Intel Sandy Bridge, AMD 6630m).
I experience the exact same bug, thanks to your post I can now "prevent that bug", by running ```
xinput set-prop 8 "Device Enabled" 0
``` automatically at each session launch (thanks to gnome autostart app).
But there might be a "cleaner/better" way to do it, I've heard about the xinit.rc file but do not know how to configure it... Would you have an idea?

I can neither identify that device, it is for sure a duplicate of the "Video Bus" id=7, I think it might be the fact that I have dual gpu, as Dell engineers implemented the muxless system on the Vostro series, they may have not written device properties, like a description or the name of the manufacturer of that "Video Bus". And because X11 isn't really coded to detect well switchable graphic cards, it detects twice that device which leads to a bug...

Question : Do you have the AMD catalyst driver installed?

---

### Post by zuker on 2012-10-29
> **Alexislavie said:**
> 
Question : Do you have the AMD catalyst driver installed?

Hi, yes I have AMD catalyst installed v8.96 - package from ubuntu restricted repo, newer version from AMD are not working for me.

As I can understand this bug caused by some kernel module because while testing upstream kernel I missed the installation of linux-image-extra and "blincking issue" was gone. My thought is to try unloading kernel modules one by one to detect which module causing bug.

---

### Post by zuker on 2012-12-25
12.10 is also affected.

---

### Post by zuker on 2013-01-15
It looks like issue with GUI blinking is fixed but continuous generation of keypress event which looks like "^@" in TTY remains.

---

