---
title: "Microscopic text, fixed once before, has since returned."
date: 2016-03-18
forum: Desktop Environments
---

### Post by Mugsy323 on 2016-03-18
I first sought help for [this problem]("http://ubuntuforums.org/showthread.php?t=2303908&p=13395761#post13395761") last November. I was provided a solution that appeared to work at the time but has since returned. :(

For some unknown reason, the text in my windows (but NOT menus or dialogs) are so tiny they are unreadable. The "solution" I was provided in the previous thread appeared to work but has since returned DESPITE the fact **the suggested "fix" is still there** (setting the font size in the videocard conf file.)

Yesterday, the problem fixed itself after a reboot :confused:, but today, even after 4 reboots, the problem remains. :(

I don't use Ubu every day as my primary OS, so I can't say everything was fine for months then suddenly stopped working. I *did* do an update recently (still 15.10 though), but Ubu was fine after several reboots. Then yesterday, the problem suddenly returned.

Any idea as to what is wrong or how to fix? Thank you.

[IMG]http://s6.postimg.org/g1c5kfc1d/Screenshot_from_2015_11_22_16_43_57.png[/IMG]

---

### Post by buzzingrobot on 2016-03-19
Is the DPI still set at 96 in xorg.conf?

---

### Post by Mugsy323 on 2016-03-21
> **buzzingrobot said:**
> Is the DPI still set at 96 in xorg.conf?

(Sorry for the late reply. Spam filter intercepted your reply.)

Yes, the xorg.conf file still contains the 96 dpi setting I was instructed to add the last time:

> Section "Monitor"
    [stuff]
    Option "DPI" "96x96"
EndSection

Is there a way to test if my xorg.conf file is even being read? That's the only thing I can think of. :(

---

### Post by Mugsy323 on 2016-03-21
Apparently, it's a known issue with the nVidia drivers:

[https://bbs.archlinux.org/viewtopic.php?id=39665](https://bbs.archlinux.org/viewtopic.php?id=39665)

...although the above post is from 2007.

I'm still not entirely sure how to fix. :(

---

### Post by Mugsy323 on 2016-03-21
Okay, I figured out what went wrong.

Somewhere along the line, my "/etc/X11/xorg.conf" file got renamed, so Ubu couldn't find it to load it and was reverting to its default settings.

The solution, "simple" enough, was to copy it to a new file with the correct name. But the /etc/X11/ folder is protected from writes, so from the terminal, you must copy the old file to a new file with the correct filename, then reboot:

(In my case, this was: **sudo cp /etc/X11/xorg.conf.03022016 /etc/X11/xorg.conf**)

Everything appears to be fine now. Very annoying.

---

