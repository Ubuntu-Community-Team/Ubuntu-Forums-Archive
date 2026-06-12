---
title: "Fails to boot gives Busy Box instead"
date: 2009-05-19
forum: Desktop Environments
---

### Post by darkorical on 2009-05-19
I have a computer that worked great for 3 months running 8.04 (and was probably never shutdown in that time) 

someone tried to reboot it the other day and it came up that it couldn't find its hard drive most of the time but they said that occasionally they would try to boot it and it would bring something that said 
as they described it "
The word grub with two arrowy thingies on either side and we could type there" Gotta love those technical descriptions from end users don't you.

Im assuming they mean something like 

<grub>


So I brought it in to look at it. When I turned it on if found the hard drive and started up just fine and showed the ubuntu logo and the scrolling bar for a min or so then it simply goes to 

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 

So I rebooted and when it offered the grub menu I entered and selected recovery mode and it gives me 
```

    Check root= bootarg cat /proc/cmdline
    or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk//by-uuid/fee79d8c-8a74-440e-b15c-f1de354f1e08 does not exist. Dropping to a shell

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 

```

any help or suggestions would be appreciated

---

### Post by balboost on 2009-05-20
hello,

i don't have the response but i am very interested in this topic, as i encounter the same problem when i want to launch a live persistent session.

@darkorical : did you try to boot with a live cd to check your /etc/fstab ?

i don't know either what a busybox is.

---

### Post by darkorical on 2009-06-01
well I took a week vacation and havent been back to the computer since but Im back now anyone have any other suggestions?

---

### Post by darkorical on 2009-06-02
still no help on this?

---

