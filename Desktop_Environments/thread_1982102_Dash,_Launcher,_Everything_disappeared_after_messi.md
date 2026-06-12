---
title: "Dash, Launcher, Everything disappeared after messing with ccsm"
date: 2012-05-18
forum: Desktop Environments
---

### Post by vj41 on 2012-05-18
I tried some tweaking with ccsm which worked just fine just until the recent reboot. After that, everything disappeared. I can only see my desktop and mouse. i was able to access terminal so i tried to bring ccsm to default settings again but that didn't work either. I tried other solutions like enabling the plugin but its already enabled. Also tried the,
sudo unity --reset
That didn't work either. And also, now i see a cross over major folders like root etc.?
What just happened to my ubuntu?? :mad:

---

### Post by mcduck on 2012-05-18
> **vj41 said:**
> I tried some tweaking with ccsm which worked just fine just until the recent reboot. After that, everything disappeared. I can only see my desktop and mouse. i was able to access terminal so i tried to bring ccsm to default settings again but that didn't work either. I tried other solutions like enabling the plugin but its already enabled. Also tried the,
sudo unity --reset
That didn't work either. And also, now i see a cross over major folders like root etc.?
What just happened to my ubuntu?? :mad:

just run "unity --reset" and it will reset the Compiz settings back to a working setup.

(Don't use sudo here, that would reset the Compiz/Unity settings for *root user*, not your own user.)

edit: The /root directory is by default inaccessible for any other user than the root itself. SO that's normal. Same goes for /Lost+Found. If you see crosses over some other of the default directories you might want to tell us which ones.

---

### Post by vj41 on 2012-05-19
The system was still not showing anything still... Had to re-install it again... Thanks anyways... :)

---

