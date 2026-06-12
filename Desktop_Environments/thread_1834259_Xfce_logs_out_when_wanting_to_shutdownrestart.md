---
title: "Xfce logs out when wanting to shutdown/restart?"
date: 2011-08-27
forum: Desktop Environments
---

### Post by ojdon on 2011-08-27
I'm currently using Xubuntu and when I get to the options to shutdown or restart it logs out instead. Which is a bit of an annoyance. My friend also has the exact same issue as me on his laptop which is also using Xfce. Is there a fix for this?

---

### Post by Toz on 2011-08-27
It appears to be a bug: [https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/711571]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/711571")

Some people have had success with the following procedure: [http://ubuntuforums.org/showpost.php?p=10943741&postcount=5]("http://ubuntuforums.org/showpost.php?p=10943741&postcount=5")

I've added **ck-launch-session startxfce4** to **~/.xinitrc** and made the file executable. Shutdown/restart works for me about 90% of the time - much better than before.

---

### Post by ojdon on 2011-08-27
Tried that. Seems for me it only Shutsdown 10% of the time. =P 


So nobody has any other possible solutions?

---

### Post by xeemo on 2011-09-11
I just reinstalled ubuntu after a long time of not using it.  I installed xfce4 and I was having this problem.  I found that if i tab over to shutdown and press enter it works, while if I just click on it, it doesn't.  I have not seen this problem in any other distro.

Edit: ...guess it was just a lucky couple times.  i have this problem too.  i'll just leave it at that.

---

### Post by hasfar on 2011-10-04
i was having the same problem. im using a dell desktop. what i did was i kept the power button pressed and forced the cpu to shutdown. then i turned it back on again and the problem seems to have vanished for now. i hope this helps

---

### Post by rojaasensei on 2011-10-04
Hasfar's trick works for me too.

 I found the bug appears if I have been making changes to a panel.

---

