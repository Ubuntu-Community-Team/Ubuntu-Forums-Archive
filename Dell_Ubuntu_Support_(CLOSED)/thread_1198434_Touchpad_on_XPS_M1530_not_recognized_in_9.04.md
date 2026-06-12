---
title: "Touchpad on XPS M1530 not recognized in 9.04"
date: 2009-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Zachs Kappler on 2009-06-27
Well upgrading to 9.04 has solved a bunch of problems and limitations this laptop had with 8.04. But with any distro, new bugs will arise, but this one survived in a way. 

The touch pad has ceased functioning. It won't freak out, just sit there, motionless. The "i8042.nomux=1" kernel setting does nothing to it now. Is there another workaround? 

This hardly inconveniences me since I have a USB mouse that works, but the bug is a problem when the mouse has no surface to work on (Optical mice and reflective surfaces don't mix).

---

### Post by coffeeaddict22 on 2009-06-27
Hi Zachs,
There's been a change in the way input devices are managed from 8.04; they've moved to HAL from being part of the xorg.conf setup file.  Have a look [here at the Debian info doc on it]("http://wiki.debian.org/XStrikeForce/InputHotplugGuide") and [here on the Ubuntu wiki site]("https://wiki.ubuntu.com/X/Config/Input") for a bit more.  I think it's safe  to say that it's still early days, and the documentation is a bit light still.
Having said that, your touchpad should be being picked up.  is it showing up in ```
xinput list
```

---

### Post by Zachs Kappler on 2009-07-12
> **coffeeaddict22 said:**
> Hi Zachs,
There's been a change in the way input devices are managed from 8.04; they've moved to HAL from being part of the xorg.conf setup file.  Have a look [here at the Debian info doc on it]("http://wiki.debian.org/XStrikeForce/InputHotplugGuide") and [here on the Ubuntu wiki site]("https://wiki.ubuntu.com/X/Config/Input") for a bit more.  I think it's safe  to say that it's still early days, and the documentation is a bit light still.
Having said that, your touchpad should be being picked up.  is it showing up in ```
xinput list
```

Thanks, here is what I get
```
daniel@Egg-Carrier:~$ xinput list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Broadcom Corp"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Mouseemu virtual keyboard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Mouseemu virtual mouse"	id=7	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"AlpsPS/2 ALPS GlidePoint"	id=8	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 1 :
		Min_value is 0
		Max_value is 767
		Resolution is 1
"PS/2 Mouse"	id=9	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Broadcom Corp"	id=10	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Microsoft Basic Optical Mouse"	id=11	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
daniel@Egg-Carrier:~$ 

```

The Alps entry is the touchpad, but I'm still lost on how I can convert the xinput entry to HAL or make calls to it...

\Hasn't touched either in a year due to the editing not being needed since
\\Might explain the sudden retardation/glitch of my Bamboo Fun tablet

---

### Post by Zachs Kappler on 2009-12-02
Well consider this solved, 9.10 corrected this big issue without me having to do anything to it.

---

