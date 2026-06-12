---
title: "Multiple input devices in X"
date: 2006-08-31
forum: Desktop Environments
---

### Post by kidders on 2006-08-31
Hi everyone,

I'm trying to figure out how to get KDE to let me use multiple mice & keyboards, each with different button & key maps.

The other day, I figured I'd try to get the bells 'n whistles on all my input devices working at the same time, but I haven't been having much luck :( My biggest problem is getting these to work simultaneously:

[LIST]
[*]Apple bluetooth keyboard, Mac US+Euro keymap with volume/eject keys
[*]Generic USB keyboard, PC UK keymap with power/sleep/etc. keys
[/LIST]

The problem I'm having is with writing my xorg.conf in such a way that X knows which tweaks to apply to which keyboard. The tweaks themselves are pretty straighforward.

My first thought was to use udev rules to create predictable /dev entries and explicitly enumerate my keyboards in xorg.conf. I'm having less than no luck finding one for my wireless keyboard though ...

```
$ cat /proc/bus/input/devices
I: Bus=0005 Vendor=05ac Product=0209 Version=0110
N: Name="Apple Wireless Keyboard"
P: Phys=00:10:60:A3:32:D5
S: Sysfs=/class/input/input7
H: Handlers=kbd event4
B: EV=120003
B: KEY=10000 7 ff87207e c1405fff fffeffdf ffefffff ffffffff fffffffe
B: LED=1f
```

```
udevinfo -a -p `udevinfo -q path -n /dev/input/event4`
  looking at class device '/sys/class/input/input7/event4':
    KERNEL=="event4"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:68"
```

Not a whole lot of help :(

Of course, even if I *did* get it working, I'm not sure it'd be a good idea ... While I was wandering around the web looking for ways around another problem, I noted the suggestion that explicitly specifying input device paths in xorg.conf is > very strongly discouraged. Is that true?!


Just to frustrate me even more, when I tried to use the evdev driver for one of my mice, I kept getting ...

> Preinit returned NULL for "devname"

When I googled the error, I found that this message often has something to do with device name pattern matching. Unfortunately, tweaking my udev rule so the device was always called /input/event999 (which matches the required pattern) had no effect :(

I can't help getting the feeling I'm overlooking some obvious way of solving all this in one go, which is why I've posted all the problems together. I'd really appreciate any suggestions.

Thanks a lot!

---

### Post by kidders on 2006-09-26
Nobody? :-(

---

