---
title: "Mouse problem"
date: 2011-09-24
forum: Desktop Environments
---

### Post by DanFlo on 2011-09-24
Hello,

The mouse pointer freezes for a second every 10-20 minutes.
The mouse is a steelseries kinzu and i'm running ubuntu 11.04.
Tested the same mouse on a Windows Os and there the problem doesn't exist.
Can anyone please advice.
Thanks

---

### Post by DanFlo on 2011-09-26
Anyone can please provide some tips?
Is it a usb port problem?

---

### Post by larpon on 2011-10-10
I'm using Kubuntu 11.04 - and have also recently bought a Steelseries Kinzu optical mouse - I have the exact same issue.

10-20 minutes between freezes sounds about right - although I have experienced shorter periods of random freezes as well.

Any guidance/help would be greatly appreciated.

---

### Post by appier on 2011-10-10
Does this happen when you try other mouses?

---

### Post by larpon on 2011-10-10
> **appier said:**
> Does this happen when you try other mouses?

No not from what I have experienced - I bought the Kinzu mouse (USB w/cord btw) because my old logitech (wireless but connected via USB) mouse's left button started to fail sometimes - but it never failed on movement. I haven't changed anything else in my setup beside the kinzu mouse.

Googling the issue haven't brought much up except this thread, this unanswered thread [http://kubuntuforums.net/forums/index.php?topic=3115078.0](http://kubuntuforums.net/forums/index.php?topic=3115078.0) and some other evdev driver velocity/speed based issues with X11 and Kinzu mice but didn't look like it was related to this.

At some point I though it was an issue when mixing a cordless keyboard/mouse(defunct) with the Kinzu mouse with cord. But I bought a Steelseries keyboard today which works like a charm and thus it can't be a bad cord/cordless mix

Thanks for your interest on this!

---

### Post by larpon on 2011-10-12
Alright, I might have solved this somehow (maybe only temporary?)

I've had a good few hours now with no problems after i followed this procedure to update the "firmware" (firmware updates for mice? c'mon) for the mouse from Windows:
[[COLOR="Blue"]Steelseries Kinzu FAQ[/COLOR]]("http://faq.steelseries.com/questions/136/Do+I+need+specific+software+for+the+Kinzu%3F")

After first update just pressing "Apply" in the settings tool - nothing happened when I booted back into Linux...

Then I went back to Windows and chose the least amount of Hz in the "Kinzu report rate" and sat the CPI 2 to 400.
This is how the settings tool looks like (sorry this is a stolen screenshot so the values are different here ;) ):
[IMG]http://pici.se/pictures/anEsdjUoi.jpg[/IMG]

I then tried to connect the bastard via PS2 (USB -> PS2 adapter) and rebooted back into Kubuntu... At first nothing happened (at all - mouse wouldn't move) - probably because it's not PS2 compatible (doh) - then while the machine was on I changed it back to be connected via USB.

And now I've been using it for about 5 hours with no freezes.

On the other hand I haven't tried a restart yet - so it might come back - but it seems like it's working now.

Maybe worth a try for others who have the same problem (personally I don't think the PS2 step did anything but who knows, eh?).

I'll report back if the problem persists between boots.

---

### Post by larpon on 2011-10-13
It seems like my problem is solved I've tried a reboot and the mouse is still working as expected.

---

