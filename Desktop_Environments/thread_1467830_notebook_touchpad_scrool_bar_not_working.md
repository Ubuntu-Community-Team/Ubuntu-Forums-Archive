---
title: "notebook touchpad scrool bar not working"
date: 2010-05-01
forum: Desktop Environments
---

### Post by mdaud on 2010-05-01
After upgrading from 9.10 to 10.04 my touchpad scroll bar not working any more 
Im using hp pavilion dm1
I made several reboots 

any idea?

---

### Post by frithiof on 2010-06-21
Hi.
I have the same problem on the same machine.

Have you found a solution for this?

/F

---

### Post by megalodon16 on 2010-06-21
i have the quite the same problem. i say "quite" because i would like to deactivate the scrolling touchpad because it goes crazy sometimes. (i don't know if ubuntu 10.04 is the problem or my scrolling touchpad).

---

### Post by frithiof on 2010-06-22
megalodon16: Do you also have the same laptop model?

---

### Post by zemoffm on 2010-08-11
I am having the same issue.  Scroll bar does not work.  In fact, my touchpad does not appear as a synaptics touchpad, which I think is the issue.

me@computer:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]

Shouldn't it be SynPS/2 Synaptics Touchpad or something like that?
What's going on here?  I did a lot of googling around, but can't find any anything that helps.

I am on a pavilion dm1z-2000.  And on fresh install of ubuntu 10.04 (no upgrade from earlier ubuntu version).

Thanks in advance.  Any help would greatly be appreciated.

---

### Post by zemoffm on 2010-08-11
More info:
me@computer:~$ cat /var/log/Xorg.0.log | grep Synaptics
me@computer:~$ cat /var/log/Xorg.0.log | grep PS/2
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event12)
(**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Generic Mouse: always reports core events
(**) PS/2 Generic Mouse: Device: "/dev/input/event12"
(II) PS/2 Generic Mouse: Found 3 mouse buttons
(II) PS/2 Generic Mouse: Found relative axes
(II) PS/2 Generic Mouse: Found x and y relative axes
(II) PS/2 Generic Mouse: Configuring as mouse
(**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
(II) PS/2 Generic Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)

Looks like its being seen as a generic mouse... and that it SHOULD emulate the wheel (scroll).  But I could be reading that wrong.  If EmulateWheelButton does mean the scroll bar, then its not working, because there is no vertical scrolling.

---

### Post by g.c.haze on 2011-01-19
Same notebook, same problem. I'm using 10.10-netbook. I googled this problem for hours last night with no luck. Synaptics touchpad recognized as standard mouse. I've been using linux for over ten years. This version of Ubuntu has the best hardware recognition I've seen on a stock kernel except for this one glitch.

Any suggestions?

---

### Post by g.c.haze on 2011-01-19
Same notebook, same problem. I'm using 10.10-netbook. I googled this problem for hours last night with no luck. Synaptics touchpad recognized as standard mouse. I've been using linux for over ten years. This version of Ubuntu has the best hardware recognition I've seen on a stock kernel except for this one glitch.

Any suggestions?

---

### Post by g.c.haze on 2011-01-19
Same notebook, same problem. I'm using 10.10-netbook. I googled this problem for hours last night with no luck. Synaptics touchpad recognized as standard mouse. I've been using linux for over ten years. This version of Ubuntu has the best hardware recognition I've seen on a stock kernel except for this one glitch.

Any suggestions?

---

### Post by g.c.haze on 2011-01-19
Same notebook, same problem. I'm using 10.10-netbook. I googled this problem for hours last night with no luck. Synaptics/Alps touchpad recognized as standard mouse. I've been using linux for over ten years. This version of Ubuntu has the best hardware recognition I've seen on a stock kernel except for this one glitch.

I'm a long term Slackware and Gentoo user. I installed Ubuntu just to see what kind of hardware I was dealing with. I'd been impressed by BackTracks detection and even more impressed by your live usb. Almost everything works. WebCam, Verizon 3g card, wireless card all worked out of the box, with stock kernel. Very impressive. I've come across references to a kernel bug with this touchpad.

Any suggestions?

Wonderful distro, btw.

---

### Post by g.c.haze on 2011-01-19
Same notebook, same problem. I'm using 10.10-netbook. I googled this problem for hours last night with no luck. Synaptics/Alps touchpad recognized as standard mouse. I've been using linux for over ten years. This version of Ubuntu has the best hardware recognition I've seen on a stock kernel except for this one glitch.

I'm a long term Slackware and Gentoo user. I installed Ubuntu just to see what kind of hardware I was dealing with. I'd been impressed by BackTracks detection and even more impressed by your live usb. Almost everything works. WebCam, Verizon 3g card, wireless card all worked out of the box, with stock kernel. Very impressive. I've come across references to a kernel bug with this touchpad.

Any suggestions?

Wonderful distro, btw.

---

### Post by g.c.haze on 2011-01-19
Same notebook, same problem. I'm using 10.10-netbook. I googled this problem for hours last night with no luck. Synaptics/Alps touchpad recognized as standard mouse. I've been using linux for over ten years. This version of Ubuntu has the best hardware recognition I've seen on a stock kernel except for this one glitch.

I'm a long term Slackware and Gentoo user. I installed Ubuntu just to see what kind of hardware I was dealing with. I'd been impressed by BackTracks detection and even more impressed by your live usb. Almost everything works. WebCam, Verizon 3g card, wireless card all worked out of the box, with stock kernel. Very impressive. I've come across references to a kernel bug with this touchpad.

Any suggestions?

Wonderful distro, btw.

---

