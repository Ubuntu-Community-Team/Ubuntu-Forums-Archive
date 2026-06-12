---
title: "can't boot up in ubuntu  9.10"
date: 2010-02-06
forum: Desktop Environments
---

### Post by ghetelek on 2010-02-06
I try to put up and i get a screen message

[3.114207] kernel panic-not syncing:VFS:Unable to mount root fs on unknown-block(8,1)

and my caps lock and scroll lock light flashes on and off and nothing works.  I have to turn of my computer and log on to windows vista.  I'm a novice and know nothing about computer programing.  This is the second time it happened to me. The first time i just reinstalled everything and lost all my old information.  can somebody please help.

---

### Post by the_karmic_koala on 2010-04-18
...have you ever booted to it? Are you using the right kernel?? Intel or amd???  32 bit or 64? ...i've never seen that....are you using wubi? Or partitioning?

---

### Post by uberlinuxnerd on 2010-04-18
The kernel dose not know what filesystem the root partition is. I suspect that your grub config is incorrect and is pointing to your Vista partition. Can you post your grub.conf and your partition layout please?

---

### Post by hariks0 on 2010-04-18
It happened to me once when I had been a newbie and tried to install Slackware Linux in a very small partition of my HDD. Try giving some more space for Ubuntu. I recomment atleast 10 GB. Reinstall it and post back.

Good luck !:popcorn:

---

