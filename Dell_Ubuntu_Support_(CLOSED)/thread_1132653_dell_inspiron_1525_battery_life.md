---
title: "dell inspiron 1525 battery life"
date: 2009-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djurny on 2009-04-22
hi all,
a lot of posts on battery life and power consumption on here.. just thought i'd share my tweaks gathered from the innanets here :)

most of them are well known and some others i tried out myself (or just havent found them just yet :))

[LIST]
[*]**usb tweaks**
remove all unnecessary usb modules currently loaded. if udev is running, the modules needed to work are loaded automatically anyway..
```

# this needs more intelligence!
usbmodlist="$(lsmod|awk '/usb/{print $1}')"
for mod in $modlist $usbmodlist; do
	modprobe -r $mod 2>/dev/null
done

```

enable usb autosuspend for all currently active usb devices
```

for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
done
for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "1" > $i
done

```

[*]**iwlagn tweaks**
although i read somewhere on here that this setting is reverted automatically in jaunty, i havent noticed it happening on my lp..
```

echo 5 > /sys/bus/pci/drivers/iwlagn/*/power_level

```
disable 11n..
```

echo "options iwlagn 11n_disable=1" > /etc/modprobe.d/iwlagn.conf

```
[upd]
better results all-round with januty-backports iwlagn module.
[*]**bluetooth tweaks**
```

killall kbluetooth4
if sh /etc/init.d/bluetooth stop >/dev/null 2>/dev/null; then
	hciconfig hci0 stop 2>/dev/null
fi
# remove bluetooth modules (if any)

```

[*]**vm tweaks**
google the vm parameters and you will find a list like the one below:
```

echo 10 > /proc/sys/vm/swappiness # 60
echo 10 > /proc/sys/vm/dirty_ratio
echo 5 > /proc/sys/vm/dirty_background_ratio
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

```

[*]**module tweaks**
unload firewire, mmc/sdhc, joystick, webcam, printer and polling modules..
```

modlist="ohci1394 sdhci_pci joydev uvcvideo lp input_polldev"
for mod in $modlist; do
	grep $mod /proc/modules >/dev/null || continue
	modprobe -r $mod 2>/dev/null
done

```

[*]**ide/ata/sata tweaks**
google hdparm/link_power_management_policy and you will find a list like the one below:
```

for i in /dev/sd[a-z]; do
	hdparm -f -F -B 128 -S 12 $i >/dev/null
done
for i in /sys/class/scsi_host/host*/link_power_management_policy; do
	[ "$(cat $i)" = "min_power" ] && continue
	echo min_power > $i
done

```

[*]**irqbalance**
haven't seen any (major) improvement, but the theory is sound and it surely cannot do any harm...
```

sudo apt-get -s install irqbalance
# satisfied with apt-get actions?
sudo apt-get install irqbalance

```
[http://irqbalance.org/]("http://irqbalance.org/")

[*]**use exa w/greedy heuristics**
using jaunty jackalope w/uxa resulted in xorg eating a lot of cpu cycles.. around 10% almost all the time.. going for exa w/greedy heuristics ([http://www.phoronix.com/vr.php?view=13700]("http://www.phoronix.com/vr.php?view=13700")) put xorg in check and kept it around 3% cpu on average..

[*]**firefox w/flashblock**
using powertop, firefox caused a lot of wakeups from idle when browsing sites with flash.. flashblock simply prevents flash running right away, keeping firefox (flash) from waking up the cpu(s) that often
[*]**laptop mode**
enable it!
[/LIST]

with these options, my lp manages power consumption of around 9.5 watts with backlight off and around 11.5 ~ 14 watts with backlight at minimum..
all that with wifi enabled and browsing the innanets.. don't know if these numbers are spectacular, but i'm pretty pleased.. maybe there is some more watts can be squeezed from the current setup..

[upd]
with attached scripts i now have approx 7~9 watts w/out backlight and around 10.6~14 watts w/backlight and wifi/g :)

do any of you have some more hints, tips & tricks to reduce power consumption?

---

### Post by smsmith050 on 2009-04-22
Thanks for the detailed power saving scripts.
On my laptop, HP6715, the bluetooth is the worst power offender. My system spends 2.7% time in power saving state C1E with bluetooth enabled and 62% in power saving state C1E with bluetooth disabled. In state C1E, the CPU clock is ramped down, the Memory is in self-refresh and the Hyper-transport link is stopped.

hciconfig hci0 down really helps with battery life on my laptop.

aticonfig --set-powerstate =1 also helps save battery

---

### Post by djurny on 2009-05-07
updated w/new results :)
added my scripts, please check them if they are suited for your system as well.. i have tried to make them as generic as possible.. although rmod'ing all usb related modules isnt exactly 'generic' ;)

---

