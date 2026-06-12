---
title: "Netbook launcher, gconf etc. messed up [Ubuntu 10.04 LTS]"
date: 2013-04-08
forum: Desktop Environments
---

### Post by Fincer on 2013-04-08
Hey,

today after having run a disk check for my Ubuntu 10.04 LTS installation (Asus 1215N laptop) I encountered a strange bug that not only annoys me but also makes my laptop unusable. You can see the bug in the following video I recorded while ago:

[http://www.youtube.com/watch?v=BbdWJdrXqkc](http://www.youtube.com/watch?v=BbdWJdrXqkc)

I know the bug is related to netbook-launcher. After prompting to terminal and killing process *netbook-launcher* I get no blinking at all. However, the sidebar is not also available.

Before having run the disk check everything worked as charm. I have tried d*pkg-reconfigure *command for all packages related to Xorg and Netbook-launcher + reinstalled all netbook-launcher packages to solve the problem - however, without success.

I doubt this bug is caused by some misconfiguration either in my personal settings of g*conf, xorg *or *netbook-launcher *but I'm unable to specify the source of the bug in more detail. I wish you have some ideas how to approach the problem in more professional way. I'm really stuck with this now and I don't certainly want to install newer Ubuntus in my laptop, so that's not a solution for me. What might cause the strange blinking behavior for the netbook-launcher?

I have bumblebee package installed.

**Edit: As I've studied the problem in more detailed way, the netbook launcher seems not to be the only program messed up -> topic title changed. See below posts for further information.**

---

### Post by Fincer on 2013-04-08
I checked */var/log/messages* on my laptop.

I have multiple messages stating:

```
[   21.262711] netbook-launche[1901]: segfault at 0 ip 0462d535 sp bf9a8848 error 4 in libc-2.11.1.so[45b7000+159000]
[   23.791222] netbook-launche[2004]: segfault at 0 ip 00ce4535 sp bffbdfb8 error 4 in libc-2.11.1.so[c6e000+159000]
```

and so on. My wild guess is that netbook-launcher is trying to restart itself forever but fails time after time. This means that restarting process is looping (and causing the blinking showed in the video) until I decide to kill it.

In addition, my pulseaudio installation was corrupted somehow and there were no sound at all. However, I solved audio problems by deleting .pulse -folder in my home dir and then letting pulseaudio to recreate it.

---

### Post by kostkon on 2013-04-08
Tried purging and reinstalling the netbook-launcher package?

---

### Post by Fincer on 2013-04-08
> **kostkon said:**
> Tried purging and reinstalling the netbook-launcher package?

Thanks for suggestion. Unfortunately purging and reinstalling all packages related to netbook-launcher didn't solve the problem. After reinstallation I tried to launch netbook-launcher via terminal. Same segfault error appeared in logs.

I've discovered that this problem might be more serious than I thought at first. See the following picture:

[[IMG]http://88.192.69.68/ftp/public/other/corrupt1_thumb.png[/IMG]]("http://88.192.69.68/ftp/public/other/corrupt1.png")

I seriously doubt that *gconf* or *nautilus* is messed up as well.

Edit: Already run *dpkg-reconfigure -a* without success.

---

### Post by Fincer on 2013-04-08
Possibly solved. I just rudely deleted corrupted gconf entries in nautilus one by one, shown in the picture above. After having done that I rebooted my laptop and started netbook-launcher manually via terminal. The launcher seems to stay running as it did before the unlucky disk check (mentioned in the opening post).

I mark this thread as solved. I hope the error will not return. That's why I make a *dd image* backup from my laptop SSD, just make sure I can restore the image in a case of failure.

---

### Post by kostkon on 2013-04-11
> **Fincer said:**
> Possibly solved. I just rudely deleted corrupted gconf entries in nautilus one by one, shown in the picture above. After having done that I rebooted my laptop and started netbook-launcher manually via terminal. The launcher seems to stay running as it did before the unlucky disk check (mentioned in the opening post).

I mark this thread as solved. I hope the error will not return. That's why I make a *dd image* backup from my laptop SSD, just make sure I can restore the image in a case of failure.
Good to hear, although as you may already know, support for 10.04 ends in a month (May 9), so eventually you'll have to start thinking about upgrading to 12.04. Your laptop is powerful enough and it should run 12.04 just fine.

I wouldn't recommend you staying with 10.04, since after it becomes EOL, you'll stop getting security updates, even for web facing applications like Firefox and all.

What are your plans?

---

### Post by VeeDubb on 2013-04-11
> **kostkon said:**
> Good to hear, although as you may already know, support for 10.04 ends in a month (May 9), so eventually you'll have to start thinking about upgrading to 12.04. Your laptop is powerful enough and it should run 12.04 just fine.

I wouldn't recommend you staying with 10.04, since after it becomes EOL, you'll stop getting security updates, even for web facing applications like Firefox and all.

What are your plans?

Just to second that, I have a 1201n, which is the immediate predecessor to your 1215n, and has significantly less horsepower, and it is currently running 12.10.  I liked the netbook remix as well when it was still active, but Unity is actually pretty similar to netbook remix.  On my 1201n, I'd say that 12.10 runs at least as well as 10.04, and probably a good bit better.

---

