---
title: "My own desktop effects problem"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by Igotthisusernamefirst! on 2008-02-02
I'm relatively new to ubuntu (and linux in general) so, yeah. I've had ubuntu installed for a while and got it set up with most things. I tried getting my desktop effects working today, after seeing their full extent (lol youtube). I've searched the forums, and understand that they don't work with NVIDIA drivers and Xinerama. So from the threads I read, I got Envy, installed the 169.09 drivers, and got nvidia-settings. When trying to set nvidia settings to use TwinView, I get this message when I click reply:

For all the requested settings to take effect, you must save the configuration to the X config file and restart the X server.

So I click the "Save to X Configuration File", try to save to /etc/X11/xorg.conf, then get the error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

My xorg. conf doesnt change then.
I guess I'm supposed to take the preview of the xorg I need to make from nvidia settings and make another out of it, and make the current one a backup, but I need root rights and dont know how to do it from terminal. Thats my guess, I might be wrong.

So err, help?

---

