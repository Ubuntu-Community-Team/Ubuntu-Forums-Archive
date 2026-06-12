---
title: "Having a strange hanging problem...."
date: 2009-04-29
forum: General Help
---

### Post by klapauciuspdx on 2009-04-29
Running Jaunty...

Running ASUS M3N78-VM motherboard, 2 GB RAM, onboard Nvidia 8200 or 8300 that uses part of the system RAM.  Not running 64-bit Ubuntu, just the standard.

Anyway, I did a fresh install, didn't have much in the way of problems, everything seemed to be working properly.  A day or two later, I realized that I hadn't installed the Nvidia restricted driver, so I could use Compiz.  I proceeded to do so, and that went well, I was able to get the system tweaked the way I wanted it....

Here's where it gets strange.... Thunderbird is my preferred mail client.  I was able to configure it and pull the data down from my Gmail imap account with no problems.  However.... when I click 'Write' to compose a new mail in Thunderbird.... it locks/hangs.  I'm running a dual core AMD CPU, and I can get to the machine via SSH from another machine on the network.  I run top/htop, and I see one core pegged high, between 99-104 percent CPU, associated with the following process:


/usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7


I tried other suggestions with regards to uninstalling tracker/trackerd, killing update-notifier, etc.  Nothing seems to work... I can move the pointer in the screen that I'm in, but I can't switch to different windows, nor can I click on anything.  System is still available from the command line from another machine on the network.

Anyone able to reproduce this, or perhaps give me an idea why it might be doing this?  In the meantime, my workaround is using Evolution, which doesn't seem to cause the same problems when composing.

Thanks for your time... 

Scott

---

### Post by Bindsa on 2009-04-29
Tried using another distro of Thunderbird?

---

### Post by klapauciuspdx on 2009-04-29
I've not tried that, but I was doing some other tweaking within the Compiz panel, when it locked up again.  Don't recall exactly what setting I was altering, but it did that again... 

I had some thoughts as to whether it was the RAM I was using, but switched it out with some matched RAM from another machine, and still had the same issue.  

Scott

---

