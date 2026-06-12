---
title: "did i compromise my encrypted drive when I tried to address my hibernate issues?"
date: 2012-05-08
forum: Desktop Environments
---

### Post by GOwin on 2012-05-08
I had an issue with hibernating on Xubuntu 12.04 (on 10.04, the laptop hibernate works fine) which has been resolved. See my thread [here](http://ubuntuforums.org/showthread.php?t=1975000&page=2)

While troubleshooting the problem, we found an "unknown" partition that is supposedly an encrypted partition not working. I took out my livecd and reformatted the said partion as linux swap, updated /etc/fstab, /etc/initramfs-tools/conf.d/resume to match the new UUIDs and finally did a
$ sudo update-initramfs -u

This last command warned me about an error:
cryptsetup: WARNING: failed to detect canonical device of /dev/dm-0

At the same time, I tried to hibernate and it now works - kinda. It will hibernate and resume but it will not ask me for a password, just sends me straight to my last desktop state.

I would like to know if I compromised my encrypted drive by doing what I did, and how do I address the issue with resuming a session without asking for a password

---

### Post by mips on 2012-05-08
Maybe just to get helped quicker post the outputs I requested from post#13 onwards here so people have a quick reference without having to go look at the original thread. Also post that error you got wrt crypt.

---

### Post by GOwin on 2012-05-08
I found this helpful tip from Toz from the original thread. 

> **Toz said:**
> 
As for the encrypted swap remnants, have a look at this link: [http://www.logilab.org/blogentry/29155]("http://www.logilab.org/blogentry/29155"). I think you just need to remove that final remnant. 

I don't believe that an encrypted swap is necessary for an encrypted home, but its generally considered best practice to encrypt the swap if your in the need for encryption.

---

