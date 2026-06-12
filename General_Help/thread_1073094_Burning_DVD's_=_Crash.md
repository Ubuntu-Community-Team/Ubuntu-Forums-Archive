---
title: "Burning DVD's = Crash"
date: 2009-02-18
forum: General Help
---

### Post by PoopyTheJ on 2009-02-18
When burning DVD's using either Brasero or the vd/DVD creator with Ubuntu my system crashes. HDD activity is through the roof, DVD burnner is spinning like a sonic screwdriver and the entire system locks hard, no response to CTRL+ALT+DEL or BACKSPACE. ALT+F1 doesn't work, I have to hard reboot by powering down manually. How can I fix this? Is there a log file I can check to see what's going on?

EDIT:Forgot to mention DVD burner works fine in Windows and burns CD's fine in Ubuntu...

---

### Post by Kain000 on 2009-02-18
humm I've not had the burner problem this badly, I do recall when I used brasio that it would lock up on me but I still had the rest of the system, and could force quit it.

What do the sys logs have to say about it?

system > Admin > System logs

---

### Post by PoopyTheJ on 2009-02-18
I got this error when the system crashed...


```
Feb 18 20:41:51 poopythej-desktop kernel: [   76.266246] UDF-fs: No VRS found
```

Kern.log shows...

```
kernel: [   76.266246] UDF-fs: No VRS found
kernel: [   76.288389] ISO 9660 Extensions: Microsoft Joliet Level 3
kernel: [   76.289099] ISOFS: changing to secondary root
```

---

### Post by PoopyTheJ on 2009-04-21
I have to ressurect this thread since it's still happening. Any time I try to burn a DVD the system hard locks, HDD light stays solid DVD light is solid and DVD is spinning like mad, and system is totally frozen. Windows burns DVD's just fine and I can burn cd's fine in ubuntu but not DVD's. Anyone got anything? Below are system log messages...

```
Apr 21 21:51:05 poopythej-desktop NetworkManager: <debug> [1240365065.696288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_empty_cd_r'). 
Apr 21 21:53:35 poopythej-desktop NetworkManager: <debug> [1240365215.666256] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_empty_cd_r'). 
Apr 21 21:54:06 poopythej-desktop kernel: [19195.752359] cdrom: This disc doesn't have any tracks I recognize!
Apr 21 21:54:06 poopythej-desktop NetworkManager: <debug> [1240365246.395787] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_empty_dvd_plus_r'). 
```

Kernel Log...
```

Apr 21 20:21:20 poopythej-desktop kernel: [13638.219964] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2680, err_flag:40
Apr 21 20:32:49 poopythej-desktop kernel: [14326.736717] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2680, err_flag:40
Apr 21 21:45:49 poopythej-desktop kernel: [18700.021340] atl1 0000:02:00.0: hw csum wrong, pkt_flag:2680, err_flag:40
Apr 21 21:50:34 poopythej-desktop kernel: [18984.213794] atl1 0000:02:00.0: hw csum wrong, pkt_flag:1600, err_flag:80
Apr 21 21:51:05 poopythej-desktop kernel: [19015.453009] cdrom: This disc doesn't have any tracks I recognize!
Apr 21 21:54:06 poopythej-desktop kernel: [19195.752359] cdrom: This disc doesn't have any tracks I recognize!
```

---

