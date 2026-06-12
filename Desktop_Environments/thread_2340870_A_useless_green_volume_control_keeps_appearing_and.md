---
title: "A useless green volume control keeps appearing and disappearing"
date: 2016-10-22
forum: Desktop Environments
---

### Post by vivian-unger on 2016-10-22
Ever since I updated my Ubuntu to 16.10, I have seen a mysterious green bar periodically appear and disappear in the upper right corner of my screen. I'm attaching a screen shot of this bar. It looks like a volume control, but I can't do anything with it, such as adjust the volume. If I float my mouse over it, it "greys out" (or really, it becomes a lighter green).

In my efforts to make it go away (because it really is annoying) I uninstalled Pulseaudio. This did indeed make it go away, but I also lost the real volume control on my top panel. I reinstalled Pulseaudio, and neither the real nor the fake volume control came back.

After some internet searches, I found out about indicator-applet. Reinstalling it (sudo apt-get install indicator-applet) put the volume control back in my panel, but it also brought back the ghostly green volume control.

I have therefore concluded that indicator-applet is doing this--why, I don't know. It never did this before the 16.10 upgrade. I would like to discover a way to get it to stop doing this, without actually uninstalling it, since I like having a volume control in my top panel. But I will uninstall it if that's the only way to get rid of the durned thing.

Can anyone help?

---

### Post by howefield on 2016-10-23
Don't think you can easily remove the sound notification witout removing all of them but depending on how serious you are about removing it..

[http://askubuntu.com/questions/532044/how-do-i-disable-the-sound-indicator-notification-bubbles](http://askubuntu.com/questions/532044/how-do-i-disable-the-sound-indicator-notification-bubbles)

might help.

---

### Post by vivian-unger on 2016-10-24
It's a notification? What's it notifying me of? :confused:

EDIT: OK, I read the link. I'm not aware of modifying the volume when it comes up. Maybe there's some hotkey I'm unaware of that I'm pressing?

Thanks for your help, howefield!

---

### Post by vivian-unger on 2016-10-25
I just booted up this morning and the indicator came up while I had my hands completely off the keyboard. It just came up again while I was typing this message. I didn't alter the volume in any way. I think this is a bug.

Is anyone else having this problem?

---

### Post by bearlake on 2016-10-25
The only time it's noticeable here is when the volume is changed.

It seems you have a problem or a bug of one kind or another. 

If you shut off notifications, does it still happen?

---

### Post by vivian-unger on 2016-11-01
Renaming org.freedesktop.Notifications.service has stopped the volume notification. Though of course it doesn't fix whatever underlying problem is making the volume notification pop up when there's no change in volume.

---

