---
title: "black boot screen after update"
date: 2012-10-08
forum: Desktop Environments
---

### Post by bravegag on 2012-10-08
Hello,

I have Ubuntu 10.11 Desktop. I didn't take updates for 2 months and was at kernel 3.0.23-generic. I also installed back then the nVidia driver directly from nVidia. Today took the update containing 154 changes :( and can't boot anymore. After the GRUB menu I get a black screen.

How can I repair it? any pointers? hints?

TIA,
Best regards,
Giovanni

---

### Post by cipherboy_loc on 2012-10-08
Can you access a TTY by using **Ctrl+Alt+F1**? If so, others can instruct you how go view the logs (dmesg command) and see what the problem is. Do you ever get to a full desktop environment, or are you always stuck at a black screen?


Thanks,
Cipherboy

---

### Post by bravegag on 2012-10-08
> **cipherboy_loc said:**
> Can you access a TTY by using **Ctrl+Alt+F1**? If so, others can instruct you how go view the logs (dmesg command) and see what the problem is. Do you ever get to a full desktop environment, or are you always stuck at a black screen?
Cipherboy

Thank you for your answer.

After GRUB can't get in ... stays at black screen, while at the black screen the **Ctrl+Alt+F1 **doesn't work. I tried entering in "recovering mode" second GRUB choice and it gets stuck in the following message forever:
...
Loading initial ramdisk ...
_

I have also tried troubleshooting but choosing the previous kernel 3.0.23, same issues ...

Is there a command I can run in GRUB to get in in command line mode at least? so I can uninstall the nVidia driver?

I really believe Ubuntu has some serious usability issues, if after taking updates one can not boot any longer ...

---

### Post by cipherboy_loc on 2012-10-08
You could try using a livecd and chrooting to see what the issue is, but likely I would save your data (where a separate /home partition comes in handy) and re-install. However, **do not do this** until others have posted. To me, it looks like an update was hosed somehow with nvidia and a new kernel. Maybe the nvidia drivers didn't get built into the new kernel?

---

### Post by bravegag on 2012-10-08
I have said it, I took the updates without uninstalling the nVidia driver first. I know this is not the way to do it but leading to an unbootable system is a bit ridiculous. I think the Ubuntu developers have no idea what robustness means ...

---

### Post by bravegag on 2012-10-08
OK fixed it. 

First, thank you for bringing up the term "Chrooting", I searched for it and followed directions from this page [http://www.tuxation.com/chrooting-into-a-linux-environment.html](http://www.tuxation.com/chrooting-into-a-linux-environment.html) to use the LiveCD to gain access into the broken Ubuntu installation. I then moved the file:
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia

ejected the LiveCD disk, rebooted and now Ubuntu boots fine. I will install the latest nVidia drivers and I should be good to go.

---

### Post by daslinkard on 2012-10-08
> **bravegag said:**
> I have said it, I took the updates without uninstalling the nVidia driver first. I know this is not the way to do it but leading to an unbootable system is a bit ridiculous. I think the Ubuntu developers have no idea what robustness means ...

Since you have this fixed (now)....can you show some love to the Ubuntu developers?  Also, please mark this thread as Solved!!

---

