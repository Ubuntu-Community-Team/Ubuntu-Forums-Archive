---
title: "xps 13 locking up, no UI response, not sure if anything is alive underneath"
date: 2013-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by octetcloud on 2013-07-03
This is an xps-13 dev edition with 12.04.

This has happened three times this morning... its my second day using xps, first day using usb keyboard and mouse with external HDMI monitor.

I don't have another machine handy to ssh in and see if its just the UI that's frozen.

Anybody else seeing this? What can I do/provide to troubleshoot?

Nothing interesting I can find in the logs, though this "sometimes" happens just before (but other times doesn't).

[   91.090859] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 18070000, was 18000000

---

### Post by mattcole on 2013-07-18
Hey there

Did you ever get this resolved?  I've been on the XPS13 for a couple of months now, but this is becoming a daily occurrence for me.

---

### Post by mattcole on 2013-08-08
FYI, moving to the 3.5 kernel solved this for me.  Some other minor issues have cropped up, but it is much better than random frequent lockups.

---

