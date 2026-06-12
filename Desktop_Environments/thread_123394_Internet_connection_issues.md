---
title: "Internet connection issues"
date: 2006-01-29
forum: Desktop Environments
---

### Post by equal on 2006-01-29
Here's an interesting situation. I've recently aquired a new laptop, and (laziness prevailing) I haven't gotten an additional RJ45 cable to connect this third computer to my router. So I'm constantly switching the network cable from my Ubuntu desktop to the laptop. 

However, I've noticed that when I disconnect the desktop from the network for any significant amount of time, it is unable to detect the connection when I re-attach the cable. Even restarting X doesn't fix this, I'm actually forced to reboot. 

Is there a simple command to make it notice the connection is back? I feel like I'm running Windows with all this rebooting! ;)

---

### Post by darth_vector on 2006-01-30
```
sudo /etc/init.d/networking restart
```should do it for you

if that doesnt work - it may not - then you may have a problem with your /etc/network/interfaces file. i remember having issues whenever i restarted networking once.

---

### Post by stevea1210 on 2006-01-30
Check your /etc/network/interfaces file.  Assuming that eth0 is the adapter, there should be a line in there that says 

```
auto eth0
```

Restarting networking per the above post should also work.

---

