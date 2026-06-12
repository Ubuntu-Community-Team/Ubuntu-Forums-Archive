---
title: "Changed resolution and now 'Out of Range'"
date: 2009-03-30
forum: General Help
---

### Post by ericnord on 2009-03-30
Hey everyone,

Picked a wrong choince in my Nvidia-Settings app and now I cannot correct it. I've done a ctrl-alt-f4 at boot and the ran the xorg.conf reconfigure, but it didn't help, still 'out of range' once it boots.

Tried something else someone suggested and that got me to the desktop w/ a bad resolution, then when I went to Nvidia it said it wasn't the active driver, turned it self on, right back to out of range.

How do I get this back working? xorg.conf file has no resolutions or hertz listed. All just 'default monitor', 'default device', etc.

Thanks

---

### Post by dcstar on 2009-03-31
> **ericnord said:**
> Hey everyone,

Picked a wrong choince in my Nvidia-Settings app and now I cannot correct it. I've done a ctrl-alt-f4 at boot and the ran the xorg.conf reconfigure, but it didn't help, still 'out of range' once it boots.

Tried something else someone suggested and that got me to the desktop w/ a bad resolution, then when I went to Nvidia it said it wasn't the active driver, turned it self on, right back to out of range.

How do I get this back working? xorg.conf file has no resolutions or hertz listed. All just 'default monitor', 'default device', etc.

Thanks

Delete/rename any hidden .nvidia files/folders in your home directory.

---

### Post by ericnord on 2009-04-01
Thanks for the response. I will give that a try later this when I get home. Last night I was able to login using a low graphics mode (not Nvidia) and went in and downloaded the latest Nvidia thinking that it would start w/ a clean file. Rebooted and went back to 'Out of Range' so I'm assuming deleting/renaming the files per your suggestion will help. I didn't know where they were located.

Thanks

---

### Post by rattking on 2009-04-01
* Having problems with reading comprehension! please ignore

---

### Post by ericnord on 2009-04-02
Looked in home directory and no .nvidia hidden/shown files (yes I'm selected to view hidden files). Only thing I could find that looked helpful was a /config folder in home that had a monitor.xml file. It had the incorrect resolution in it, so I edited, saved, confirmed, rebooted, same 'out of range' issue. can only boot in 'low graphics mode'.

Any other suggestions on where nvidia is pulling this info from? I check nvidia-settings-rc, but that doesn't have resolution in it.

thanks

---

