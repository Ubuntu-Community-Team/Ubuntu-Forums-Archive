---
title: "occassional flickering screen and blanks connected to LCD TV"
date: 2010-05-16
forum: Desktop Environments
---

### Post by CJ_Hudson on 2010-05-16
Hi,
I just connected my LCD TV to my desktop and now I get two things happening which I didn't get when I used a proper monitor:

the screen scrolls down and sort of flickers every minute or so, plus: 
every few minutes it goes competely 'blank' i.e. reverts to the blue screen of my TV when there is no signal.

Please, could anyone suggest something I can do to correct these annoying problems?
Thankyou.

Hey Sorry, I got the wrong category. It should be in Ubuntu NOT Kubuntu!

---

### Post by Zorael on 2010-05-17
It may be a hardware issue or incompatibility between your graphics card and the TV itself. Do you have any other (graphics card/TV) combination you could try?

You could also check the output of '**dmesg | tail**' entered in a terminal after one such flickering/blue screen, and see if any video errors are output there.

I'm guessing a bad cable could also cause this, perhaps causing the signal voltage in the cable to go below the TV's minimum threshold, making it think the connection was severed or interrupted.

---

### Post by CJ_Hudson on 2010-05-17
Thanks that's very helpful. 

Also, I have observed that with the same TV/desktop configuration I do not get the same flickering/blue screen when using Windows.

Any other helpful/informative suggestions would also be gratefully received.

Oh, and I forgot to mention, my cable MIGHT be the cause because it is fairly long (about 2 metres).

Whoa! It has now flickered once whilst in Windows with extended use.

---

### Post by Zorael on 2010-05-17
What videocard is this? Open or proprietary driver?

Again, do give '**dmesg | tail**' a check after getting any symptoms.

There may be something output to the X logs at **/var/log/Xorg.0.log**, too.

---

### Post by CJ_Hudson on 2010-05-19
It is the standard built-in Intel integrated graphics chip, plus whatever drives come normally with Ubuntu. Sorry I can't be more specific, I don't know.
And sorry but I don't know how to get that upright 'bar' symbol in the dmesg command. It isn't on my keyboard.

Actually,the fault now seems to have fixed itself without my having done anything!. How mysterious. Thanks for you assistance Zorael.

By the way I have an Asus, an ECS 945G-M3 (Intel 945G Express, Viiv Ready) motherboard with integrated Intel graphics i.e Gigabyte GA-945GM-S2 945G Express Core 2 Duo motherboard, apart from the fact that mine differs because it has memory expansion slots for two further memory cards (up to 4 GB).

In fact, I had been thinking of upgrading my graphics and memory chip. Any clues as to which ones are preferable from a Linux Ubuntu perspective (sorry I know this is in the wrong section, perhaps the mods would be so kind as to move it into the Ubnuntu section?!) It takes a a discreet PCIe graphics card.

---

