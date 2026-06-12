---
title: "Wine broken after most recent update"
date: 2010-08-12
forum: Desktop Environments
---

### Post by phamnewan on 2010-08-12
I ran the update manager this morning and after that wine is broken.  Wine had been working without issue for a long time, but now anything that uses wine is not working.  I have re-installed wine and even updated to 1.3, but to no avail.

The oddest part is that dozens of error windows are popping up for about 20 seconds and then they stop opening and then clear out.  What would have changed in a recent update that would generate the errors I have listed?


Following is the errors that are happening.


wine: Unhandled page fault on read access to 0x00000000 at address 0x403d7f2f (thread 00d0), starting debugger...
err: xrender:get_xrender_format_from_color_shifts No XRender format found!
err: xrender:get_xrender_format_from_color_shifts No XRender format found!
err: xrender:get_xrender_format_from_color_shifts No XRender format found!
err: xrender:get_xrender_format_from_color_shifts No XRender format found!
err: xrender:get_xrender_format_from_color_shifts No XRender format found!
Maximum number of clients reachederr:winediag:x11drv_init_thread_data x11drv: Can't open display: :0.0. Please ensure that your X server is running and that $DISPLAY is set correctly.

---

### Post by phamnewan on 2010-08-12
Bump.

This is not a wine problem, but something that broke during an Update manage update.

Part of my problem is that I can't find the list of things that were updated this morning so I can figure out what packages changed.  Once I have that I should be able to fix this.

Where is the list of package updates?

---

### Post by Wisp558 on 2010-08-12
It's a wine thing. If you want your wine to remain stable, you should try just compiling it from source, and keeping the version that works.

The log you want is in /var/log/dpkg.log

DPKG powers synaptic/apt-get, btw.
Best of luck.

---

### Post by phamnewan on 2010-08-14
Thanks for the feedback.  Will add more when I get time to work on it.

---

