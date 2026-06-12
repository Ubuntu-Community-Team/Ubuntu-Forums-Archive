---
title: "Mouse Button Config - Switch 6th and 7th Buttons"
date: 2009-05-10
forum: General Help
---

### Post by zzzBrett on 2009-05-10
I have a Kensington mouse that has side buttons that would typically be used for the "Back" and "Forward" commands in an internet browser.  They work, they're just backwards.  The button that I want to make the browser go back one page makes it go forward.


I think i'll be using the xinput set-button-map, but not sure what to have after that.

Thanks!

---

### Post by zzzBrett on 2009-05-13
bump

---

### Post by zzzBrett on 2009-05-27
Can anybody help me with this?

---

### Post by zzzBrett on 2009-05-28
bump

---

### Post by fillintheblanks on 2009-05-29
install btnx & btnx-config from synaptic

goto applications > system tools > btnx

there you can map mouse buttons and assign commands/functions to them such as ALT+Left and ALT+Right to go back and forward in your browser.

---

### Post by zzzBrett on 2009-05-31
> **fillintheblanks said:**
> install btnx & btnx-config from synaptic

goto applications > system tools > btnx

there you can map mouse buttons and assign commands/functions to them such as ALT+Left and ALT+Right to go back and forward in your browser.


Thanks for the suggestion.  I installed btnx and assigned the keys to them, but it still doesn't work.  Are there any additional installation steps that I have to complete before btnx takes effect?

Thanks,
Brett

---

### Post by zzzBrett on 2009-05-31
After a restart, btnx seemed to start working.  Now, the two buttons do allow me to go back and forward in a web browser in the correct direction, but there is still a small problem.

If the browser is at the forward-most page, and I press the button that corresponds to 'page forward', it will go back one page.  I'm thinking this is because the button still is telling the browser to go in the wrong direction, and it is also executing the Alt+Right key.  The same issue exists for going back when the browser can no longer go back.

Is there a way to disable firefox from 'listening' to these mouse buttons?

---

### Post by Frenziefrenz on 2009-06-11
I have roughly the same problem. I have configured btnx the way you can see in the attachments.

Now, the top left button results in both normal left click AND middle click (which is the default action for that button) in Firefox, and whether it's going to give precedence to the default, my setting or execute both seems to be a per application chance. The bottom left button isn't disabled at all and the other buttons also randomly stick or don't stick to their default actions. Any thoughts on what I might be doing wrong with btnx? (and yes, I'm running btnx-config and btnx with sudo)

I'm afraid that I'll have to dive into the xorf.conf file, but since it doesn't even list any settings for my mouse (Kensington Expert Mouse) to begin with, I have no idea how to go about that. :(

Any help would be greatly appreciated, especially since many other people to whom I could recommend Ubuntu (as an upgrade to XP) will also be interested in this.

Edit: 

Okay, after some further checking in the manual I noticed that [http://www.ollisalonen.com/btnx/man/x915.html#troubleshoot-xorg](http://www.ollisalonen.com/btnx/man/x915.html#troubleshoot-xorg) describes my problem. Except like I said, I don't have an inputdevice section in my xorg.conf. How do I get something that works? :/

---

### Post by tenmilez on 2009-06-11
> Some pointing devices have a strange button mapping, so need some tweaking to match X's perception of things. Such tweaking can be performed at runtime with xinput - find your device in xinput list and run xinput set-button-map <device name> 1 2 3 6 7, replacing those numbers with your required button mapping. You might be able to find it by searching for other people with the same hardware, or you might need to play around and see what works. 

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

So, the default is usually like 1 2 3 4 5, but if you map it to something like 1 2 3 5 4 then the 4th and 5th buttons will be swapped. 

Alternatively, look into xbindkeys and xmodmap. It's a little more text based configuration (actually, it's all text based configuration), but if what's been suggested already doesn't work then this might. 
The trick to this approach is that one of them is going to assign commands to the buttons and that command will call the other one passing in the function that it wants to do. That second program then takes that argument and emulates that function.

---

### Post by Frenziefrenz on 2009-06-11
What about disabling buttons, or giving them entirely different functions? xinput seems to be allow only the most basic of remapping (i.e. swapping buttons).

I couldn't find a screenshot of the Windows version of the drivers (and I don't want to bother booting it right now), but the [Mac version](http://www.apple.com/downloads/macosx/drivers/kensingtonmouseworks.html) seems to demonstrate how you can assign just about any imaginable function to anything quite well. btnx seems to be a roughly equivalent, although slightly harder to use, software.

I suppose that for myself, I could try to figure out [fdi files](https://wiki.ubuntu.com/X/Config/Input), or xmodmap, or even xinput (as limited as that one may be, it ought to be better than nothing), but both for maintainability (for me) and people who aren't me, I'd really prefer to get btnx to work. I think that all I need to do in this particular instance is disabling X.org's handling of the 4 mouse buttons to be able to customize them to my wildest fantasies in btnx. The preferred method seems to be fdi files. I'll report back if I manage to make any progress on that. Perhaps someone knows a bit more about them?

---

### Post by Frenziefrenz on 2009-06-11
Is there any way to generate a current, working FDI file for a piece of hardware? I've been trying some things in a mouse.fdi file, but even adding merely the following (which shouldn't do anything other than identify it, right?) makes my mouse go crazy.

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
	<device>
		<match key="info.capabilities" contains="input.mouse">
			<merge key="input.x11_driver" type="string">mouse</merge>

		</match>
	</device>
</deviceinfo>
```

---

### Post by Frenziefrenz on 2009-06-13
Alright, I figured out that the thing to make it work, the most important thing was to add ```
<merge key="input.x11_driver" type="string">evdev</merge>
```

Here's my annotated /etc/hal/fdi/policy/mouse.fdi file. 

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
	<device>
		<match key="info.capabilities" contains="input.mouse">
			<!-- Kensington tweaks -->
			<match key="input.originating_device" contains="usb_device_47d_1020"><!-- should only match the Kensington Expert Mouse, shouldn't be relevant if you only have one mouse attached afaik -->
				<merge key="input.x11_driver" type="string">evdev</merge><!-- have to specify this, otherwise it doesn't work-->
				<merge key="input.x11_options.Emulate3Buttons" type="string">false</merge><!-- shouldn't need this, but on a mouse with 3 or more buttons it's really just annoying if it's enabled -->
<!--				<merge key="input.x11_options.CorePointer" type="string">On</merge>--><!-- some search results suggested this enabled, but I haven't noticed any difference either way -->
				<!--
					1 = bottom left (left click)
					2 = top left
					3 = bottom right (right click)
					4 = scroll up
					5 = scroll down
					8 = top right

					the default buttonmapping is thus
				<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4 5 6 7 8</merge>

					ergo, to edit the 4 buttons, the ones to edit are (marked by x)
				<merge key="input.x11_options.ButtonMapping" type="string">x x x 4 5 6 7 x</merge>

					to swap scroll directions
				<merge key="input.x11_options.ButtonMapping" type="string">1 2 3 5 4 6 7 8</merge>

					or change any of these to 0 to disable and/or use with an alternative program like btnx
				-->
				<!-- simple remapping -->
				<merge key="input.x11_options.ButtonMapping" type="string">0 1 2 4 5 6 7 3</merge>
				<!-- disabling for use with btnx -->
				<!--<merge key="input.x11_options.ButtonMapping" type="string">0 0 0 4 5 6 7 0</merge>-->
			</match>
		</match>
	</device>
</deviceinfo>
```
To find the default button mapping I used xev, which should probably be self-explanatory. Just click & scroll on the window and watch the terminal output.

In order to get the necessary information for use in the FDI file, I had to use "lshal | less" and then use "/mouse" to make it show me the first occurrence of mouse (although "/Kensington" was more useful in my particular case).

The output of this was
```
udi = '/org/freedesktop/Hal/devices/usb_device_47d_1020_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'  (string)
  info.product = 'Expert Mouse Trackball'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_47d_1020_noserial'  (string)
  info.vendor = 'Kensington'  (string)
  linux.device_file = '/dev/bus/usb/006/012'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-3'  (string)
  usb_device.bus_number = 6  (0x6)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 12  (0xc)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-3'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Expert Mouse Trackball'  (string)
  usb_device.product_id = 4128  (0x1020)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Kensington'  (string)
  usb_device.vendor_id = 1149  (0x47d)  (int)
  usb_device.version = 1.1 (1.1) (double)

```

I have to say, all of this was really badly documented. After I finally found out about the lshal command things went fairly quickly, but it was still no fun. I hope this helps someone else, 'cause I spent way too much time trying to figure this out. I wouldn't mind adding some stuff to the wiki either, but I'm not sure about the correct writing style/way of giving examples etc.

---

