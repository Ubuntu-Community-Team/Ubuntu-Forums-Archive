---
title: "aftter upgrade to 10.04 buttons on mouse intermitent"
date: 2011-03-27
forum: Desktop Environments
---

### Post by rocket777 on 2011-03-27
I've just upgraded from 9.04 to 9.10 then to 10.04. Everything seemed to be working just fine before the last upgrade. I've got a 32 bit system. I'm using an acer 32 in monitor and it seems to recognize it quite well. I've tried several resolutions.

The problem is that now the left mouse button quite often stops working. The pointer moves fine and the right mouse button seems to work most of the time but it too fails. By fail, I mean ignored on a press down. If I then use the keyboard to tab from button to button, often the mouse buttons will begin to work again, but not always.

I get the same result coming in with a remote desktop, so I can rule out the hardware, although I'm using a usb mouse.

Sometimes a dialog in front is ignored, while some buttons in the windows below it will work. Sometimes moving the mouse over something (e.g. a button) will make the button change colors, other times nothing at all happens. 

Any ideas? upgrade manager doesn't show anything. How can I upgrade to 10.10 to see if that fixes this.

---

### Post by Krytarik on 2011-03-28
I recommend to stick with 10.04, because 10.10 has much more issues/bugs than it, and it will also be supported (updates) for 3 years, because it's a LongTermSupport version, whereas 10.10 will be supported for only 18 months.

Are you running Compiz (desktop effects)? If so, does the issue disappear when you replace it with Metacity:
- press Alt+F2
- enter:
```
metacity --replace
```

---

### Post by rocket777 on 2011-03-29
update:

I've went to a wired ps2 mouse and so far it's working (but only 10 minutes so far). I'm pretty sure the usb mouse is working though. I'll have to try it on another computer. Also, I installed temp monitors and all looks fine with temp and voltages. I put in a new battery in the usb mouse and it had no effect. So far, however, my problems seem to start after about 10 minutes of use (reboot don't help). I'll have to see what goes with this other mouse. But when the mouse didn't work, neither did my keyboard - couldn't even do control-alt-delete to shut it down. The keyboard is wired.

update2:

usb mouse works perfectly on my windows xp system. I'm using it now. Wired mouse still working on 10.04, so it's looking like that's the problem. When the usb mouse was failing earlier today, i could run with remote desktop and get the mouse to function. Don't know why it would act up after some time unless the system was heating up or something. Maybe my MB usb ports aren't working well. Dunno.

---

### Post by phil02 on 2011-03-29
I think I see the same thing on 10.10 on a Thinkpad R40 with Radeon mobility 7500 graphics.  It seems the focus of the mouse is behaving oddly as you can drag and select things but clicking on it doesn't work.  Also, I have two monitors enabled.

Perhaps, it's a recent update the broke things?  I think it was working ok before.

As for compiz, I have desktop effects disabled.

---

### Post by rocket777 on 2011-03-29
I have an asus mb, p5kpl-cm, e7400 core2duo. Running 32 bit with 2.5 gigs.

I left a hd video running over and over for the last hour not a miss with the hard wired ps2 mouse.

I also have been using the same usb mouse for an hour on my xp machine, not a hiccup.

I think this nails it. I can live with the wired up mouse, so for what it's worth, hope someone can fix this for people w/o a ps2 mouse port.

---

### Post by Krytarik on 2011-03-29
> **rocket777 said:**
> hope someone can fix this for people w/o a ps2 mouse port.
In fact, I'm using a wireless USB trackball, and wired USB mouse. And my mom is using a wireless USB mouse. Both with Ubuntu 10.04.

Sorry, I've no real idea why it behaves that way at your system, it may have something to do with your mouse model.

---

