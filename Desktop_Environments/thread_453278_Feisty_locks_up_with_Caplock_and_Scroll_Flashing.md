---
title: "Feisty locks up with Caplock and Scroll Flashing"
date: 2007-05-24
forum: Desktop Environments
---

### Post by svalvasori on 2007-05-24
Hello everyone,

I wonder someone could tell me how to troubleshoot this issue. When the computer is left running for some time, it will lock up and leave the Caps lock and Scroll lights flashing on the keyboard. The only way out of it is a hard reset.

I don't see anything recorded in syslog that tells me what might be causing this, and I don't know how to go about gathering more information to track down what is causing this. It seems to happen in one profile more than the other, so I'm guessing it's application related.

Thanks for any advice,

Steve.

---

### Post by hyperair on 2007-05-24
What you have there is a kernel panic. Try looking for anything that messes around with the kernel, especiall kernel modules.

---

### Post by svalvasori on 2007-05-25
I think you are right, but how do I go about troubleshooting a kernel panic?

---

### Post by swv on 2007-05-25
I have this too. Just installed Fiesty on an otherwise empty disk.  haven't  downloaded anything that would interfere with kernel, although I did let it automatically download updates. Yes it says kernel panic. I have no idea what that means. I am trying to reinstall, but so far it does it also when running from the iso (which I md5 confirmed)

any help with this is much appreciated.....

---

### Post by hyperair on 2007-05-26
Basically a kernel panic generally happens when your hardware fails the kernel. More information could be gotten from /var/log/kern.log. Normally the last few lines of each session will show what happened to cause the kernel panic. I could help you out with troubleshooting that if you post your kern.log here (in an attachment please)

As for the LiveCD kernel panic, I'm not sure how to go about that.. perhaps you could try safe graphics mode? Also could you post your hardware configuration

---

### Post by svalvasori on 2007-05-26
Thanks for pointing me to that log. It looks to me like my USB wireless device (which I'm not using) might be causing this to happen. Seems I always see:

May 24 08:03:21 office kernel: [  792.562395] ubuntu/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
May 24 08:03:23 office kernel: [  794.326147] ubuntu/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL failed

just before another boot sequence. I'll disconnect the device and see what happens. If it happens again I'll post the end of the kern.log file.

Thanks again...at least I know where to look now.

---

### Post by hyperair on 2007-05-26
Good luck. Post again if you need any help :)

---

