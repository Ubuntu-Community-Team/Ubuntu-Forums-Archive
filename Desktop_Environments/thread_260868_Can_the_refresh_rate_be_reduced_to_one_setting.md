---
title: "Can the refresh rate be reduced to one setting"
date: 2006-09-19
forum: Desktop Environments
---

### Post by BirdZerk on 2006-09-19
I am having a problem with the refresh rate being changed when I go to full screen in VMware server.  Is it possible to alter xorg.conf and reduce the refresh rate to just one setting, that way when VMware goes to full screen there is no other possible settings available?  Or, is this a bug with VMware server that can not be fixed yet?

---

### Post by wkulecz on 2006-09-19
I don't know about VMware, but I know you can change the V refresh from say 52-100 to 60 in xorg.conf and have only 60 Hz refresh modes available.  I had to do this to get my Sony LCD to display 1920x1600.

--wally.

---

### Post by BirdZerk on 2006-09-19
Thanks that fixed the problem, perfectly!  Did not know you could do that with V refresh.

---

