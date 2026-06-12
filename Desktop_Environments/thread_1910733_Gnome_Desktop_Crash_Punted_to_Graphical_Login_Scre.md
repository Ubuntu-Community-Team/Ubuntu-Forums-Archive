---
title: "Gnome Desktop Crash: Punted to Graphical Login Screen Every Time"
date: 2012-01-17
forum: Desktop Environments
---

### Post by stanley drew on 2012-01-17
Hello hello,

I apologize in advance if the terms I use aren't precise. I'm not really an expert in Linux desktop environments. But I appear to have a real problem that a couple of hours of searching Google and experimenting haven't been able to fix.

Some background: I'm running Ubuntu 11.04 x64 on a macbook pro and haven't had any graphical display issue since I started using Ubuntu on the MBP in July of 2010.

But yesterday morning when I tried to power up my machine I got to the graphical login prompt, entered my password as usual, and then briefly saw the mouse pointer on the standard purple gradient background before the screen went blank. The nVidia logo then appeared and filled the screen I'm using proprietary nVidia drivers and this usually happens at boot time before the login prompt appears. After that, the login prompt reappeared.

So I tried again, and again, but the same cycle kept occurring.

So I tried to log into 'Ubuntu (Safe Mode)'. Same thing.

So I tried to log into the 'Recovery Console'. Same thing.

I rebooted into recovery mode and looked at dmesg and other logs but didn't know what to look for.

I rebooted and dropped to a shell where I was able to log in. I removed the nVidia driver with apt-get remove nvidia-current. I moved xorg.conf to xorg.conf.bak in hopes that it would be rebuilt correctly. I then reinstalled the nvidia-current driver after a reboot. Same thing.

So now I don't know exactly what to do. I don't remember installing any updates that might have caused this.

Does anyone have any ideas about what to look for in a log file or how to better diagnose this problem?

Thanks very much in advance for any help.

Cheers,
amb

---

