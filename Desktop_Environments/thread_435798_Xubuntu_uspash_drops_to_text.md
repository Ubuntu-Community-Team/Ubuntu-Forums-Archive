---
title: "Xubuntu uspash drops to text"
date: 2007-05-07
forum: Desktop Environments
---

### Post by Steve1961 on 2007-05-07
Hi.  I've just installed Xubuntu feisty on a laptop and everything seems to be working well.  However, when booting the usplash theme launches and then, after about 10 seconds, it drops to a text only bootup.  Everything seems to be working fine, but does anyone know of a fix for this?

---

### Post by metalheart on 2007-05-07
Are you using Nvidia proprietary/binary only drivers? Installing them the Nvidia logo is shown before the logon screen and if you turn the logo off in xorg.conf, the blank screen appears.

---

### Post by Steve1961 on 2007-05-07
No, just using standard savage xorg driver.  I also have only a single ext3 partition for root and a swap partition on my system.

---

### Post by metalheart on 2007-05-07
Does it look like there is a switch to another terminal?

---

### Post by Steve1961 on 2007-05-07
No, usplash just seems to time out and the boot continues in text mode.  I don't know if it's because it's a fairly low spec system - xp1800 CPU amd 256mb ram - but I'm not sure how to increase the usplash timeout.  Any ideas?

---

### Post by metalheart on 2007-05-07
I found something on subject but I'm not sure if this is what you need.

[HOWTO: Fix usplash]("http://ubuntuforums.org/archive/index.php/t-76309.html")

hth

---

### Post by Steve1961 on 2007-05-07
Thanks for the help.  I tried this but no difference.

---

