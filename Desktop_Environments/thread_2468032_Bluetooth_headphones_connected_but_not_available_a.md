---
title: "Bluetooth headphones connected but not available as output device"
date: 2021-10-16
forum: Desktop Environments
---

### Post by fbarcelo on 2021-10-16
Hi everyone, I've just update my laptop with clean reisntall to ubuntu to 21.10
I'm glad with the changes but found an issue with my bluetooth headphones
They were detected and connected as bluetooth device without any issue, but sound output options list doesnt show the headphones as an option

[ATTACH=CONFIG]289288[/ATTACH][ATTACH=CONFIG]289289[/ATTACH][ATTACH=CONFIG]289290[/ATTACH]

Any clue?

---

### Post by jeremy31 on 2021-10-16
Post results from terminal for ```
pactl list short | grep blue
```

---

### Post by fbarcelo on 2021-10-16
Suddenly started to work without doing nothing after a reboot, anyway, here is the required output

pactl list short | grep blue
7	module-bluetooth-policy		
8	module-bluetooth-discover		
9	module-bluez5-discover		
27	module-bluez5-device	path=/org/bluez/hci0/dev_17_07_07_13_0C_33 autodetect_mtu=0 output_rate_refresh_interval_ms=500 avrcp_absolute_volume=1	
3	bluez_sink.17_07_07_13_0C_33.a2dp_sink	module-bluez5-device.c	s16le 2ch 44100Hz	RUNNING
4	bluez_sink.17_07_07_13_0C_33.a2dp_sink.monitor	module-bluez5-device.c	s16le 2ch 44100Hz	IDLE
2	bluez_card.17_07_07_13_0C_33	module-bluez5-device.c

---

