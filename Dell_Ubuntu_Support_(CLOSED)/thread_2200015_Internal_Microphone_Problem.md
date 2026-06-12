---
title: "Internal Microphone Problem"
date: 2014-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Shiran_Maor on 2014-01-17
Hi all,

I am using Ubuntu 13.04 hosted by Windows 8.1. (Windows is my primary OS)
Before upgrading to Windows 8.1( don't know why I did that) my microphone was working fine.
Since I upgraded my Windows, my microphone stopped working.
I searched the internet for solutions and tried many things like changing things in [COLOR=#333333][FONT=arial]/etc/modprobe.d/alsa-base.conf
[/FONT][/COLOR]but non of them were helping (only got worse).
My PC is DELL INSPIRON (laptop).
One more detail is that I can't open Multimedia Systems Selector (I am sure it is installed). When I am trying to run in the terminal gstreamer - properties I get this message: 
"No command 'gstreamer' found, did you mean: Command 'streamer' from package 'streamer' (universe)
gstreamer: command not found"

Thanks

---

### Post by mikewhatever on 2014-01-17
Hi, and welcome to the forums.
I am not sure what we can do here about your W8 upgrade. Ask at your Windows help&support forum.

...about your other problem, your correct command is **gstreamer-properties**. No spaces!

---

