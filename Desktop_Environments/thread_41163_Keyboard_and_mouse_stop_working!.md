---
title: "Keyboard and mouse stop working!"
date: 2005-06-12
forum: Desktop Environments
---

### Post by hellraiser_rob on 2005-06-12
Hi Guys, hope someone is able to help, my keyboard and mouse seem to stop working after being left to idle for x amount of minutes.  Possibly after the screen saver ingages.

Keyboard and mouse are wireless logitech mx series (usb)

i notice that the caps button doesn't even work, as the light doesn't go on and aff accordingly on the wirless reciever

Any help would be much appreicated

---

### Post by jweila01 on 2005-06-12
I had a similar problem on a Dell Latitude 610 laptop.

Problem was solved by removing powernowd: apt-get remove powernowd

---

### Post by hellraiser_rob on 2005-06-12
thanks i'll give it a go

---

### Post by pauls101 on 2005-06-12
I'm getting the same freeze as soon as I attempt to do anything after logging on. I just removed powernowd in recovery mode, had no effect.

The mouse pointer still moves but no clicks, keyboard is dead (Num Lock light is on, no longer responds to the key.) Switching to a cheapo PS2 from a MS USB Wheel mouse made no difference. Currently I have a half drawn K menu frozen on the screen.

Machine is a whitebox ADM 2100XP+. New default install, no problems except the CD was apparently bad, I unmounted it, mounted the ISO, and the install completed w/ no errors.

If anyone has any other ideas, this is kind of hard to troubleshoot from here.

---

### Post by tigerstripedcat on 2005-06-12
[QUOTE=pauls101]I'm getting the same freeze as soon as I attempt to do anything after logging on. I just removed powernowd in recovery mode, had no effect.

The mouse pointer still moves but no clicks, keyboard is dead (Num Lock light is on, no longer responds to the key.) Switching to a cheapo PS2 from a MS USB Wheel mouse made no difference. Currently I have a half drawn K menu frozen on the screen.

Machine is a whitebox ADM 2100XP+. New default install, no problems except the CD was apparently bad, I unmounted it, mounted the ISO, and the install completed w/ no errors.

If anyone has any other ideas, this is kind of hard to troubleshoot from here.[/QUOTE]
 I had a similar problem.  Keyboard wouldn't work until the Xserver started, and the computer wouldn't reboot.  I solved both problems by reseting bios defaults.

---

### Post by hellraiser_rob on 2005-06-13
so what had you changed in the bios beforehand?

---

### Post by pauls101 on 2005-06-13
Resetting the BIOS didn't help. It's an ASUS mobo w/ no changes (IIRC) other than Boot From CD.

The thing can 
 - Sit on the desktop indefinitely. 
 - Dragging a rectangle on the desktop makes no difference (a bunch of artifacts appear in the rectangle.) 
 - Mouseovers in the taskbar are fine (tooltips work), but clicking on anything other than empty desktop causes a lockup. It has frozen with the K menu (kubuntu) half drawn once and with the bouncing cursor in mid-wiggle several times, so it seems more like a time thing than any particular item (I've tried several.)

---

