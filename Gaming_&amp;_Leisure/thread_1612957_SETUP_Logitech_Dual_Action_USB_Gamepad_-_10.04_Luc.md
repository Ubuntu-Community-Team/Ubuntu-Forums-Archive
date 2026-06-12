---
title: "SETUP: Logitech Dual Action USB Gamepad - 10.04 Lucid"
date: 2010-11-03
forum: Gaming &amp; Leisure
---

### Post by coolglobal on 2010-11-03
I bought this popular gamepad as it appears to be well supported in previous releases of Ubuntu. After looking through numerous threads on gamepads on the ubuntu forums and with internet search, I cannot get clear and easy to understand instructions on its setup. Can you help. Please make the process simple, for me and those who follow. Your help is appreciated. If a link posts here that doesn't apply to lucid I'll let you know.

---

### Post by dfreer on 2010-11-03
It should work out of the box. I have 3 of them, and they use a standard USB HID driver, which means just plug them in and play. One thing I would NOT recommend is using jscalibrator, for reasons see my sig. They shouldn't really need calibrating.

Have you already tried plugging it in, and did it not work? What program or game did you try using it with?

---

### Post by coolglobal on 2010-11-04
Thank you for the encouraging reply dfreer, it's much appreciated.

I installed Joystick and Joy2key. (joystick has a command jscal).

I am attempting to get the gamepad to work in [Sauerbraten]("http://sauerbraten.org/") first. Would also like to use it for [Vendetta]("http://www.vendetta-online.com/") and others such as [Alien Arena]("http://icculus.org/alienarena/rpa/"). Am also interested for using it as an option to replace key strokes and mouse gestures in Ubuntu.

If it is installed, I am unaware of it, as Ubuntu gives no indication of it's presence after plugging it in or rebooting. Sauerbraten keyboard options do not respond to the gamepad.

I honestly don't know where to start with Joystick or Joy2key, and am certain I am not alone in this.

(Have used Ubuntu for many years with just occasional use of the terminal. First time trying a joystick/gamepad with Ubuntu.)

---

### Post by dfreer on 2010-11-04
Ubuntu won't visible show you plugging in a device, but you can use a couple of the following commands to see if it was detected after you plug it in:
```
dmesg | tail
lsusb
```

I'm not even sure those games support gamepads, I'd recommend trying a game that is known to do so. Any emulator should support gamepads, I believe frozen-bubble in the repository will also support gamepads. Try a known good game first, just to make sure your gamepad works (which it should).

Then you can try using a joystick to keyboard mapping program to play your other games. Can't promise those will work, seems like a kludgy workaround to me. Especially trying to get it to control the OS.

---

### Post by coolglobal on 2010-11-04
Those commands are indeed the key to revealing the gamepads status, as seen here (a little trimmed for clarity):

computer@computer:~$ **[COLOR="DarkOrange"]dmesg | tail[/COLOR]**
[   16.416573]  domain 0: span 0-1 level MC
[   16.416575]   groups: 0 1
[   16.416580] CPU1 attaching sched-domain:
[   16.416581]  domain 0: span 0-1 level MC
[   16.416583]   groups: 1 0
[   22.860011] eth0: no IPv6 routers present
[46695.548780] __ratelimit: 9 callbacks suppressed
[46695.548782] type=1505 audit(1288913573.118:15):  operation="profile_replace" pid=3395 name="/usr/lib/cups/backend/cups-pdf"
[46695.549341] type=1505 audit(1288913573.118:16):  operation="profile_replace" pid=3395 name="/usr/sbin/cupsd"
[47952.076481] sr0: CDROM not ready.  Make sure there is a disc in the drive.

computer@computer:~$ **[COLOR="DarkOrange"]lsusb[/COLOR]**
Bus 004 Device 003: ID 046d:c523 Logitech, Inc. 
[COLOR="DarkOrange"]Bus 004 Device 002: ID 046d:c216 Logitech, Inc. Dual Action Gamepad[/COLOR]
Bus 003 Device 003: ID 1532:001c Razer USA, Ltd 
Bus 003 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel


[COLOR="DarkOrange"]**Frozen Bubble**[/COLOR] from the Ubuntu Software Centre, allowed me to test the gamepad. It works.

Am going to attempt some keymapping/profiling now, with Joy2key, from synaptic. Is there a better way than Joy2key? Unsure if it can do mouse gestures. There is no gui. If there is an easier way to do it please post.

---

### Post by thatguruguy on 2010-11-04
I believe qjoypad supports mouse gestures.

---

### Post by weasel fierce on 2010-11-08
for simple "keyboard to joystick" stuff, I find rejoystick works wonders.

---

