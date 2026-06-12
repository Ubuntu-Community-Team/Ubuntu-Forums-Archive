---
title: "X in a two video card environment"
date: 2010-10-31
forum: Desktop Environments
---

### Post by Skaperen on 2010-10-31
I'm looking at getting a computer with two video cards.  Actually "card" #1 is really a video chip on the motherboard.  Card #2 is plugged into a PCIe slot.  I want to leave card #1 as the card BIOS uses, and also the one the kernel uses (text mode) because it has better text mode support.  I want to run X via card #2 because it is better for graphical uses.

I'd like to review what X will do, or can do, to support this.  Presumably, the X driver for video #2 has no support to work with video #1 at all.  They are radically different video chips from different manufacturers.  Specifically, video #1 is a Matrox G200.  Video #2 could be an NVIDIA, or alternatively ATI, or maybe even something else.

1.  How will X know to use video #2 and not video #1?  Is that coded into xorg.conf?

2.  As X starts up, will it try to save the video mode of video #1 or of video #2?

3.  Will X do a virtual terminal switch and effect video #1 that way, even though it will be doing all its graphics on video #2 which comes out a separate DVI connector (video #1 is VGA analog).

4.  Can I configure X to only use a keyboard/mouse attached to USB, and ignore another keyboard/mouse attached to PS/2?

5.  What if I have 2 instances of video #2 (thus video #3), with a 2nd set of keyboard/mouse on USB, to do a 2-seat setup on one computer, with 2 instances of X for that video type (assuming video #2 and video #3 are identical cards)?

---

### Post by cascade9 on 2010-10-31
Normally, adding a video card disables the onboard video. Thats not always true, and if you do have a motherboard/chipset that does allow you to run the onboard + a standalone viodeo card, then you might be able to do some of what you want. 

You'd probably have to blacklist the onbaord video,  but then you wont get text mode from the onboard video. There might be some neat hack that lets you, but I dont know it. 

Seems to be an awful amount of sodding around to just have BIOS + text mode running from1 video card and then X from another.

---

### Post by Skaperen on 2010-10-31
> **cascade9 said:**
> Normally, adding a video card disables the onboard video. Thats not always true, and if you do have a motherboard/chipset that does allow you to run the onboard + a standalone viodeo card, then you might be able to do some of what you want.Just disable in BIOS the video card(s) you don't want BIOS to use.  Scenarios with multi-seat video cards (where they assume all video cards will be used by X) would be accessing at least on video card in X that was not enabled in BIOS.  So disabling in BIOS clearly doesn't prevent X from using it once the OS and X comes up.  So for my scenario (#1 for text, #2 for X) I'd just disable #2 in BIOS.

> **cascade9 said:**
> You'd probably have to blacklist the onbaord video,  but then you wont get text mode from the onboard video. There might be some neat hack that lets you, but I dont know it.I'd be telling BIOS to use the onboard video and not the plugged in video.  Hopefully someone who knows X well and would realize what neat hack is needed, might come along and tell us.

> **cascade9 said:**
> Seems to be an awful amount of sodding around to just have BIOS + text mode running from1 video card and then X from another.I agree.  They should just make it simple.  I should be able to tell BIOS which video card/chip to use, and tell X which video card/chip to use.

But assumptions do get made, and code is too often written under such assumptions.  Apparently, from reading about the "2 or more seats of X" scenarios, even that gets impacted by legacy assumptions of "one machine, one video card" ... or ... "one machine, one keyboard/mouse" (this one might be harder).

---

