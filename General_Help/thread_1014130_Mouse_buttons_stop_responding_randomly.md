---
title: "Mouse buttons stop responding randomly"
date: 2008-12-17
forum: General Help
---

### Post by chrisamiller on 2008-12-17
I have a standard Dell USB 2-button w/ scroll mouse, and every few days the system stops recognizing mouse clicks.  The mouse cursor moves fine, keyboard shortcuts work fine, and nothing else seems to be wrong with the system.

I can unplug and replug the mouse, and even try different USB ports, and the same problem persists until I do a restart.  I can even plug a different USB mouse into the system, and I get the same problem - cursor movement, but no mouse button support.

I've tried checking out dmesg, but can't find anything indicative of a problem.  Here's a tail from right after the click support dropped.  You can see where I unplug/replug the mouse and it is recognized, but the buttons still do not work.

```
[275575.356288] ppdev0: registered pardevice
[275575.404382] ppdev0: unregistered pardevice
[275575.472065] ppdev0: registered pardevice
[275575.520058] ppdev0: unregistered pardevice
[275575.522425] ppdev0: registered pardevice
[275575.568151] ppdev0: unregistered pardevice
[275988.126220] type=1503 audit(1229034676.279:32): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=5495 profile="/usr/sbin/cupsd"
[340160.192014] usb 8-4: reset high speed USB device using ehci_hcd and address 4
[342345.202766] type=1503 audit(1229101033.355:33): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=19108 profile="/usr/sbin/cupsd"
[436562.168035] NVRM: Xid (0001:00): 8, Channel 00000001
[436562.172002] NVRM: Xid (0001:00): 55,  L0 -> L0
[475748.328245] NVRM: Xid (0001:00): 13, 0003 00000000 0000002d 00000280 00000000 00000000
[475748.328615] NVRM: Xid (0001:00): 13, 0003 00000000 0000002d 00000280 00000000 00000000
[475748.328940] NVRM: Xid (0001:00): 12, COCOD 00000003 80022d00 0000502d 00000280 00000000
[475748.393415] NVRM: Xid (0001:00): 12, COCOD 00000003 80022d00 0000502d 00000280 00000000
[611981.320038] usb 2-1: USB disconnect, address 2
[611988.400013] usb 2-2: new low speed USB device using uhci_hcd and address 3
[611988.631141] usb 2-2: configuration #1 chosen from 1 choice
[611988.652652] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input5
[611988.713645] input,hidraw1: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1a.1-2

```

This is all on Ubuntu 8.10 (intrepid) 64-bit.
kernel: 2.6.27-9-generic (x86_64 GNU/Linux)

Any ideas?  Is there another log I should be checking?  I'm completely stumped here.

---

### Post by weyh on 2008-12-21
I have the same problem.  It just started happening the last couple weeks.
I have 8.10 and have been using ubuntu for the last couple years with no problems.  The batteries in the Wireless Mouse are new.  BTW

---

### Post by chrisamiller on 2008-12-23
Hrmmm - The problem may be linked to segfaults in npviewer.bin (Flash) causing crashing of firefox.  They occurred simultaneously today, and may have occurred at the same time previously.  I've installed Flash 10 x64 alpha, which seems to have solved the flash stability problem.  I'll update in a few days with more info.

---

### Post by chrisamiller on 2009-01-13
Update:  Doesn't seem to be flash-related after all.  This bug report may be the one that ultimately solves this problem:
[https://bugs.freedesktop.org/show_bug.cgi?id=18922](https://bugs.freedesktop.org/show_bug.cgi?id=18922)

---

### Post by dcstar on 2009-01-13
> **chrisamiller said:**
> Update:  Doesn't seem to be flash-related after all.  This bug report may be the one that ultimately solves this problem:
[https://bugs.freedesktop.org/show_bug.cgi?id=18922](https://bugs.freedesktop.org/show_bug.cgi?id=18922)

I have also been experiencing this recently (8.04 64-bit), but I had put it down to my hardware.

It seems to resolve itself in the time it takes to change the battery in my wireless mouse so I initially thought that was the problem, but not now since it seems a regular annoyance......    :-(

More research show this:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167)

I have just downgraded my xorg version from the hardy-updates version to the hardy version, so I'll see how that goes over time.

Nope, no difference on the older xorg version, but hitting the ALT key seems to re-enable my mouse buttons - I'll see how this goes over time.

---

### Post by DaveHartburn on 2009-01-15
I have the same issue since upgrading to 8.10 last week. Running an ATI graphics card, two monitors, focus on mouse over and Xinerama.

The work around from one of the links does get focus back:
> 
 Kevin Browne wrote on 2008-12-10: (permalink)

I also encounter this problem three or four times per day. I have three monitors on two Nvidia Quadro FX cards, using the nvidia 177 binary driver on 8.10.

I found that when the problem strikes, I can re-enable the mouse with the following steps:
1) Select a window using ALT+TAB.
2) Open the window's menu with ALT+SPACE.
3) Select 'Move' from the menu. The cursor should change to the hand cursor and be positioned in the centre of the window.
4) Move the cursor with the mouse. If this causes the window to move (unlikely), left-clicking should release the window and the mouse should work normally.
5) It's more likely that moving the mouse will just move the cursor and the window will stay put. In this case use the cursor keys to move the window to the primary monitor. If the window is already on the primary monitor, move it to another monitor, then back to the primary.
6) Once the window is on the primary monitor, move the cursor with the mouse. The window should move with the cursor, and mouse events register again.

This works for me every time. It's far from ideal, and I detest this kind of voodoo workaround, but it's better than restarting X. Of course, your mileage may vary.


Interestingly, if I pick a window on the second monitor, the menu appears on the first. It almost looks like the pointer position detection gets detached from the pointer display. As it does appear to be dual screen related, I suspect some compatibility bug between X and Xinerama.

---

### Post by chrisamiller on 2009-01-15
FWIW, I'm using the same Nvidia driver (177) and Xinerama on 8.10. 

Thanks for the workaround - I'll give it a shot next time it freezes (likely at some point today)

Update: yeah, that workaround restores functionality for me too.  What a kludge...

---

### Post by DaveHartburn on 2009-01-16
I've just had another crash. This time I had changed to 'click for focus', so it appears the problem is nothing to do with mouse focus mode.

---

### Post by Coopster on 2009-02-24
Ahh, thanks so much for the workaround;  this has been driving me nuts.

Perhaps it's related to ppdev somehow?  I've noticed my dmesg always states this after a mouse crash:
```
[  176.968588] ppdev0: registered pardevice
[  177.016812] ppdev0: unregistered pardevice
[  178.284188] ppdev0: registered pardevice
[  178.332545] ppdev0: unregistered pardevice
[  179.664363] ppdev0: registered pardevice
[  179.712838] ppdev0: unregistered pardevice

```

This is also present in the first dmesg quote on this thread.

---

### Post by Coopster on 2009-02-24
Sorry, hadn't read through the bug report yet.  [Bug #296167]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/296167") has a better discussion and links to a good [workaround]("http://www.gen-x-design.com/archives/workaround-for-ubuntu-810-mouse-bug/").

---

