---
title: "USB output voltage"
date: 2005-12-12
forum: Desktop Environments
---

### Post by N8MAN1068 on 2005-12-12
This is something I just noticed this past weekend.
I had to hook my Blackberry 7520 into a usb cable to charge it up. Doing so, it seemed like it took several hours to get a full charge, whereas it only takes an hour on my office machine running XP Pro.

I know 'seemed like' isn't scientific data, so i'm going to give it a shot in a day or so when the battery runs low to find out how long it takes.

I've also noticed this slower recharge when charging my Palm T|E.
Is there anywhere to check to see what the output voltage is?
Maybe this weekend I'll play Brickbreaker with the screen light on full to kill the battery and run it through charging using a different usb port.

---

### Post by earobinson on 2005-12-12
No clue but it would be intresting to find out, Post your results!

---

### Post by M3ta7h3ad on 2005-12-12
If you have a usb cable you can waste and a multimeter give it a go properly :) it'll be rather wierd if it does!

---

### Post by earobinson on 2005-12-12
[QUOTE=M3ta7h3ad]If you have a usb cable you can waste and a multimeter give it a go properly :) it'll be rather wierd if it does![/QUOTE]
Im not sure i understand that

---

### Post by M3ta7h3ad on 2005-12-12
Chop the end of a usb cable off.

Plug the other end into the pc.

Place the ground probe of the multimeter to the ground of the USB cable.

Place the positive probe of the multimeter to the 5v line on the USB cable.

Set your multimeter on VDC and the appropriate scale, and watch the voltage output.

Then try the same only in windows.

---

### Post by earobinson on 2005-12-12
[QUOTE=M3ta7h3ad]Chop the end of a usb cable off.

Plug the other end into the pc.

Place the ground probe of the multimeter to the ground of the USB cable.

Place the positive probe of the multimeter to the 5v line on the USB cable.

Set your multimeter on VDC and the appropriate scale, and watch the voltage output.

Then try the same only in windows.[/QUOTE]
ahhhhhh, way to smart for me.

---

### Post by M3ta7h3ad on 2005-12-12
pah! nonsense! :) you'd understand what I mean after 10mins of fiddling :)

I just mean if you have the equipment handy and a spare cable, you could do it "scientifically" :) if not just a simple timed charge would work too :)

---

### Post by N8MAN1068 on 2005-12-13
yeah...not enough time to be doing all that.
I fried my multimeter years ago.
Maybe i'll pick a new one up next time I'm at Sears.

Ok..took 2-2.5 hours to charge on a XP Pro laptop.
Now to wait a day or two and try on my Ubuntu desktop.

The kicker is that I gotta make it go dead between a certain time frame. This is my work phone and all server sms messages for alerts get sent to it, so if I miss something, I could be in deep-doody the next morning.

Another possible scenario for Ubuntu is to:
1: Initiate charge while PC has been up for some time. Record charge time.
2: Plug in blackberry with just enough juice to stay on, reboot PC so that Ubuntu sees it as an active device (a la some digital cameras/other devices).
Maybe Ubuntu is feeding just enough voltage to read that it's recving power, but not fully aware that the device is there?

---

### Post by jimmy41 on 2005-12-13
if we were to be scientific-ish....

we'd have to use the same machine to both outputs on.  It could be a voltage difference between a laptop and a desktop.

---

### Post by earobinson on 2005-12-13
meh, beggers cant be chosers.

---

### Post by mcduck on 2005-12-13
USB provides +5V all the time when computer is switched on, but the current is limited and hardware plugged into USB port has to tell your system that it needs more than minimum.

So I suppose your problem is that Linux doesn't recognize your hardware properly and therefore doesn't give it more than minimum current and that makes your charging times longer.

edit. yes, the standard actually allows voltage to vary between 4,4V and 5,25V, but the impact of current is the one that makes the diference. I'm not sure how to solve that, but perhaps using a self-powered USB-hub would give you higher current even when your computer doesn't.. If you can borrow one from somebody it might be worth a try..

---

### Post by N8MAN1068 on 2005-12-16
Could be.
Came home last night. Blackberry 7520 had 1 bar of power out of 5. Plugged it in, made sure the charge symbol came on, then turned it off.
12hrs later, it has only gone up to the 4th bar...1 bar left and then some.

Using Gkrellem, my +2.5V is=0.36
I/O=3.49
Not sure if I/O is voltage, but the wall charger is 5.0V. So if I/O is voltage, I'm missing 1.51V of output.

I've got 5.10 on a laptop, i'll try that this weekend, as well as a self powered usb hub.

---

### Post by davidsrsb on 2005-12-16
First be very careful, I have damaged motherboards by shorting the usb +5V as not all motherboards have proper current limiting. Boards use various chips with different current capability.
Finally your battery is probably a lithium ion which has a fully charged voltage of 4.2V. As this is quite close to the USB output voltage, the actual value is going to have quite a strong effect on charging time
I/O is nominally 3.3V in a desktop pc, nothing to do wit usb

---

### Post by N8MAN1068 on 2005-12-16
The 5v meter in gkrellem actually read 5.34volts

For kicks, I rebooted with the BB plugged in to the USB to see if that changed anything in the boot process....no change.

I guess the really only way to find out, is rig a usb cable w/ a multimeter, or reinstall XP which defeats the purpose of going to linux in the 1st place.

Not that this is a big deal or anything...just a quirk.

---

### Post by earobinson on 2005-12-16
Thanks for all the info guys n gals

---

### Post by pksings on 2005-12-16
There is also a serious current difference between USB-1 and USB-2. USB-2 has LOWER current specs. My USB attached Harddrive will spin up and run just fine on USB-1 but requires an external power adapter with USB-2. It draws One Amp (1.0A) (amperes) of current.

PK

---

### Post by davidsrsb on 2005-12-19
I think that USB high power devices have never been meant to draw more than 500mA.

---

### Post by briancurtin on 2005-12-20
[QUOTE=jimmy41]if we were to be scientific-ish....

we'd have to use the same machine to both outputs on.  It could be a voltage difference between a laptop and a desktop.[/QUOTE]
i was about to mention the same thing. this is a pretty interesting thread

---

### Post by N8MAN1068 on 2006-01-17
heh...if I had broadband @ home, I'd reload XP and try; but since I'm on dialup i'll refrain.
I have a spare laptop I could try on though.

---

### Post by aosmith on 2006-12-06
check this post:
[http://www.ubuntuforums.org/showthread.php?t=314003]("http://www.ubuntuforums.org/showthread.php?t=314003")

---

