---
title: "how do I install Jamboree"
date: 2006-09-03
forum: Desktop Environments
---

### Post by diegoguillen on 2006-09-03
Hi does anyone knows how to install jamboree on Dapper i followed the instructions from here:
[http://ubuntuforums.org/showthread.php?t=32568](http://ubuntuforums.org/showthread.php?t=32568)

but I  have the next error:
checking for gst-inspect... gst-inspect
checking GStreamer element spider... not found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element audioconvert... found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element audioscale... not found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element volume... found.
checking for gst-inspect... (cached) gst-inspect
checking GStreamer element fakesink... found.
configure: error:
The following GStreamer elements are missing:

     spider audioscale

Make sure you have gstreamer and gstreamer-plugins installed, along with their development packages.

but I have the gstreamer-plugins installed

I hope any of you can help me

---

### Post by croak77 on 2006-09-04
You might want to think about using another music player like exaile, listen, quodlibet, muine, amarok etc. I don't think jamboree is really developed anymore.

For your error, jamboree uses gstreamer-0.8 not the current gstreamer-0.10. So make sure you have gstreamer-0.8 and the related -dev packages.

---

