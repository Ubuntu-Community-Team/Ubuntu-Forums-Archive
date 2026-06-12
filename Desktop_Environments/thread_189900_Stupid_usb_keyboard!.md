---
title: "Stupid usb keyboard!"
date: 2006-06-05
forum: Desktop Environments
---

### Post by OtonVM on 2006-06-05
Hi! 

I have this Genius keyboard wich doesn't get sold anywhere on earth but I somehow got one. Anyway, I got it working in gentoo by loading the usbkbd module on startup. It kinda works on ubuntu too, except that I must first boot and login with the ps/2 adapter and then connect it to the usb port. If I don't, I can't login and I get this error in dmesg:
```
[4294971.277000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4294971.278000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4294971.279000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4294971.280000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4294971.500000] usb 1-7: USB disconnect, address 3
[4294974.071000] input: AT Translated Set 2 keyboard as /class/input/input3
[4294974.237000] input: AT Translated Set 2 keyboard as /class/input/input4
[4294997.968000] usb 1-7: new low speed USB device using ohci_hcd and address 4
[4295008.128000] drivers/usb/input/hid-core.c: usb_submit_urb(ctrl) failed
[4295008.128000] drivers/usb/input/hid-core.c: timeout initializing reports
[4295008.128000]
[4295008.128000] input: ABBAHOME as /class/input/input5
[4295008.128000] input: USB HID v1.10 Keyboard [ABBAHOME] on usb-0000:00:02.0-7
[4295014.641000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4295014.642000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4295014.643000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4295014.644000] drivers/usb/input/hid-core.c: ctrl urb status -110 received
[4295014.752000] usb 1-7: USB disconnect, address 4
[4295018.188000] input: AT Translated Set 2 keyboard as /class/input/input6
[4295018.268000] atkbd.c: Failed to enable keyboard on isa0060/serio0
[4295018.268000] input: AT Translated Set 2 keyboard as /class/input/input7
[4295018.328000] input: AT Translated Set 2 keyboard as /class/input/input8
[4295018.494000] input: AT Translated Set 2 keyboard as /class/input/input9

```
and no mather what I do (rmmod, modprobe), nothing works. I suppose it's something to do with udev? 

tnx in advance for any suggestions.

---

### Post by padre999 on 2006-06-05
Maybe it has to do with Bios settings...

[http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689)
[http://ubuntuforums.org/showthread.php?t=187896](http://ubuntuforums.org/showthread.php?t=187896)

---

### Post by OtonVM on 2006-06-05
nope, legacy usb was the first thing I set up in bios upon assembling the pc and I have no HT. And it does work in linux. If it did in gentoo...

---

### Post by guice on 2006-06-05
Any reason not to keep it as PS/2? I've had many problems with USB based keyboards (even in windows) that I just keep all mine plugged into the PS/2 port now. Makes it much simpler, especially when I need to dig around in the BIOS.

---

### Post by OtonVM on 2006-06-06
Unfortunately yes. I really like the multimedia features that work with ps/2, but the keyboard gets stuck sometimes. shift, ctrl sometimes remain "pressed" and I must literally bang on them to deactivate them. and the *lock keys don't work properly. If it wasn't that it is the best keyboard I ever had in terms of keys and layout I would burn it with no seccond thoughts.

---

### Post by OtonVM on 2006-06-07
Bump! No ideas? What about recompiling the kernel? Could it be an idea?

---

### Post by mlho on 2006-06-07
i'm having the same problem and getting frustrated too! 
[http://ubuntuforums.org/images/smilies/icon_confused.gif](http://ubuntuforums.org/images/smilies/icon_confused.gif)
:???:
see if these threads listed below are of any use. i was going to do as it suggests, but unfortunately something has screwed up with my xsessions and i can't login, so that's my more pressing problem!

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36339](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36339)
[http://ubuntuforums.org/showthread.php?t=150855](http://ubuntuforums.org/showthread.php?t=150855)

mark

---

### Post by OtonVM on 2006-06-07
Ok, found something new! (every day something...) 
ubuntu is actually blocking usbkbd:*/etc/modprobe.d/blacklist: # these drivers are very simple, the HID drivers are usually preferred* -- you gotta be joking! Where has the "simplicity rulez" philosophy gone?
Ok, is this module beeing blocked on some other level too?

---

### Post by OtonVM on 2006-06-07
[QUOTE=mlho]i'm having the same problem and getting frustrated too! 
[http://ubuntuforums.org/images/smilies/icon_confused.gif](http://ubuntuforums.org/images/smilies/icon_confused.gif)
:???:
see if these threads listed below are of any use. i was going to do as it suggests, but unfortunately something has screwed up with my xsessions and i can't login, so that's my more pressing problem!

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36339](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36339)
[http://ubuntuforums.org/showthread.php?t=150855](http://ubuntuforums.org/showthread.php?t=150855)

mark[/QUOTE]
Now I saw this on the forum too. Thank you for the links!!

---

### Post by OtonVM on 2006-06-07
The results are the same, but some improvement has been reached:
/var/log/messages:
```
...Jun  7 20:23:37 ubuntu kernel: [4294687.862000] ts: Compaq touchscreen protocol output
Jun  7 20:23:37 ubuntu kernel: [4294688.105000] intel8x0_measure_ac97_clock: measured 50717 usecs
Jun  7 20:23:37 ubuntu kernel: [4294688.105000] intel8x0: clocking to 46815
Jun  7 20:23:37 ubuntu kernel: [4294689.187000] drivers/usb/input/hid-core.c: timeout initializing reports
Jun  7 20:23:37 ubuntu kernel: [4294689.187000]
Jun  7 20:23:37 ubuntu kernel: [4294689.187000] input: ABBAHOME as /class/input/input2
Jun  7 20:23:37 ubuntu kernel: [4294689.187000] input: USB HID v1.10 Keyboard [ABBAHOME] on usb-0000:00:02.0-7
Jun  7 20:23:37 ubuntu kernel: [4294689.187000] usbcore: registered new driver usbhid
Jun  7 20:23:37 ubuntu kernel: [4294689.187000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Jun  7 20:23:37 ubuntu kernel: [4294689.193000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6204
Jun  7 20:23:37 ubuntu kernel: [4294689.193000] usbcore: registered new driver usblp
Jun  7 20:23:37 ubuntu kernel: [4294689.193000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jun  7 20:23:37 ubuntu kernel: [4294689.194000] usbcore: registered new driver usbkbd
Jun  7 20:23:37 ubuntu kernel: [4294689.194000] drivers/usb/input/usbkbd.c: :USB HID Boot Protocol keyboard driver
Jun  7 20:23:37 ubuntu kernel: [4294689.386000] lp: driver loaded but no devices found
...
```

hid-core is the bitch! I bet is some incompatibility between modules beeing loaded. If no solution is reached soon, I'll recompile the kernel and strip it down to the (almost) lone essentials. Then we'll see.

---

### Post by reticencias on 2006-11-30
sorry for my newbiness but I think I'm having the same problem. I also have a USB Genius keyboard and it just went crazy when I moved to ubuntu, I really haven't had the "birght idea" off trying it out with the usb-ps2 adapter (lolol) do you guys think it would be a good solution??? I really don't care if it's usb or ps2 I only want it to work :)

---

### Post by kerry_s on 2006-11-30
I'd say maybe it's time for a new keyboard, just grab something cheap. I just got 1 at wal-mart for $7 dollars. But till you figure things out you can try using the gnome on-screen keyboard(gok) it should be under accessibility. I use fluxbox so i used xvkbd for like a month putting off buying a keyboard at all. I've gotten so use to using the on-screen keyboard that i barely use the real one.

---

### Post by reticencias on 2006-11-30
man, that's not an option, I just spent 35 Eur. (that's 46 USD) onthis keyboard!!!!!

it's got to work!!!

---

