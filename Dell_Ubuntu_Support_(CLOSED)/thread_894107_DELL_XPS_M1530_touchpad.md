---
title: "DELL XPS M1530 touchpad"
date: 2008-08-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wxiluo on 2008-08-18
I've been looking around and tryin and trying to get my touch pad to work. well it works but really slowly... Like I have to swipe my finger 50 times to go from one corner to another.


Does someone know how to solve this problem?

I need your help!:KS

---

### Post by TimDaniels on 2008-08-19
In the XPS-M1330 laptop, **System|Preferences|Mouse|General tab|Pointer Speed** will set the ratio of pointer movement-to-finger movement.  It's probably the same for the M1530.

*TimDaniels*

---

### Post by lazercat on 2008-08-19
I have a similar problem, except it's quite the opposite: my XPS 1530's mousepad is unusable because it flies all over the screen and clicks on everything. Does Dell have touchpad drivers for Linux?

---

### Post by jsc1959 on 2008-08-19
add i8042.nomux=1 to /boot/grub/menu.lst like this:


title		Ubuntu intrepid (development branch), kernel 2.6.26-5-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.26-5-generic root=UUID=3ce50c52-edc5-4c07-ac1f-3e189a0f8163 ro quiet splash i8042.nomux=1
initrd		/boot/initrd.img-2.6.26-5-generic
quiet

it fixed it for me.

---

### Post by TimDaniels on 2008-08-19
> **lazercat said:**
> ...my XPS 1530's mousepad is unusable because it flies all over the screen and clicks on everything. Does Dell have touchpad drivers for Linux?

Thoroughly adequate touchpad driver(s) can be found in the standard Ubuntu installation CD file.  The driver for my M1330 laptop's touchpad was installed automatically by that installation CD.  Try the easiest thing first:  Go to **System|Preferences|Mouse|General tab|Pointer Speed** and move the slider a little way toward "Slow".  If the Sensitivity is set high, try moving the slider a little way toward "Low" to require a more positive finger pressure.  In the "Touchpad" tab, uncheck "Enable mouse clicks with touchpad".  Tapping the touchpad will then no longer be interpreted as a double-click.

*TimDaniels*

---

### Post by jespdj on 2008-08-21
You need to add the kernel boot parameter as jsc1959 explains if you have BIOS version A08 or A09. This is a known problem with the M1530 touchpad and Ubuntu.

Just changing the pointer speed isn't going to solve the problem.

See also [http://ubuntuforums.org/showthread.php?t=808164](http://ubuntuforums.org/showthread.php?t=808164)

---

### Post by lazercat on 2008-08-21
> **TimDaniels said:**
> Thoroughly adequate touchpad driver(s) can be found in the standard Ubuntu installation CD file.  The driver for my M1330 laptop's touchpad was installed automatically by that installation CD.  Try the easiest thing first:  Go to **System|Preferences|Mouse|General tab|Pointer Speed** and move the slider a little way toward "Slow".  If the Sensitivity is set high, try moving the slider a little way toward "Low" to require a more positive finger pressure.  In the "Touchpad" tab, uncheck "Enable mouse clicks with touchpad".  Tapping the touchpad will then no longer be interpreted as a double-click.

*TimDaniels*
I use a dual boot and downloaded it and put the partition in the C drive (awkward, I know. I forgot what Mubi was called at the time.). Editing mouse preferences doesn't do anything.

---

### Post by superm1 on 2008-08-21
This is a bug that was introduced in BIOS A08.  That exact quirk, i8042.nomux=1 is the current known workaround for it.  Someone who has verified that this solves the issue on A08, can you try to roll your BIOS back to A07 and see if there are any negative side effects from keeping that quirk in place on A07?  If not, then i'll submit a kernel patch to hardcode it to this model.

---

### Post by lundbymads on 2008-09-25
I have a Dell XPS M1530 and I've done the i8042.nomux=1 work-around.

It works almost perfectly. 

However, I experience a pretty annoying bug: When I'm writing text, the mousepad randomly do "ghost" clicks, without me using the touchpad, and jumps to the position of the cursor. This happens every other minute.

I swear, I'm not touching the touchpad or mousebuttons.

I don't suspect it to be a hardware problem, since the touchpad worked flawlessly in Vista.

Does anyone else experience this problem or something similar, and can somebody help me?

I've been googling extensively.

---

### Post by lundbymads on 2008-10-01
bump

---

### Post by meeces2911 on 2008-10-04
I having this exact problem as well. I have just added the above work around, and i will try that when i restart.  but your saying your still having problems with the mouse going spaz ? hmmm, doesn't look too promising then :P. Oh well i will try.

---

### Post by zd3nik on 2008-10-14
> **lundbymads said:**
> I have a Dell XPS M1530 and I've done the i8042.nomux=1 work-around.

It works almost perfectly. 

However, I experience a pretty annoying bug: When I'm writing text, the mousepad randomly do "ghost" clicks, without me using the touchpad, and jumps to the position of the cursor. This happens every other minute.

I swear, I'm not touching the touchpad or mousebuttons.

I don't suspect it to be a hardware problem, since the touchpad worked flawlessly in Vista.

Does anyone else experience this problem or something similar, and can somebody help me?

I've been googling extensively.

I've been having the exact same problem.  Except I figured I was accidentally brushing my thumb across the touchpad so lightly I couldn't feel it.  I figured this because, as you said it only happens when typing, and my thumbs do hover very close to the touchpad when I type.

In my case this issue only exists when the system does not detect the touchpad as a touchpad (you can tell when this happens because the touchpad tab does not appear on the mouse preferences window).  Sometimes the touchpad is recognized properly and everything is fine.

I just saw another post on a similar topic that recommends adding the following line to your /etc/modprobe.d/options file:

options psmouse elantech=1

I'm hoping this will help the system to properly identify the touchpad each time it boots and therefore resolve the issue.  But I haven't tried it yet because I am currently using my old laptop (this issue is bad enough that I just leave the M1530 sitting unused at home).

Z

---

### Post by lundbymads on 2008-10-16
Thank you. I'll try that solution.

For a while I've disabled mousepad clicking, which (of course) prevents the "ghost" clicking.

Thank you for your suggestion, zd3nik. I'll report back, if the workaround works.

---

