---
title: "firewall"
date: 2006-09-26
forum: Desktop Environments
---

### Post by satbunny on 2006-09-26
Help!
I ran Firestarter by accident. I cancelled out but now my firewall comes on when I reboot and blocks all traffic which is a bit of a problem on my fileserver.
Since I am behind a hardware firewall on a small home network I don't need a firewall on this machine, how do I turn the thing off permanently as opposed to stopping it until the next reboot suing Firestarter. is it as simple as uninstalling Firestarter?

Thanks, and remember I am behind a hardware firewall, I am not being silly.

---

### Post by x64Jimbo on 2006-09-26
Try running firestarter and turning off the firewall before you close it. Firestarter is just a front-end for built-in features of the OS, and closing it does not change the settings it has made.

---

### Post by pseudonym on 2006-09-26
> **satbunny said:**
> is it as simple as uninstalling Firestarter?
It should be. But to be on the safe side, you might want to set it to allow all traffic first before running 'sudo apt-get --purge remove firestarter'

---

### Post by satbunny on 2006-09-27
Thanks.

Now, if I did want to do this properly where is a good how-to as to how to set Firestarter properly?

---

### Post by x64Jimbo on 2006-09-28
[http://www.fs-security.com/docs/interface.php](http://www.fs-security.com/docs/interface.php)

---

