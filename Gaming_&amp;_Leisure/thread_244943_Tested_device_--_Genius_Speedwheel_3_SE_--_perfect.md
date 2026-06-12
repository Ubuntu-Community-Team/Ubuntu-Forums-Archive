---
title: "Tested device -- Genius Speedwheel 3 SE -- perfect"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by avilella on 2006-08-27
Hi all,

This is to report that this device works fine under Dapper. Tested playing [http://torcs.sf.net](http://torcs.sf.net).

Genius Speedwheel 3 SE (~$30)
Bus 002 Device 003: ID 0458:3016 KYE Systems Corp. (Mouse Systems)

AXIS0-0 Left/right Wheel
AXIS1-0	Throttle/Brake

8 buttons. Works like a charm.

under Linux Ubuntu 6.06 Dapper

Calibration is needed:

sudo apt-get install joystick
jscal /dev/input/js0 -c
(follow instructions)

Then calibrate it again under torcs.

---

