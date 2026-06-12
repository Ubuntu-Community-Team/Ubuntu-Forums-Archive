---
title: "Bluetooth DualShock3 has incorrect mappings in 15.10"
date: 2015-11-21
forum: Gaming &amp; Leisure
---

### Post by james-arlow on 2015-11-21
I've tested this scenario with two dual shock controllers on two different 15.10 (wily) installs.  The same issue appears with both controllers on both systems.

Using a wired connection, the DS3 controllers behaves mostly as expected.

* The lights flash when connected, before the controller is activated.
* The lights turn off and the controller is activated when the PS button is pressed.
* The PS button opens big picture mode in Steam.
* Games detect the controller
* Buttons are mapped as expected (same positions as an xbox controller).
* The device path is a standard value: /dev/input/js0
* jstest-gtk shows the device name as: Sony PLAYSTATION(R)3 Controller
* jstest-gtk can be used to verify the axis and buttons events / mappings (Select = 0, R3 = 2, PS = 16, X = 14)

After pairing the controller via the `System Settings -> Bluetooth -> +`:

* DIFFERENT LIGHTS: The controller port light correctly indicates the controller mapping (light 1 -> js0, etc)
* SAME PATH: The device path is the same: /dev/input/js0
* DIFFERENT NAME: jstest-gtk shows the device name as: PLAYSTATION(R)3 Controller
* jstest-gtk visual feedback shows the same buttons being triggered as a wired connection. (Select = 0, R3 = 2, PS = 16, X = 14)
* The PS button DOES NOT open big picture mode in Steam.
* Buttons are mapped wrong in-game: Select acts as X; R3 acts as Square

The Bluetooth connection correctly detects the controller as a joystick, and the mappings for the controller appear the same in jstest.  In game, however, the bluetooth connected controller is mapped completely differently from the same controller over a wired connection.

Any idea how to fix this?

---

### Post by james-arlow on 2015-11-21
I used jscal-store to write the mappings file to /var/lib/joystick/joystick.state.

[ATTACH]265712[/ATTACH]

This verifies my observations about the device name, and that the joystick mappings are the same.  I'm still not clear on why the effective mappings of the controller are different.

---

