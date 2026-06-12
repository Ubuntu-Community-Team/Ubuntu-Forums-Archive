---
title: "Kernel update problem on E1505"
date: 2007-06-02
forum: Dell  Ubuntu Support
---

### Post by ernestw on 2007-06-02
Just got my brand new Inspiron E1505 with Feisty Fawn on it from Dell.  Turned it on and was pleased to see things just work.  Unfortunately after letting Update Manager update some packages and forcing me to reboot, grub would fail with the message:

"Unable to mount partition"

Long story short - the kernel upgrade pulled down by Update Manager altered grub to start with:

root (hd0,0)

This is a problem - digging around my old menu.lst, I found that the Inspiron E1505s are supposed to run:

root (hd0,2)

Changing menu.lst to use root (hd0,2) fixed my problem and I'm able to continue with my life.  I hope that my laptop is an isolated incident although I fear it isn't.  Anybody else run into this problem?

---

### Post by benanzo on 2007-06-02
I didn't have that problem when I updated my new XPS 410n, but that definitely seems like the risk you take when /boot isn't the first partition on the disk.

---

### Post by nescafe1001 on 2007-06-02
This appears to be a problem with the Dell factory install -- the issue (along with a fix) is described on the [[COLOR="RoyalBlue"]Dell Linux wiki[/COLOR]](http://linux.dell.com/wiki/index.php/GRUB_error_17_after_kernel_update) and the [[COLOR="RoyalBlue"]Dell community forum[/COLOR]](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&thread.id=9851).

If you just got your shiny new Inspiron with Ubuntu, you might want to see if your system is affected before letting the system install a kernel update.

---

### Post by caro on 2007-06-02
Thanks for the info Nescafe1001.   I had the same problem and hopefully it's fixed now.

---

### Post by junction-tim on 2007-06-04
Had the same problem and did the same fix. I also had a terrible screen resolution issue which was fixed via 915resolution. Other than that I am excited to be using a beautiful new laptop. I am sure there will be plenty of tears but for now it is all looking great.

---

### Post by SlackNerd on 2007-06-04
Fed Ex just brought my E1505 bundle of joy.  I had the same problem and am just tickled pink that I just logged on to the web before the update (again) and found the fix.  Gonna give it a go.  Thanks so much for sharing, y'all!
:popcorn:

---

### Post by nescafe1001 on 2007-06-06
Can a mod make this thread sticky?

---

### Post by kerristallax on 2007-06-06
Same problem yesterday, wish I had looked here before using Dell's "RESTORE TO FACTORY DEFAULTS" and wiping out everything.  It's good to know that there is a simple fix.  


Thanks!

---

