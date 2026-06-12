---
title: "Wired Controller Not Responding"
date: 2014-02-12
forum: Gaming &amp; Leisure
---

### Post by dragonboss on 2014-02-12
So, I have a Razer Sabretooth wired controller and it was working perfectly for gzdoom(brutal mod) after setting up xboxdrv and blacklisting xpad. One reboot later it doesnt even get detected anymore(it does show up in lsusb but the controller turns on then off again after 2 seconds) and it's not the controller cause it is my main for my 360.

Also, gzdoom is still detecting input and going crazy even when the controller is not connected. Dmesg is filled with this:
```

[40667.737257] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40667.789217] evbug: Event. Dev: input5, Type: 3, Code: 0, Value: -90
[40667.789221] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -702
[40667.789224] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40667.841228] evbug: Event. Dev: input5, Type: 3, Code: 0, Value: -90
[40667.841232] evbug: Event. Dev: input5, Type: 3, Code: 1, Value: 648
[40667.841235] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -738
[40667.841237] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40667.893247] evbug: Event. Dev: input5, Type: 3, Code: 1, Value: 684
[40667.893251] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40667.945273] evbug: Event. Dev: input5, Type: 3, Code: 0, Value: -72
[40667.945277] evbug: Event. Dev: input5, Type: 3, Code: 1, Value: 684
[40667.945280] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -756
[40667.945282] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40667.997287] evbug: Event. Dev: input5, Type: 3, Code: 0, Value: -90
[40667.997291] evbug: Event. Dev: input5, Type: 3, Code: 1, Value: 648
[40667.997294] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -738
[40667.997296] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40668.049325] evbug: Event. Dev: input5, Type: 3, Code: 0, Value: -54
[40668.049331] evbug: Event. Dev: input5, Type: 3, Code: 1, Value: 630
[40668.049338] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -720
[40668.049341] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40668.101476] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -720
[40668.101482] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40668.153481] evbug: Event. Dev: input5, Type: 3, Code: 0, Value: -90
[40668.153488] evbug: Event. Dev: input5, Type: 3, Code: 1, Value: 666
[40668.153492] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -738
[40668.153495] evbug: Event. Dev: input5, Type: 0, Code: 0, Value: 0
[40668.189945] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 28
[40668.189980] evbug: Event. Dev: input3, Type: 1, Code: 28, Value: 1
[40668.189982] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0
[40668.205459] evbug: Event. Dev: input5, Type: 3, Code: 0, Value: -90
[40668.205467] evbug: Event. Dev: input5, Type: 3, Code: 2, Value: -666
```

---

### Post by dannyboy79 on 2014-02-12
run jstest-gtk and see if it's spitting stuff out. if so, one of the analog sticks is most likely stuck in a non-zero location. the computer thinks it's receiving information constantly from the controller.

---

### Post by dragonboss on 2014-02-12
So uh, apparently there's an accelerometer in the laptop I previously had no idea existed, being detected as /dev/input/js0.
[ATTACH=CONFIG]250292[/ATTACH]

---

### Post by dannyboy79 on 2014-02-12
most likely the touchpad

---

### Post by dragonboss on 2014-02-12
It's not the touchpad.

---

