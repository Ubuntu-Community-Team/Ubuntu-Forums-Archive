---
title: "Mouse dropouts"
date: 2023-01-09
forum: Desktop Environments
---

### Post by denispc92 on 2023-01-09
I am running 64 bit Ubuntu 22.04. 1 LTS, Gnome version, Wayland Windowing system on an HP Notebook,with a Logitech M325 USB Mouse.

Until about 2 months ago, It was running very well.  Then the Mouse started to freeze.  Sometimes it would unfreeze and at other times it would stay frozen so I would have to use the touchpad, which is hopeless.  I can't remember if an Update came through at the time.

I had a look around in Settings to find where I could fix the Mouse as the default Pointer.  But that doesn't appear to exist.  

How do I either find where I can do that or what else do I need to do to get the mouse working all the time as it should?

Thanks
Denis

---

### Post by TheFu on 2023-01-10
Check that it isn't gunk inside the mouse, messing with the ball or covering the optical sensors.  Check those first.
Next I'd see if Wayland is the issue by changing to X11.  The display server controls the mouse inputs, so that's an easy check. Not sure if a reboot is even needed. Just logout, click the "Gear" icon, and select Xorg or X11 or X/Windows (I don't remember the exact name).
Lastly, if it is a USB mouse, try using the other slow USB port.  Sometimes a USB port will go bad.  Does that same USB port work with other devices, say storage or another peripheral?

I've had issues with Logitech mice before.  One that worked great and I'd still be using today, stopped working across every system I owned.  The industry had changed what they considered "standard" and didn't check with me first. Scary how often that happens. I bet it happens to everyone else here too. ;)

About a year ago, I was forced to get a new keyboard.  Got a Logitech USB mechanical keyboard.  It works fine when directly connected to the system(s), but not going through either of my KVM switches.  Both the mouse and keyboard work for about 5 seconds, then drop for 20 seconds, then work for 5 seconds, then drop.  Logitech ... er ... Logi is their new name now ... is doing things that work with Windows and forgetting to test with other OSes or other non-trivial setups, like with KVMs.  

I contacted Logi support. There answer was "we don't support KVMs", but it was like pulling teeth to get them to admit it. For 15 minutes, they used exactly the scripted answer, "directly connected keyboards work best", which isn't an option. I finally got the CSR made enough to admit they don't test with any KVM switches.  I won't be buying any more Logi hardware, if I can help it.  I can only vote with my money.

Ignore OT, personal story below:
I have 1 more hardware issue to check with that setup - got a new KVM cable for the systems in the mail yesterday. Just need to plug it in and perhaps try moving a system to a different KVM set of ports. My issue really could be with the cables or switch port.  If it were THAT important, I would have solved the issue long ago.  The computer where I see the problem is a server, so 99.999% of the time, I'm using ssh to do things on it, not the console. I did have to set the BIOS to boot even if it doesn't see any monitor, keyboard or mouse, so it wouldn't get stuck waiting and not booting.

Of course, my older KVM switch (from 2005) is PS/2 only and works perfect.  The new KVM switch is USB3 and has some fancy audio and USB switching built in ... no doubt mucking up the simplicity.  The only reason I got the new KVM switch is because a USB-2-PS2 adapter wasn't working with Logi's keyboard.

We all have little issues. If I only had 1 computer, a little issue could be a show-stopper. It is a minor inconvenience for now.

---

### Post by denispc92 on 2023-01-11
Thanks for that.  I hooked up an older Logitech Mouse and USB dongle and that works.

However, and there's always a damned "however", I have found that doing Screen Dumps no longer works as it did.

Before hit "prt scn/ctrl" position the boundary then hit the big button.  I could then "ctrl V" it into the document.  It appears that the "ctrl" button is no longer needed when invoking the screen dump command.  But dropping it into the document only gives a huge blank area with a small image and the word "Image" in the top RH corner.  So when I go to Properties and hit the Crop or Images Tabs of I go to "Pictures/Screen Shots" the image is there.  

Its just that its no longer dropped into the document on the "ctrl V" command.

I just tried that with the other Mouse and it now works but wont Paste the clipboard content.

Also when I go to Pictures/Screenshots and Cut, it wont Paste.

I'll give the X11 path a go too.

---

