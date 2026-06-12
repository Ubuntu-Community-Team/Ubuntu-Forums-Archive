---
title: "UBUNTU 8.04 cannot use in Vista?"
date: 2009-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by firetail on 2009-06-11
Hello all!

Recently I install Ubuntu8.04(32bit) in my laptop(DELL INSPIRON) which already have window vista(original), by shrinking out about 10GB space for Ubuntu.
After installed Ubuntu it just can use for 5 minutes then whole computer hang, initially i thought was screen saver problem, but after i tried for many times, it's not screen saver problem, it hang suddenly(5 minutes) when I was still  using it.I can't even use restart key, I can just press on/off button to shutdown my laptop.

Can someone help me solve my problem?
Thanks!

---

### Post by coffeeaddict22 on 2009-06-12
hi,
Reboot into Linux, and as soon as you get there open a terminal (Applications/Accessories/Terminal) and type in ```
dmesg
```That should give you a heap of output.  Scroll back up to where the numbers on the left suddenly change; they are in seconds of uptime, so you should see the reboot, and the messages just before that will relate to the crash. Post the lines before the crash back if you need more assistance.

If the output looks unremarkable, go back to the terminal and type in ```
cat /var/log/Xorg.0.log
```;  look through that/ post it back as well.  
Have you modified the setup at all?  Have you altered the Linux install?

---

