---
title: "[Lirc -CinergyT2] Remote control doesn't work correctly"
date: 2006-09-27
forum: Desktop Environments
---

### Post by eurika on 2006-09-27
Hello, 

I have installed the remote control's cinergyT2 and I stay on a particular problem, I'm trying to explain it : 

- Lirc compilation is good
- irw or irckik (kde lirc) can connect on /dev/input/event3

but i think the remote control is recognized like a mouse or keyboard because in irw, when i press buttons i have : 
 &é"'_à_(

Do you know this problem ?

eurika.

---

### Post by SeanHodges on 2006-11-04
It sounds like you might be using the wrong lircd.conf file, 

This guide might be helpful: [http://www.ubuntuforums.org/showthread.php?t=183545](http://www.ubuntuforums.org/showthread.php?t=183545). It refers to Hauppauge remote controls, but the same process relates to other models.

Once things are working, make sure you create a symlink for /dev/input/remote... because each time you reboot, the eventX number can change. There are some instructions on the link above, or you can follow the instructions I have given here: [http://ubuntuforums.org/showthread.php?t=222672](http://ubuntuforums.org/showthread.php?t=222672)

I will monitor this thread in case you still have problems.

---

### Post by fdimmling on 2006-11-04
I'm using the Cinergy T2 with Lirc on a Dapper system. It just worked out of the box without doing any configuration - of course only the basic things like Volume and Channel by number entering.

Friedrich

---

