---
title: "Possible solution for beryl working, but slow response time."
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by Smuve on 2007-03-21
Here's the quick answer.  Check your xorg.conf for the UseFBDev option.  If it is "true" change it to "false".

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

Find your Device Section that looks something like this:

```
Section "Device"
	Identifier	"GeForce 6800"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"false"
	Option 		"TripleBuffer" 		"false"
	Option         	"RenderAccel" 		"true"
	Option         	"AllowGLXWithComposite" "true"
EndSection
```

If Option UseFBDev "true", change it to "false."  Save and restart X (Ctrl+Alt+Backspace).

---

### Post by Smuve on 2007-03-21
I wanted to get the quick answer in there before I gave the long explanation.  I found this fix via google last night, then did a search in here and found 0 results for FBDev.  So I thought I would post it for others.

I've had beryl *working* with my nvidia GeForce 6800 for quite some time now, but it always had a very *slow* response time.  Every time a tried to do something (open a window, close a window, change tabs in web browser), it would pause before it did anything, then render very quickly.  This was rather annoying, so I removed beryl from my session startup.

However, I knew my hardware could handle it, so I went looking for a solution.  I kinda figured that it was a hardware acceleration problem because my system monitor always showed a cpu spike that coincided with the pauses mentioned above.

The obvious place to look is xorg.conf.  I made a backup and was simply going to delete the UseFBDev line, but then decided that a quick search might save me from borking my system.  I was right about FBDev, but it's always nice to know why.  I found this:

"fbdev is an XFree86 driver for framebuffer devices. **This is a non-accelerated driver**, the following framebuffer depths are supported: 8, 15, 16, 24. All visual types are supported for depth 8, and TrueColor visual is supported for the other depths. Multi-head configurations are supported."

I'm not sure how it got in there in the first place, but I would guess that I chose the wrong option somewhere during my last
```
sudo dpkg-reconfigure xserver-xorg
```

Beryl is now running smooth as silk, immediate reactions and fluid animations.

I hope this helps someone else get the delicious eye candy to satisfy their sweet tooth.

---

