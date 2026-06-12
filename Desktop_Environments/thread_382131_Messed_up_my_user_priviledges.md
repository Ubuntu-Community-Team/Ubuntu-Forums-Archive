---
title: "Messed up my user priviledges"
date: 2007-03-11
forum: Desktop Environments
---

### Post by aorthr33 on 2007-03-11
Little history:  I just installed Ubuntu 6.10, and after doing the 1st set of major updates (including a kernel update), my sound quit working.  I googled around and found someone with a similar problem, that he/she had resolved by issuing:

```
sudo usermod -G audio trey
```

I tried this and still no sound, so I decided to go look for updated drivers for my Audigy card, but when I tried to launch Synaptic (or any other root/sudo needed app), I get the popup asking for my password, bu then I get the following error in a separate pop up:

> Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

Can anyone offer any advice on how to resolve my permissions problem.  I can't do anything administrative at this point.

Even when I use sudo from the command line, I get no response....just kicked to the next line and and a cursor.

Thanks

Trey.:confused:

---

### Post by dhughes on 2007-03-11
I had a similar problem the other day using Xubuntu on an old laptop, I couldn't access Synaptic because it wouldn't accept my password. 

 I rebooted and it went away, not the best solution since I have no idea why it happened but for me it's an old laptop and it doesn't matter to me if it fails.

---

### Post by aorthr33 on 2007-03-11
I tried the reboot option and things went from bad to worse.  I still have the same problem with sudo on the command line (e.g. - sudo appears to be ignored), but now the apps that would require sudo (synaptic, Add/Remove,  et al) are even missing from the menus on my top panel.

Anyone else have any ideas?  I've just built this installation, and I don't want to have to do a full re-install, or image restoration, because I *REALLY* want to learn how to fix these kinds of things

---

### Post by aorthr33 on 2007-03-12
Fianlly figured it out.  I had to boot into rescue mode (option #2 in the Grub menu), and then re-add myself to the 'admin' group.


```
root@Goliath# usermod -a -G admin trey
```



:lolflag:

---

