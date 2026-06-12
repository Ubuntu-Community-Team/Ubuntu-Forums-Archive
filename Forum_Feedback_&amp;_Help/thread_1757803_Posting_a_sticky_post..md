---
title: "Posting a sticky post."
date: 2011-05-13
forum: Forum Feedback &amp; Help
---

### Post by irv on 2011-05-13
I have taken notice of many having problem with Broadcom 43xx wireless cards in Ubuntu 11.04, and I have been trying to help as many as I can. I also had this problem and found a fix. Is there anyway to have a sticky post for other to find. Here is the fix?



A fix for the Broadcom BCM43xx driver in 11.04.

1. I uninstalled “bcm-kernel-source” package,
Code:```
sudo apt-get remove bcm-kernel-source
```


2. I installed “firmware-b43-installer” package
Code: ```
sudo apt-get install firmware-b43-installer
```

3. I installed “b43-fwcutter” packager
Code:  ```
sudo apt-get install b43-fwcutter
```

4. I typed into the terminal:
Code:  ```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'

```

---

### Post by overdrank on 2011-05-13
Hi and I believe this is the [sticky]("http://ubuntuforums.org/showthread.php?t=1604868") you speak of. :)

---

### Post by irv on 2011-05-13
> **overdrank said:**
> Hi and I believe this is the [sticky]("http://ubuntuforums.org/showthread.php?t=1604868") you speak of. :)

I believe you are right, I miss this one. Thanks for pointing it out. I will point other to it.
Thanks again.

---

