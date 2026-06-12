---
title: "Ctl-Left-Click no longer selects/deselects single item in list"
date: 2007-10-19
forum: Desktop Environments
---

### Post by Xitron on 2007-10-19
My best example would be in the Evolution email client, but it happens elsewhere as well.

When I left-click on an email, and then shift-left-click on another further down in the list, as expected, it selects all from-to.  When I then go into the middle of the highlighted list and ctl-left-click on one I want removed from the list, it just makes the entire highlighted list blink, and does not select/deselect items on the list.

This used to work, and I cannot tell you when it stopped.

It happened while I was on Feisty, but having just updated to Gibbon, it is still happening.

I get the following in dmesg output, which may provide a clue...

# dmesg | grep -i mouse
[   18.345352] input: Macintosh mouse button emulation as /class/input/input0
[   18.351072] mice: PS/2 mouse device common for all mice
[    5.140000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-6.3
[   17.724000] input: PS/2 Mouse as /class/input/input4

Can anyone tell me how to get my mouse back to the point where it uses the ctl-left-click as a select/deselect for individual line items?  Note: dual-boot notebook (Dell Latitude D800) and the ctl-left-click works in the windoze side, so it would appear that the problem is not with the mouse hardware.

Thanks!

Unca Xitron

---

