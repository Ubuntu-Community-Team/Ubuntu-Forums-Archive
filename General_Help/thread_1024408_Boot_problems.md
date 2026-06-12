---
title: "Boot problems"
date: 2008-12-29
forum: General Help
---

### Post by dasim on 2008-12-29
im loading into the command line after downloading updates and trying to add video driver, followed by a reset.

This is what is coming up

Boot from (hd0, 0) ext3 1cce55ba-73456-41fd-a439-8168f26be836
Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/b36010af-d41e-4f54-a79c-334b69271d84)dev(8,5)
kinit: trying to resume from(/dev/disk/by-uuid/b36010af-d41e-4f54-a79c-334b69271d84)dev(8,5)
kinit: No resume image, doing normal boot...

and then user login etc.


Any ideas?

---

### Post by dcstar on 2008-12-29
> **dasim said:**
> im loading into the command line after downloading updates and trying to add video driver, followed by a reset.

This is what is coming up

Boot from (hd0, 0) ext3 1cce55ba-73456-41fd-a439-8168f26be836
Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/b36010af-d41e-4f54-a79c-334b69271d84)dev(8,5)
kinit: trying to resume from(/dev/disk/by-uuid/b36010af-d41e-4f54-a79c-334b69271d84)dev(8,5)
kinit: No resume image, doing normal boot...

and then user login etc.


Any ideas?

You are seeing some normal login stuff because your splash screen is no longer covering it up, fix you splash screen and you won't see it again.

---

### Post by dasim on 2008-12-29
I log in through the command line and then startx and it comes up with the response:

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 11): unable to connect to X server
xinit: No such process (errno 3): Server error

---

### Post by blazini on 2008-12-29
I'm getting pretty much the same thing. 

I upgraded to Intrepid just now and I get the same command line errors you do. At first it booted into low graphics mode, so I enabled the Nvidia restricted drivers and restarted.

Now I get the command line errors then the xorg config screen but the keyboard won't fuction in the xorg screen.

I also noticed when I went into the grub menu (to boot XP so I could post this, unfortunately) there was no option for the 8.10 kernel, just the 8.04 and previous kernels. I should have an 8.10 right?

---

### Post by dasim on 2008-12-29
I tried using the 173 driver for my card, and after enabling it, i restarted to the same problem. I'm going to attempt the 177 driver tomorrow. I'm pretty sure its a driver problem.

---

### Post by dasim on 2008-12-29
Any of the drivers I install do not seem to work. I load automatically into command line after the splash screen. This error has happened on every occassion where I have installed anything to deal with nvidia. I've downloaded and activated the drivers 173 and 177, have opened up system panel and installed nvidia settings and certain files, and this problem happens every time. 

Any help?

---

