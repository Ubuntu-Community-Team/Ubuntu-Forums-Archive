---
title: "Problem Upgrading"
date: 2009-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by epb223 on 2009-04-26
I have Ubuntu 8.04 on the Mini 9. I understand that I need to upgrade to 8.10 before I can upgrade to 9.04, but the instructions on [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) don't work for me, because there is no option under Software Sources to change the Upgrades to Normal Releases. I'm very confused!

Edward

---

### Post by xuCGC002 on 2009-04-26
Press Alt+F2 or go to Applications>Accessories>Terminal, and type ```
update-manager -d
``` and hit enter. It should bring up update manager with an option to download 8.10.

Edit: After reading the below post, this is obsolete unless you install 8.10/9.04 via a fresh install. I didn't know that Dell had a separate set of repositories and a custom kernel, so this is my bad.

---

### Post by Cowchip7 on 2009-04-26
> **epb223 said:**
> I have Ubuntu 8.04 on the Mini 9. I understand that I need to upgrade to 8.10 before I can upgrade to 9.04, but the instructions on [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) don't work for me, because there is no option under Software Sources to change the Upgrades to Normal Releases. I'm very confused!

Edward

Edward,

Are you using Dell's pre-installed Ubuntu? If you are, you cannot upgrade to a newer version unless Dell adds a new version to their repositories. This would be very unlikely as 8.04 is a long term release and supported until 2011.

Without getting into too much detail, Dell's pre-installed Ubuntu on the mini 9 has an lpia custom kernel. In other words, Dell customized the kernel and optimized it for use on an atom processor. Supposedly, the lpia custom kernel improves battery life and boot time.

If you really want to update your mini 9, you would have to download the 9.04 iso and do a fresh install. You can find the information you need here: [www.ubuntumini.com](www.ubuntumini.com).

Good luck.

---

### Post by epb223 on 2009-04-26
> **Cowchip7 said:**
> Edward,

Are you using Dell's pre-installed Ubuntu. If you are, you cannot upgrade to a newer version unless Dell adds a new version to their repositories. This would be very unlikely as 8.04 is a long term release and supported until 2011.

Without getting into too much detail, Dell's pre-installed Ubuntu on the mini 9 has an lpia custom kernel. In other words, Dell customized the kernel and optimized it for use on an atom processor. Supposedly, the lpia custom kernel improves battery life and boot time.

If you really want to update your mini 9, you would have to download the 9.04 iso and do a fresh install. You can find the information you need here: [www.ubuntumini.com](www.ubuntumini.com).

Good luck.

Thank you, that really explains a lot of things that have been baffling me since getting the mini 9 and finding that nothing works exactly like the Ubuntu support materials online say they should.

My sense is that given the customization issue, perhaps it would be wiser for me not to upgrade; would you concur?

Edward

---

### Post by Cowchip7 on 2009-04-26
I haven't upgraded. Everything just works (as of now). And I have not ran into a problem where the Dell repositories lacked a program I wanted. To that end, I will not upgrade until I screw things up so much I need to reinstall. :)

---

