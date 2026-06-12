---
title: "Hibernate shuts computer completely off"
date: 2007-06-13
forum: Desktop Environments
---

### Post by NJC on 2007-06-13
I recently posted a thread about my PC automatically shutting down - it seemed to happen around 5pm. It was because I had it set to Hibernate after one hr. As reference I have followed instructions in [this post]("http://ubuntuforums.org/showthread.php?t=237264") to set apm because my BIOS is also older and does not support acpi. Note that implementing this code did not cause my problem. 

I searched Google and the forums but I did not see others with this problem. Is Hibernate causing anyone else's PC to shut off (IE needing reboot)?

---

### Post by dolphin_oracle on 2007-06-13
That's what hibernate is supposed to do.  It saves the contents of your memory to disk and then cuts the power.  When it comes back up, it should be somewhat faster than a normal reboot, and anything that was running at the time of the hibernate should come back up.

You probably want to set it to go to standby instead of hibernate.  That will put your computer into a low power state, but its still operating from RAM.  Moving your mouse, for instance, should make the machine come back to life.

I've never had any problems with it on my old sony vaio notebook, but in looking around the forums it seems to be an imperfect tool.

---

### Post by NJC on 2007-06-13
It hasn't written anything to memory (that I can tell) and when I restart after Hibernate it's as if I had powered the computer down. Boot is not any faster.

Standby doesn't work via Ubuntu, but seems to work if I have it operational from bios. Thanks.

---

