---
title: "hangs while updating gstreamer plugins"
date: 2005-10-11
forum: Desktop Environments
---

### Post by orzechowskid on 2005-10-11
Every time I update my gstreamer0.8 plugins, either through synaptic or apt, the update process hangs.  The last message on the console reads "setting up gstreamer-0.8-(plugin name)..." , and nothing happens afterwards.  ps -A shows a process called 'gst-compprep-0.8' , which I think is getting stuck somehow.  Anyone know why this would be?

Thanks in advance for any help.

- Dan

---

### Post by KingBahamut on 2005-10-11
If memory serves me correctly, I think thats there is a bug in gst-compprep-0.8 at installation, that causes some kind of a fault. I cant quite remember what it is though.

---

### Post by orzechowskid on 2005-10-12
Thanks for your reply.

Because of this, every time I run aynaptic or apt to install security updates or whatever, dpkg tells me it was interrupted previously (when I kill -9'd it) and I need to run dpkg --configure -a to fix it.  However, this causes dpkg to try and install/configure the gstreamer plugins it choked on last time, which causes the problem all over again.

What exactly is dpkg getting stuck on, and how can I make it think there's nothing to resume so I can install the rest of my security updates?

thanks

---

