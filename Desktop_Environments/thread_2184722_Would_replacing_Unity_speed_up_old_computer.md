---
title: "Would replacing Unity speed up old computer?"
date: 2013-10-30
forum: Desktop Environments
---

### Post by glennc on 2013-10-30
Hello to all,
   I have an old HP Pavillion, AMD sempron, might be 2GB of memory. It was given to me and I loaded Ubuntu 12.04 LTS. Set it up wireless to my network and gave to my wife for browsing. I found it pretty slow but it is what it is. Lately I have wanted to use the computer with some resource intensive programs and I thought I'd try a different distro.
Well found my way to Puppy Precise. Got it running and hooked up wireless. Of course I found out that it does not have level of user accounts and security I wanted. 
  So after playing (I am not very familiar with linux, I tried Mint 13 - didn't work, 15 without Cinnamon - worked but slow and couldn't connect wireless, Kubuntu - couldn't connect.
I used separate partitions and Grub. Well I finally went back to puppy to look something up (after trying many things....). Now it wouldn't connect. My level of knowledge thought that if I loaded Windows XP I could get the Broadcom B43 drivers. No luck.
  I am currently loading yesterdays downloaded Ubuntu 12.04. I will endeavor to  solve the wireless connection issue. While it is installing, I vaguely remember that maybe, there was a way to drop the unity and go back to Gnome 2 interface. Wanted like originally to have more resources available and make it speedier!
Quite possibly totally wrong...
Appreciate any assistance in either of the described problems!
glennc7000

---

### Post by ibjsb4 on 2013-10-30
You can try running the old desktop (called Classic and/or Fallback) instead of Unity.

```
sudo apt-get install gnome-session-fallback
```

And chose your desktop at boot (login) by clicking on the icon.

If that doesn't help you may want to try Xubuntu or Lubuntu, both use less resources than Ubuntu.

Could also be that you need to install a different video driver.

Also Unity has a 2d mode that can be chosen at boot.  Have you tried it?

---

### Post by glennc on 2013-10-30
Hello ibjsb4,
  Thanks for responding! No I never have, never saw an option and since Ubuntu worked well for the old purpose, I never thought to look or ask. Just finished installing 12.04...... If I can get the wireless working again, I will give those a shot. As I mentioned, I thought I've read something about "fallback". Then all went south with the wlan0. Grrrrrrrr!
;) Thanks again
glennc

---

### Post by grahammechanical on 2013-10-30
First of all your issue with the wireless driver must be solved first. And wireless has been working so logically it should be fixable. If special precautions are needed in one distribution then those same precautions are likely to be needed in other distributions.

Second, you should be installing Xubuntu. But remember, if you need to do certain things in Ubuntu LTS to get wireless working, then you will need to do those same things in Xubuntu. As good as Linux is it cannot resurrect the dead. That machine just might not be up to the tasks that you want to use it for.

[http://xubuntu.org/](http://xubuntu.org/)

Regards.

---

### Post by glennc on 2013-10-30
> **grahammechanical said:**
> First of all your issue with the wireless driver must be solved first. And wireless has been working so logically it should be fixable. If special precautions are needed in one distribution then those same precautions are likely to be needed in other distributions.

Second, you should be installing Xubuntu. But remember, if you need to do certain things in Ubuntu LTS to get wireless working, then you will need to do those same things in Xubuntu. As good as Linux is it cannot resurrect the dead. That machine just might not be up to the tasks that you want to use it for.

[http://xubuntu.org/](http://xubuntu.org/)

Regards.

Howdy grhammechanical,
  Xubuntu, it is speedier? I will certainly take a look at it, thank you. Regarding the wireless it is a know issue and I've been unsuccessfully trying to follow the threads and advice, quite honestly not understanding what I am doing.... This old computer has Broadcom B43 Wireless Drivers, I think I somehow trashed it and the install disk won't install the Broadcom STA drivers, like mentioned in the thread. I am going back to fumbling around with it.
Appreciate your time!
glennc

---

### Post by mörgæs on 2013-10-30
Please run

```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

