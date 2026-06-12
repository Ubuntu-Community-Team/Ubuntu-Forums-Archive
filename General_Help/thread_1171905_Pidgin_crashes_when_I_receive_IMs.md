---
title: "Pidgin crashes when I receive IMs"
date: 2009-05-27
forum: General Help
---

### Post by xjgnsdof on 2009-05-27
I'm running 9.04 (64-bit) and get the following error message with the crash:

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.

(pidgin:31360): GStreamer-CRITICAL **: 
Trying to dispose element play, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(pidgin:31360): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:31360): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed
Segmentation fault

---

### Post by xjgnsdof on 2009-05-28
up

---

### Post by xjgnsdof on 2009-05-28
Disabling the sound remedied the problem. I can live with that.

FYI, I am using Pidgin version 2.5.6 in 64-bit Jaunty.

---

### Post by Sef on 2009-05-28
Have you checked to see if this problem has been filed and if not, then have you filed a bug report?  

I have used pidgin on my computer with 64-bit Jaunty and have not had this problem.

---

### Post by xjgnsdof on 2009-05-28
I've seen similar behavior: Pidgin crashing after startup, randomly, when sending IMs to offline people, etc. The people experiencing these crashes also get the same error message and reported their bugs. Hopefully this will go away with a future update.

---

### Post by jonobr on 2009-05-29
not sure if this is related but after upgrading to 9.04 I had similar issues and I think it was some pidgin plugin problems I had.

[Here]("http://ubuntuforums.org/showthread.php?t=1136859") is the forum where I got the info to rename purple and try again.

This removed all those plugins and allowed me to start from scratch again.

---

### Post by Yashiro on 2009-05-29
Use the Pidgin version that shipped with 9.04 instead.

---

### Post by xjgnsdof on 2009-05-29
> **Yashiro said:**
> Use the Pidgin version that shipped with 9.04 instead.

That too has the same problem on my machine.

---

### Post by Yashiro on 2009-05-29
Shame. 2.5.2 from Hardy does not have this issue I believe. You could try it. Be aware that you need to remove your older versions of Pidgin and libpurple*.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by xjgnsdof on 2009-08-07
up

---

### Post by xjgnsdof on 2009-08-07
What does this mean?

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
Segmentation fault

---

### Post by xjgnsdof on 2009-08-07
[http://ubuntuforums.org/showthread.php?p=7748665#post7748665](http://ubuntuforums.org/showthread.php?p=7748665#post7748665)

Post #4 did the trick for me

---

