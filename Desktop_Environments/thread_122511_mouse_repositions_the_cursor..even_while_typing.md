---
title: "mouse repositions the cursor..even while typing"
date: 2006-01-27
forum: Desktop Environments
---

### Post by byen on 2006-01-27
Hey guys,
Before I start..I know some of you might think this is a hardware issue but it is not. I remember reading in a post (I so wish i could find it) where you can fix it by customizing the mouse options. SO here goes...

Ok. I have a synaptics touch pad and a usb mouse, both of which worked out of the box. But while typing, the cursor somehow resets itself to the postion where the mouse pointer is..  this is really getting annoying and I really hope someone knows how to fix this.

thanks guys.

---

### Post by dcstar on 2006-01-28
[QUOTE=byen]Hey guys,
Before I start..I know some of you might think this is a hardware issue but it is not. I remember reading in a post (I so wish i could find it) where you can fix it by customizing the mouse options. SO here goes...

Ok. I have a synaptics touch pad and a usb mouse, both of which worked out of the box. But while typing, the cursor somehow resets itself to the postion where the mouse pointer is..  this is really getting annoying and I really hope someone knows how to fix this.

thanks guys.[/QUOTE]
Typing in what application(s)?

---

### Post by byen on 2006-01-28
anything... for instance while I post something in this very site.. while typing the mouse repositions itself to another point where the mouse cursor is.. not just in web pages... Oo, gaim... you name it.
Its just so annoying... Hope someone knows an answer to this....

---

### Post by El Kabong on 2006-01-28
so what you're saying is, the text cursor (the little blinking line from which you type) moves to where the mouse cursor (the little arrow that moves when you move the mouse) is?

I know this may sound stupid, but when you type, watch where your thumbs go. I have a touchpad as well, and I had to break the habit of resting my thumbs while I type. My thumb would touch the pad, thus moving the cursor to wherever the mouse was. This may not be your problem, but just my .02

---

### Post by byen on 2006-01-28
thanks for the suggestion El Kabong. I actually thought about this and infact I disabled my synaptic touch pad since Im using an external mouse..but still no good!!! I dont know why this happens but with my term papers due next week... I really hope I fix this...
If anyone has any suggestions... please let me know!!!!

thank you for your time fellas,
~byen

**_EDIT:UPDATE_**
Just Incase someone ends up in this thread while searching on a similar issue. I found  way to fix this by disabling tapping. Now, the flip side of this method is that you would not be able to use the tap feature to click something using the touchpad. Instead you will have to use the left and right mouse buttons that come along with the touch pad.
here is what I did:
open terminal>type>sudo gedit /etc/X11/xorg.conf
go to>Input Device / or wherever your mouse section is and add the following
```
Option 		"MaxTapTime" "0"
```

Well... thats it. Restart X and see the difference. Goodluck!

---

