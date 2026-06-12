---
title: "[SOLVED] Compiz will not activate"
date: 2008-02-19
forum: Desktop Effects &amp; Customization
---

### Post by Jammin80503 on 2008-02-19
I got a e-Geforce 7200 graphics card recently, its not that good, but it is good enough to run Compiz. I got the driver working (with some difficulty, I had to have envy do it for me) and its very nice. Now, when I try to activate Compiz, which is what I got the card for, it does this:

```

checking for Xgl: not present.
no whitelisted driver found
aborting and using fallback: /usr/bin/metacity

```

The GUI alternitive just says "Desktop effects could not be enabled"

I looked around the forums and found something about Xgl, and followed the instructions, but apparently it didn't work.
thanks!

---

### Post by Cows on 2008-02-19
I have the same problem. This is my thread :

[http://ubuntuforums.org/showthread.php?p=4362454](http://ubuntuforums.org/showthread.php?p=4362454)

---

### Post by FuturePilot on 2008-02-19
Did you install the restricted driver?
System&#8594;Administration&#8594;Restricted Driver Manager

---

### Post by Cows on 2008-02-19
I don't have any restricted drivers. I went to the Restricted Drivers manager and it says I don't need any.

---

### Post by Jammin80503 on 2008-02-19
I have the restricted driver activated, and everything looks to be working fine.

---

### Post by Jammin80503 on 2008-02-19
nevermind, i got it working. it turns out my restricted driver needed to be configured, for some reason. (nvidia-xconfig in terminal) after doing that, all my problems were solved. sorry for the hassle, everyone.

---

