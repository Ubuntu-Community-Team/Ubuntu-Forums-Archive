---
title: "GRUB displays two versions of Ubuntu?!"
date: 2010-07-20
forum: Desktop Environments
---

### Post by beaubuntoo on 2010-07-20
Hey all, this is my first post in this forum and am a first-time Ubuntu user:
I just reconfigured the grub bootloader to choose Windows 7 first and upon restarting (the second time after realising that the memory tests are included in the list ;)) I found that there were two versions of linux listed:

Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)

After I installed Ubuntu it gave a massive list of updates so I went ahead with it, I'm guessing it's because of that? My question is: It can't be a separate installation of linux, so do I need to remove these 2 "old entries" from the menu?

Thanks

---

### Post by nmaster on 2010-07-20
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

in the future, use this tool before starting a new thread: [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by mcduck on 2010-07-20
When Linux kernel updates are installed they don't replace the currently running kernel, but are installed alongside the old version instead. This allows you to test the new kernel and make sure everything is working as it should, while at the same time being able to boot back into the old kernel if you have problems with the new one.

So indeed it isn't a separate Ubuntu install, you just have two versions of the kernel installed currently. Once you are sure the new one is working fine you can simply uninstall the old kernel packages with Synaptic (or apt-get of course) and it will be automatically removed from the Grub menu.

Edit: Of course you don't have to remove the old kernel, actually quite many people prefer keeping at least one older version always available, just in case. One kernel version and it's related files takes couple of hundred megabytes of disk space so it's not much compared to hard drive sizes these days, but you probably don't want to have tens of old kernels wasting your drive space so you'll have to remove some of them over the time. Personally, I just uninstall the old kernel after couple of days running the new version, and in case the new kernel would somehow break after  that (I can't really see how that would happen) I'd just boot with the Ubuntu CD and fix the problem from there.

---

### Post by KdotJ on 2010-07-20
> **neal.m.master said:**
> [www.googlubuntu.com](www.googlubuntu.com)

I never knew that lol, thanks for the link

---

### Post by nmaster on 2010-07-21
> **KdotJ said:**
> I never knew that lol, thanks for the link
there are actually quite a few ubuntu custom google search tools.  there's also this one although i'm not sure if it actually yields different results.
[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by madison12 on 2010-07-23
nice valuable information !!!!! its really useful !!!!


[ Seo India ]("http://www.seoindia.mobi")

---

### Post by beaubuntoo on 2010-07-24
Thanks for the all the help, guys! That wiki, and "ubuntu search engine" is really helpful! ;)
Am a newbie to all this so just finding my feet! :)

---

