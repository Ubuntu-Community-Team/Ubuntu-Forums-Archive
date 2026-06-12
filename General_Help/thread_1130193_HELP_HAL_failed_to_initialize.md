---
title: "HELP: HAL failed to initialize"
date: 2009-04-19
forum: General Help
---

### Post by frOOgz on 2009-04-19
I have restarted my machine and I am getting a "HAL failed to initialize" message.  I have no clue on how to start to fix this.

My keyboard has keys mixed up, no internet conntection, no sound card.  These are obvious problems.

Any ideas on where to start?

---

### Post by s.fox on 2009-04-19
Hi,

I found [this]("http://ubuntuforums.org/showthread.php?t=291130") in the achieves and may be of some use to you.  The poster had the same error as you.  It would appear the error was fixed by reinstalling HAL.

Hope this helps.

-Ash R

---

### Post by frOOgz on 2009-04-19
First I did:

sudo /etc/init.d/hal stop

And then:

sudo hald --verbose=yes --daemon=no 2>&1 | tee /tmp/hal.log

I noticed that the second process couldn't write to some files in /var/cache/hald .  The reason was that /var/cache/hald didn't exist.

I created the dir, rebooted and it seems to have fixed my problem.  This seems a very random problem and I have got no idea why the directory didn't exist.

---

