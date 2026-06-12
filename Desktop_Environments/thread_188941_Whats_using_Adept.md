---
title: "Whats using Adept?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by jrd on 2006-06-04
I was wondering what could be using Adept. I dont have any updates or anything going, and just booted my computer not long ago. Is there a way I can tell?

---

### Post by Feanor on 2006-06-04
It seems that another program was using the db of apt. If you use more than one of them (like synaptic, kynaptic, adept, apt-get from shell or aptitude) only the first you've launched will work properly. Try to see what process are running and eventually stop the one that uses the db of apt.

---

### Post by johnc4510 on 2006-06-04
Only one of the following package managers can run at any one time:
Synaptic Package Manager
Ubuntu Update Manager
apt-get in a terminal
If you try running one while another is open, it will not let you.

---

### Post by jrd on 2006-06-04
I'm not running any of those. I tried restarting but it still does it. Here are some screenshots of all the things running.

---

### Post by jrd on 2006-06-04
I don't know what it was but this command fixed it.

sudo dpkg --configure dpkg

---

