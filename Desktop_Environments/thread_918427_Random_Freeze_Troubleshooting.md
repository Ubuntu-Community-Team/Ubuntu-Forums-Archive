---
title: "Random Freeze Troubleshooting"
date: 2008-09-12
forum: Desktop Environments
---

### Post by squiggie on 2008-09-12
I've recently installed Ubuntu 8.04.1 and everything is working ok except my system will hang randomly and I cannot do anything on. It is a complete hang; I cannot ssh to it, move mouse or keyboard doesn't respond. I can't ctrl+alt+F1 or anything else. I have to hard reset it to get it back up. 

I think it has something to do with Mythfrontend, but I'm not totally for sure. I have looked through all the logs that I can think of, but I can't see anything that makes sense for the crashed (that I can tell, I'm pretty newbish). My problem is I don't know really how to begin troubleshooting it other than looking in /var/logs and those don't give me any direction really.

Does anyone have any suggestions for me on where to look to troubleshoot? Please forgive me if I didn't include enough information.

---

### Post by knattlhuber on 2008-09-13
You could post the output of /var/log/syslog and/or dmesg (from before the crash occurred) here and see if anybody can make sense of it.

---

### Post by squiggie on 2008-09-13
Attached are the syslog and dmesg files from the latest crash at 15:47:22 today.

---

### Post by alecz20 on 2008-09-26
I think I have the same problem as you.

Using ubuntustudio, the system freezes completely, usually when idling, and the HDD light is a steady ON.

I suspect it's the video card... but I am not sure... still looking for a solution myself.

just one question: did you just enable the NVIDIA driver, or did you install it from the NVIDIA website? (I did the latter)

---

### Post by quemaneumaticos on 2008-09-26
My ubuntu freeze too like yours. It only happens some times. I think this is a known bug.



P.D.How can i post a quick reply? I have to mark something, but i dont find it.

P.D.2.Sorry for my english.

---

### Post by squiggie on 2008-09-26
I think I have nailed this down on my machine. The only time my box freezes is when I watch the Live TV option from withtin MythTV. That seems to freeze it within a matter of minutes. Has anyone had issues with this before?

---

