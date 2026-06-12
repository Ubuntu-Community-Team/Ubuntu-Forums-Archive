---
title: "Dell E6400 trackpoint issue"
date: 2009-09-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gabox01 on 2009-09-13
Hi!

I have a Dell E6400 notebook.

Today, i have installed ubuntu 9.04, have the same issue that i had with 8.04.

The trackpoint is not working perfectly, sometimes the cursor jumps randomly on the screen, and it is very unusable.

I'm supprised that the issue is still exists, on the current version of ubuntu.

Anyone else noticed the issue?

---

### Post by Gabox01 on 2009-09-25
Come on, i can't belive you don't have it.:confused:

---

### Post by Gabox01 on 2009-09-25
update:

The trackpoint itself working great. The problem comes up only, when i hold the left or right buttons while using the trackpoint.

---

### Post by creolbuay on 2009-10-10
I have the problem however for me it is with the pointing stick. It works for a couple of seconds hen just locks and goes bananas. I then have to start using the touchpad which causes really random bad things to happen. Things like the pointer jumping all over the place clicking on stuff, closing windows, pasting stuff if there is somewhere to paste in. 

Here is some info:

Desktop$ xinput list
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
"HID 413c:8157"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=5	[XExtensionPointer]
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
"DualPoint Stick"	id=6	[XExtensionPointer]
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
"AlpsPS/2 ALPS DualPoint TouchPad"	id=7	[XExtensionPointer]
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

If someone can provide some assistance, that would be awesome. If more info is needed please let me know.  Thanks in advanced.

---

### Post by Gabox01 on 2009-10-11
up

---

### Post by dj-svan on 2009-11-17
Oh - i have this problem as well. I have a Latitude D810 which is a great laptop, but im missing the feature in Windows where i can disable the stick and left/right buttons below the spacebar.

Now, i love ubuntu, but i do get frustrated watching the mouse racing all over the screen.

Now, there must be some of you guys out there who has seen the problem before and can come up with a solution for both me and Gabox01

Frank

---

### Post by teward on 2009-11-17
Got a Dell Latitude E6500.  Same problem, can't use the trackstick and touch the touchpad at the same time... fi I do, it basically opens the gates of hell on my computer.

I just don't touch the touchpad.  been looking for a solution to this myself, and haven't found one.

---

### Post by fierywater on 2009-11-19
I have the same issue on my Dell E4300. Like TrekCaptainUSA said, hitting both at the same time unleashes the gates of Hell. Technically speaking, it appears to cause the Synaptics driver that Ubuntu uses for the touchpad to crash/unload. The Touchpad settings tab completely disappear from the Mouse settings applet and no other applications can find the driver.
```
sudo modprobe -r psmouse
sudo modprobe psmouse
``` The above set of commands successfully returns things back to normal without a reboot. I'm not sure what the issue is, though. It happens even if I disable the touchpad through HAL or through some GUI utility.

I would love it if it could be corrected somehow, though, as it's really the only major bug I'm running into. I'm running 9.10, by the way.

---

### Post by teward on 2009-11-19
Perhaps it links back to some incompatibilities between the Dell BIOS and Ubuntu...  Whatever the reason, I hope a solution comes up soon.

---

### Post by dj-svan on 2009-11-23
> **fierywater said:**
> I have the same issue on my Dell E4300. Like TrekCaptainUSA said, hitting both at the same time unleashes the gates of Hell. Technically speaking, it appears to cause the Synaptics driver that Ubuntu uses for the touchpad to crash/unload. The Touchpad settings tab completely disappear from the Mouse settings applet and no other applications can find the driver.
```
sudo modprobe -r psmouse
sudo modprobe psmouse
``` The above set of commands successfully returns things back to normal without a reboot. I'm not sure what the issue is, though. It happens even if I disable the touchpad through HAL or through some GUI utility.

I would love it if it could be corrected somehow, though, as it's really the only major bug I'm running into. I'm running 9.10, by the way.

Now, i have tried this as well, but it does not help. The best thing to do is to disable the stick, and then use an external mouse - however it is anoying. When using the Windows 7 i just disable the stick and use the touchpad instead.

Anyway, from what i can see - this problem has been around since 2006, so im really wondering why any of you computerskilled guys havent found a solution for this.

My best regards 

Frank

---

### Post by teward on 2009-11-23
> **dj-svan said:**
> im really wondering why any of you computerskilled guys havent found a solution for this.

My thoughts on this statement:  Don't yell at the people helping you out on these forums, most of us aren't the developers.  Have the **developers** find a fix.

---

### Post by dj-svan on 2009-11-24
> **TrekCaptainUSA said:**
> My thoughts on this statement:  Don't yell at the people helping you out on these forums, most of us aren't the developers.  Have the **developers** find a fix.


Sorry - i did not mean to yell at the people at the forums - im just wondering why Ubuntudevelopers havent made somekind of software helping Dell laptop users as i thought ubuntuforums also were used by the developers.

Now - i am pleased with any help (on any topic) :D

Frank

---

### Post by dj-svan on 2009-11-26
Wuhuuuuu...  i found out - or Kevin Read found out.

[http://kevin-read.com/blog/2009/10/11/disable-dualpoint-stick-dell-latitude-e6500/]("http://kevin-read.com/blog/2009/10/11/disable-dualpoint-stick-dell-latitude-e6500/")

xinput set-int-prop “DualPoint Stick” “Device Enabled” 8 0 

(you might have to replace 8 with 16 or 32).

Please remember to do a "cat /proc/bus/input/devices" first (without qoutations)

Regards 

Frank

---

### Post by fierywater on 2010-01-16
Unfortunately, disabling the device that way doesn't stop the buggy behavior that can result if you hit the one you disabled enough by accident. You can still cause the driver to crash by hitting both the trackpoint and the touchpad simultaneously (by accident, obviously) at the same time.

---

### Post by k_read on 2010-01-28
> **dj-svan said:**
> Wuhuuuuu...  i found out - or Kevin Read found out.

[http://kevin-read.com/blog/2009/10/11/disable-dualpoint-stick-dell-latitude-e6500/](http://kevin-read.com/blog/2009/10/11/disable-dualpoint-stick-dell-latitude-e6500/)

xinput set-int-prop “DualPoint Stick” “Device Enabled” 8 0 

(you might have to replace 8 with 16 or 32).

Please remember to do a "cat /proc/bus/input/devices" first (without qoutations)

Regards 

Frank

Nice to hear that the posting helped you.

Regarding the lockup when using both input devices at the same time: There is something really weird going on with the Latitude E6500/E6400. I seriously hope that somebody proficient with the ALPS touchpad looks into this. This laptop is driving me nuts with random lockups, many of them related to attaching new hardware (i.e. when plugging in headphones) or sleep/wakup related.
I can only urge prospective buyers to stay away from the machine, I have had a lot of hard to pin down random lockups and slowdowns.

Regards,

Kevin

---

### Post by zman58 on 2010-02-01
On my E6400 I use a USB mouse. I have BIOS set to Serial Mouse. This prevents the touchpad and trackpoint from functioning. My pointing device is only the USB mouse and the system seems to work perfectly well. Actually I have used both USB and Wireless USB mice on the system and either will function perfectly.
Hopefully the developers will correct the problem with the trackpoint/touchpad. Until then just set bios to "Serial Mouse" and use an external mouse.

---

### Post by fierywater on 2010-03-09
Has this been reported as a bug yet? I'd do it myself, but I don't have Ubuntu installed on my E4300 at the moment and it's been a while since I've dealt with it. Honestly, this is the one thing keeping me from using Ubuntu full time on my laptop.

---

