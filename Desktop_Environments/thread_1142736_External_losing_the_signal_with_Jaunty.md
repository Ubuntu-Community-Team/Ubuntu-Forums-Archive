---
title: "External losing the signal with Jaunty"
date: 2009-04-29
forum: Desktop Environments
---

### Post by vmalep on 2009-04-29
Hi everybody,

I recently installed ubuntu-9.04-netbook-remix-i386 on a Toshiba NB100. I use to connect this netbook to an external monitor. However, with ubuntu 9.04, the monitor is sometimes losing the signal. The sound and the keyboard are still working fine, and the all system I guess, but no more image.

I can switch to the terminal (ctrl-alt-F1), but restarting the Xorg server does not solve the problem.

The netbook screen is still working, but I have to reboot to recover the signal on the external monitor.

Dmesg does not show anything relevant.

Thanks for your help,
Pierre

---

### Post by wessel_k on 2009-05-04
Hi,

Yesterday I found out I have the same issue with my Acer Aspire One 110L. I didn't have that issue with Linpus Lite. Did you already find a solution?

Regards,

Wessel

---

### Post by vmalep on 2009-05-04
Hi Wessel,

Very happy to learn that you have the same problem... Feeling less lonely :P

I found this page: [https://lists.ubuntu.com/archives/universe-bugs/2009-February/049495.html](https://lists.ubuntu.com/archives/universe-bugs/2009-February/049495.html)

It seems that the Intel drivers coming with the new version of Xorg are buggy.

As suggested on that page, I removed the "splash" option of the Grub menu and I am now waiting to see if the problem remains or not...

Best regards,
Pierre

PS: Actually, removing the splash option has not changed anything. To be noted that the screen does not systematically turns black. It sometimes turn white or yellow. And then, no other solution than rebooting from the console mode (Ctrl+Alt+F1)...

---

### Post by vmalep on 2009-05-06
I tried this:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I already noticed that the resolution of the login page is better. Will see if the screen keep freezing or not...

Update:

... But it does not fix the problem...

Moving back to Hardy (8.04) until I learn that the Intel driver is corrected. And next time I am buying a computer, I will make sure that there is no Intel component in it.

---

### Post by vmalep on 2009-05-14
After few more tests, I think it is rather an hardware problem. Indeed, the external screen freeze also with the previous verion of Ubuntu (8.04). But it keeps working at low resolution (i.e. on text mode).

I am using the Toshiba NB100...

BR
Pierre

---

