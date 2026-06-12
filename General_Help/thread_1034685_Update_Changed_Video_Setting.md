---
title: "Update Changed Video Setting"
date: 2009-01-08
forum: General Help
---

### Post by Sorceress on 2009-01-08
This is the second time this has happened how do i get it to stop doing that and how do i get my old setting back 

am not familiar with ubuntu yet to terminal as i was kde user till i couldn't get my pogo games to work with kde anymore so had to switch to ubuntu

---

### Post by tuxxy on 2009-01-08
To restore them back to original settings you ahve two options;

1. Boot into recovery mode by pressing delete at the GRUB screen and select recovery mode.  Once loaded select the xfix option, once completed then proceed to continue with normal boot.

2. If you can access a terminal then run the following command
```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Sorceress on 2009-01-08
ok will try that but how do i keep the updates from changing settings again

---

### Post by tuxxy on 2009-01-08
Im not too sure is it your resolution we are talking about

---

### Post by Sorceress on 2009-01-08
this latest update went from a 1024 resolution to the 800x600 screen resolution

---

### Post by Sorceress on 2009-01-08
tuxxy option one worked but now how do i keep updates from messing with the video settings

---

