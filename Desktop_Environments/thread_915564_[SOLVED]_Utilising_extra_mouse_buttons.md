---
title: "[SOLVED] Utilising extra mouse buttons"
date: 2008-09-10
forum: Desktop Environments
---

### Post by sternkanz on 2008-09-10
Hi, I have a logitech MX500 mouse which has two thumb buttons. In Windows XP, I can use these as "Forward" and "Back" within browsers and explorer windows. Is there any way I can configure them to do the same within Ubuntu? Even if only for Firefox and not for folders.

Thanks,

Stern

---

### Post by sternkanz on 2008-09-11
bump :)

---

### Post by kerry_s on 2008-09-11
sudo gedit /etc/X11/xorg.conf

```

Section "InputDevice"
Identifier	"Configured Mouse"
Driver		"mouse"
Option		"CorePointer"
Option		"Device"		"/dev/input/mice"
Option		"Emulate3Buttons"	"true"
Option          "Protocol" "explorerps/2"
Option          "Buttons" "7"
Option          "ZAxisMapping" "6 7"
EndSection

```

i think that should work for yours, mines a ms explorer, so it's just a little different.

---

### Post by sternkanz on 2008-09-11
So basically, I want to add the "Buttons" "7" line, and change the "ZAxisMapping" to "6 7"?

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	[COLOR="Red"]Option		"ZAxisMapping"		"6 7"[/COLOR]
	Option		"Emulate3Buttons"	"true"
       [COLOR="Red"]Option          "Buttons"               "7"[/COLOR]
EndSection
```

Thanks for helping :)

---

### Post by kerry_s on 2008-09-11
> **sternkanz said:**
> So basically, I want to add the "Buttons" "7" line, and change the "ZAxisMapping" to "6 7"?

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	[COLOR="Red"]Option		"ZAxisMapping"		"6 7"[/COLOR]
	Option		"Emulate3Buttons"	"true"
       [COLOR="Red"]Option          "Buttons"               "7"[/COLOR]
EndSection
```

Thanks for helping :)


you forgot 1
change this:
	Option		"Protocol"		"ImPS/2"
to this:
Option          "Protocol" "explorerps/2"

---

### Post by sternkanz on 2008-09-14
Ok, I'm not sure what the thumb buttons are doing now, in Firefox they do work as forward and back buttons, but in the normal folder view they seem to just select stuff while in list view or select one of the menus. I could live with that as I mainly use the forward back for Firefox anyway.

The problem is the mousewheel now scrolls left-right instead of up-down. What can I do to fix this?

---

### Post by kerry_s on 2008-09-14
> **sternkanz said:**
> Ok, I'm not sure what the thumb buttons are doing now, in Firefox they do work as forward and back buttons, but in the normal folder view they seem to just select stuff while in list view or select one of the menus. I could live with that as I mainly use the forward back for Firefox anyway.

The problem is the mousewheel now scrolls left-right instead of up-down. What can I do to fix this?

hmm,

```
Option "ButtonMapping" "1 2 3 6 7"
```

here's the how to page:
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by sternkanz on 2008-09-15
Ok, I have it working now:

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"Protocol"	"evdev"
#	Option		"Dev Name"	"Logitech USB-PS/2 Optical Mouse"
#	Option		"Dev Phys"
#	Option		"Device"
#	Option		"Buttons"	"10"
#	Option		"ZAxisMapping"	"4 5"
#EndSection

This works for "Forward" and "Back" in Firefox using the thumb buttons. The mousewheel click doesn't work but I don't use that anyway.

I was wondering if it is possible to get it to work as "Forward" and "Back" in nautilus aswell?

---

### Post by fewjr on 2008-09-16
Hello All,
     I have a question about my xorg.config > inputdevice section. This is all that is in my file:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

I do not see the options for number of buttons.My mouse is a generic mouse with a left & right buttons, a scroll wheel which can be clicked down. The only thing that is not working is the clicking of the wheel. I can scroll with the wheel but can not click the wheel to for example, bring up the little 4-way arrow in a webpage which allows me to scroll by moving the mouse up & down. According to the "ManyButtonsMouseHowto" this type of mouse is considered a 5 button mouse and should be working by default in a Gnome environment. Just wondering why I have no button options and what I should change in the file.
                                           Thanks
                                            fewjr

---

### Post by sternkanz on 2008-09-21
@fewjr

When I was figuring out how to get my Logitech MX500 to work, I often added or removed lines from the default InputDevice section. My understanding is that most of the options revert to a default value if they are not specified within that section. For example, the 'Buttons' option may revert to 4 to allow for left and right click, and up and down scroll.

You should just play around with it and see what works for you. As always make a backup of the xorg.conf in case something breaks and you need to recover it, which is a fairly straightforward operation. I found the right configuration for my mouse mainly by looking for examples of other people that had my mouse, and then slightly altering them. So if you do a google (or search on these forums) for your particular mouse model, you may find something useful.

Good luck, Stern

---

