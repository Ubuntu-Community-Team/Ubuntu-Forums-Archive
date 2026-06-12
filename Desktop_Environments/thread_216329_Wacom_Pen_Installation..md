---
title: "Wacom Pen Installation."
date: 2006-07-15
forum: Desktop Environments
---

### Post by khaledaboualfa on 2006-07-15
Hey everyone, bit of a newbie here so please go easy. I'm trying to install my wacom pen, it's an intuos 3, and I've tried to follow the tutorial here:
[http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom+gimp](http://www.ubuntuforums.org/showthread.php?t=25151&highlight=wacom+gimp)

However I'm not sure how to check which mouse I should be putting in the xorg file. 

```
sudo xxd /dev/input/mouse0
```

In the terminal gives me a long list of numbers. Nothing else, they just keep coming. So I don't know what's going on there. Any help would be well appreciated.

Also just to confirm I shouldn't be including the information for the serial port at all (it's got a usb connection) right? Or does it matter if that information is included in there as well?

---

### Post by gThree on 2006-07-15
Also a newbie, and on PPC, so beware ... but here's my experience with a Wacom Intuos 2 (USB, pen-only) and a Logitech USB mouse:

The stream of characters is, I guess, input data from the mouse.  When you see it while you're moving the mouse, you know you have the right mouse id.

On Dapper (after I upgraded), I didn't have to enter specific mouse information anymore -- in fact, I had trouble when I did because the mouse got assigned a different id every time I rebooted so, if I'd entered "mouse0" and it was now "mouse1", I was SOL.  Same with the "wacom" events.

In other words, my xorg.conf still says "/dev/input/mice" and "/dev/input/wacom" and the tablet works just fine.

But, on Breezy, I did have to enter the mouse id and event numbers before the tablet would work.

On both, I deleted the "serial" lines.

Not sure how much of that will apply to your situation, but good luck ....

---

### Post by khaledaboualfa on 2006-07-15
Cool thanks for that, it actually kinda makes sense since I did try and find my event for the wacom and it actually changed. I'll give it a try and see how it all goes (tip to all other newbies looking in on this, MAKE SURE TO BACKUP the xorg file, because you might be wanting to go back to this. Write it down on a piece of a paper like I did because you'll be able to turn the clock back once it's crapped up :)

---

