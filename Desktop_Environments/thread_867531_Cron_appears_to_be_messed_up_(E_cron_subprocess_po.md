---
title: "Cron appears to be messed up (E: cron: subprocess post-installation script returned e"
date: 2008-07-22
forum: Desktop Environments
---

### Post by bujutsukai on 2008-07-22
So, my last couple of attempted updates (update manager) have thrown the following error:

E: cron: subprocess post-installation script returned error exit status 1

The first time I saw this error was after trying to install Adeona, an open source program written to help recover lost/stolen laptops.  There is a need to make a cronjob to set the program to run at reboot.  I could never get the line to stick in the Cron file, but now I'm getting the above error.  I tried reinstalling Cron from the Synaptic package manager, but that also throws the above error message.

This is what is listed (nothing) when I type "sudo crontab -e" in terminal:

# m h  dom mon dow   command

I'm not sure what to do at this point and could sure use some help.  I believe this will continue to have an adverse affect on further update attempts.

The attached screenshot show my last Update attempt with the cron error.

Please help.

---

### Post by ahmedh on 2008-07-27
I need help with this too. I have the exact same problem for the same reason (Adeona).

---

### Post by MJN on 2008-07-30
Whilst not fixing your problem, a workaround for running Adeona at reboot is to put the advised crontab line (without the @reboot prefix) into /etc/rc.local

That said, I'm not getting any joy with Adeona - it keeps failing after a variable amount of time with a Segmentation Fault. Have you guys had any trouble with it (aside from editing your crontab for it of course)?

Mathew

---

