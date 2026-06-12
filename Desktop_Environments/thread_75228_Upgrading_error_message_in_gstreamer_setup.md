---
title: "Upgrading error message in gstreamer setup"
date: 2005-10-13
forum: Desktop Environments
---

### Post by davidjneff on 2005-10-13
I updated two computers last night from hoary to breezy by changing the apt repository list.  On my newer laptop, I didn't see anything go wrong, rebooted, things look good.  

But on a fairly old Celeron based desktop, I an error message every time any gstreamer component was being setup:

Illegal instruction execution in liboiltest.c (line 247):  [with a cryptic "somethingorother"_16_MXX type symbol name).

I had to leave for work before the upgrade was complete, so I'm not sure if this error message will matter.  Should I be worried?  Any suggestions.  Mainly I just need Gstreamer to play back mp3 audio I think.

Thanks a bunch.

---

### Post by pulp on 2005-10-15
Hi,

I got the same errormessages, but all multimedia things seem to work. Nevertheless I would be interested in the origin and the consequences of this error.

thanks

// edit: I looked through Bugzilla and found out, that its only a warning and not an error. So it is harmless. 

[http://bugzilla.ubuntu.com/show_bug.cgi?id=12362](http://bugzilla.ubuntu.com/show_bug.cgi?id=12362)

---

