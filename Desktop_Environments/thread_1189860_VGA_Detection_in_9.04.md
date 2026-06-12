---
title: "VGA Detection in 9.04"
date: 2009-06-17
forum: Desktop Environments
---

### Post by GrandBob on 2009-06-17
Expecting better VGA support, I recently upgraded my laptop to 9.04. PROBLEM: The display configuration dialogue is better. But, while it sees SOME video device out there, it does not recognize my device, a ViewSonic G790.  Any remedy for this?

---

### Post by alienkid10 on 2009-06-17
I have the same problem with my ViewSonic E771! I have been trying to find a fix.

---

### Post by lavinog on 2009-06-17
How old is this monitor?
What connection are you using (vga/dvi)?

I have come across some monitors that seem to not support EDID correctly.
One of my monitors reports that it supports a resolution higher than it actually supports.

You can manually set the supported resolutions in /etc/X11/xorg.conf
in the section labeled screen there should be a subsection labeled display. add the modes line like below with the resolutions you want to support:
```
SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

```

---

### Post by alienkid10 on 2009-06-17
VGA connected to ATI Radeon 4350. Unsure on the OP. My xorg.conf doesn't contain "Screen" section.

---

### Post by overdrank on 2009-06-17
> **alienkid10 said:**
> VGA connected to ATI Radeon 4350. Unsure on the OP. My xorg.conf doesn't contain "Screen" section.

Please do not highjack GrandBob thread when you have your own [thread]("http://ubuntuforums.org/showthread.php?p=7466971#post7466971")
Thanks :)

---

### Post by GrandBob on 2009-06-17
My monitor is at least 10 yrs old.  Note, however, that Ubuntu 8.10 DID recognize the monitor, albeit with no apparent deterministic behavior.

Further, after more than 1 week after installing 9.04 (and since my original post), the monitor IS recognized.  But after tinkering a bit, it, too, is showing very blase reaction, i.e., it seems to take its sweet time (in this case one week) to announce its discovery.

And yes, when detected, it offers all the supported resolutions.

At best, I am passivly resolved about this.

Thanks for your attention.

---

