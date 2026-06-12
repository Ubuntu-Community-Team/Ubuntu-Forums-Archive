---
title: "unsave profiles on ubuntu 11.10"
date: 2012-01-05
forum: Desktop Environments
---

### Post by talkingtek on 2012-01-05
How do you unsave profiles on Ubuntu11.10?  For example, I've download a  bunch of files to Downloads folder, but I want it to delete or cleanup  after logoff or restart the system.  

I was able to do it on 10.04 with /usr/local/bin/cleanup.sh file and set it on /etc/gdm/PostSession/Default

but I didn't find the same file under /etc/lightdm/

Anyone?

---

### Post by spacecheck on 2012-01-05
what would happen if you simply set the download folder to /tmp ? Isn't /tmp supposed to clear on shutdown?

---

### Post by talkingtek on 2012-01-06
> **spacecheck said:**
> what would happen if you simply set the download folder to /tmp ? Isn't /tmp supposed to clear on shutdown?

thanks, I'll try that and will post and update if it's working.

---

### Post by talkingtek on 2012-01-09
it doesn't work..

---

