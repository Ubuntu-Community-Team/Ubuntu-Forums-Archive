---
title: "Can't scroll with touchpad"
date: 2016-01-14
forum: Desktop Environments
---

### Post by someone2353 on 2016-01-14
Hi,
After a fresh install of Xubuntu 15.10 my two-fingers scroll doesn't work. I've tried to run ```
synclient VertEdgeScroll=1
``` but the output is ```
Couldn't find synaptics properties. No synaptics driver loaded?
```.
I also tried to install gpointing-device-settings, but when I run it I get ```
Segmentation fault (core dumped)
```
Any suggestions?

---

### Post by vasa1 on 2016-01-14
> **someone2353 said:**
> Hi,
After a fresh install of Xubuntu 15.10 my two-fingers scroll doesn't work. ...
Any suggestions?
Do all other touchpad functions work?

To start, you could post the output of ```
xinput list --long
``` and ```
synclient
``` within code tags for people to take a look at.

---

### Post by someone2353 on 2016-01-15
The output of
```
xinput list --long
```
is
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
	Reporting 7 classes:
		Class originated from: 12. Type: XIButtonClass
		Buttons supported: 13
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
		Button state:
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Vert Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 1.000000
		  flags: 0x0
		Class originated from: 12. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x2 ( preferred )


&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 4. Type: XIButtonClass
		Buttons supported: 10
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" None None None
		Button state:
		Class originated from: 4. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative
		Class originated from: 4. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 0 units/m
		  Mode: relative


&#9116;   &#8627; ASUS Tech Inc. ASUS HID Device          	id=14	[slave  pointer  (2)]
	Reporting 24 classes:
		Class originated from: 14. Type: XIButtonClass
		Buttons supported: 5
		Button labels: "Button Unknown" "Button Unknown" "Button Unknown" "Button Wheel Up" "Button Wheel Down"
		Button state:
		Class originated from: 14. Type: XIKeyClass
		Keycodes supported: 248
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Abs MT Position X
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 960.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Abs MT Position Y
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 540.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Abs MT Pressure
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Abs MT Distance
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 4:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 5:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 6:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 7:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 8:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 9:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 10:
		  Label: Abs Misc
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 11:
		  Label: Abs MT Touch Major
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 12:
		  Label: Abs MT Touch Minor
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 13:
		  Label: Abs MT Width Major
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 14:
		  Label: Abs MT Width Minor
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 15:
		  Label: Abs MT Orientation
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 16:
		  Label: Abs MT Tool Type
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 17:
		  Label: Abs MT Blob ID
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 18:
		  Label: Abs MT Tool X
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 19:
		  Label: Abs MT Tool Y
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XIValuatorClass
		Detail for Valuator 20:
		  Label: None
		  Range: 0.000000 - 255.000000
		  Resolution: 0 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 14. Type: XITouchClass
		Touch mode: direct
		Max number of touches: 10


&#9116;   &#8627; ASUS Tech Inc. ASUS HID Device          	id=15	[slave  pointer  (2)]
	Reporting 5 classes:
		Class originated from: 15. Type: XIButtonClass
		Buttons supported: 7
		Button labels: "Button Left" "Button Unknown" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
		Button state:
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 15. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Vert Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 15. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x2 ( preferred )


&#9116;   &#8627; ELAN1000:00 04F3:0401                   	id=16	[slave  pointer  (2)]
	Reporting 5 classes:
		Class originated from: 16. Type: XIButtonClass
		Buttons supported: 7
		Button labels: "Button Left" "Button Unknown" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
		Button state:
		Class originated from: 16. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 16. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 16. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Vert Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 16. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x2 ( preferred )


&#9116;   &#8627; ASUS ROG SICA                           	id=11	[slave  pointer  (2)]
	Reporting 6 classes:
		Class originated from: 11. Type: XIButtonClass
		Buttons supported: 7
		Button labels: "Button 0" "Button Unknown" "Button Unknown" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
		Button state:
		Class originated from: 11. Type: XIKeyClass
		Keycodes supported: 248
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 11. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 11. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 1.000000
		  flags: 0x0


&#9116;   &#8627; ASUS ROG SICA                           	id=12	[slave  pointer  (2)]
	Reporting 7 classes:
		Class originated from: 12. Type: XIButtonClass
		Buttons supported: 13
		Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right" "Button Side" "Button Extra" "Button Unknown" "Button Unknown" "Button Unknown" "Button Unknown"
		Button state:
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIValuatorClass
		Detail for Valuator 3:
		  Label: Rel Vert Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 12. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 1.000000
		  flags: 0x0
		Class originated from: 12. Type: XIScrollClass
		Scroll info for Valuator 3
		  type: 1 (vertical)
		  increment: -1.000000
		  flags: 0x2 ( preferred )


&#9116;   &#8627; Sunrex/JME Ghost Key Elimiantion Keyboard	id=9	[slave  pointer  (2)]
	Reporting 6 classes:
		Class originated from: 9. Type: XIButtonClass
		Buttons supported: 7
		Button labels: "Button 0" "Button Unknown" "Button Unknown" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
		Button state:
		Class originated from: 9. Type: XIKeyClass
		Keycodes supported: 248
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 0:
		  Label: Rel X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 1:
		  Label: Rel Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9. Type: XIValuatorClass
		Detail for Valuator 2:
		  Label: Rel Horiz Wheel
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 9. Type: XIScrollClass
		Scroll info for Valuator 2
		  type: 2 (horizontal)
		  increment: 1.000000
		  flags: 0x0


&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
	Reporting 1 classes:
		Class originated from: 10. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 5. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 6. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 7. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 8. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; USB2.0 HD UVC WebCam                    	id=13	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 13. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; Asus WMI hotkeys                        	id=17	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 17. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; AT Translated Set 2 keyboard            	id=18	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 18. Type: XIKeyClass
		Keycodes supported: 248


    &#8627; Sunrex/JME Ghost Key Elimiantion Keyboard	id=10	[slave  keyboard (3)]
	Reporting 1 classes:
		Class originated from: 10. Type: XIKeyClass
		Keycodes supported: 248

```
And the output of ```
synclient
```
is
```
Couldn't find synaptics properties. No synaptics driver loaded?
```

---

### Post by vasa1 on 2016-01-15
> **vasa1 said:**
> Do all other touchpad functions work?
...
What about ^^^.

Is your touchpad working in all other respects?

BTW, does [http://ubuntuforums.org/showthread.php?t=2305311&p=13407961#post13407961](http://ubuntuforums.org/showthread.php?t=2305311&p=13407961#post13407961) help?

Also: [http://askubuntu.com/questions/609892/touchpad-not-recognized-on-asus-n550jk-tp500l-focaltech](http://askubuntu.com/questions/609892/touchpad-not-recognized-on-asus-n550jk-tp500l-focaltech)

---

### Post by someone2353 on 2016-01-15
My touchpad works fine, except scrolling. The folkatech-dkms didn't help

---

### Post by monkeybrain20122 on 2016-01-15
The second answer here may help your "no synaptics driver loaded?" problem. [http://askubuntu.com/questions/397677/synaptics-drivers-are-not-loading-on-kubuntu-13-10-on-dell-vostro-2420](http://askubuntu.com/questions/397677/synaptics-drivers-are-not-loading-on-kubuntu-13-10-on-dell-vostro-2420)

After creating xorg.conf, reboot then run the command
```
synclient VertEdgeScroll=1
```
again.

This fixed my touchpad scrolling problem on Fedora.

---

