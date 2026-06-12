---
title: "KDE won't start after trying to enable hibernate / suspend with uswsusp"
date: 2007-06-04
forum: Desktop Environments
---

### Post by mrming on 2007-06-04
Hi everyone,

I just properly killed my Kubuntu install for the first time and am unable to start KDE from the login prompt. I was trying to enable suspend / hibernate via uswsusp as detailed in this article: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

My troubles began when after installing uswsusp via adept. The installer flagged up the fact that I didn't have a swap partition, so I removed the package via apt-get remove, used mkswap and swapon to set my /dev/sda2 partition as the swap, and installed uswsusp again - this time the install went smoothly.

I edited /etc/fstab and placed the required line to mount /dev/sda2 as swap, including the UUID I got from mkswap. I then used sudo s2disk to try to hibernate the machine.

The machine tried to hibernate, hung at a flashing cursor, and I powered it off and tried to start it again. It got as far as the Kubuntu progress bar and then dropped to a single flashing cursor. I hit ctrl-alt-f1 to display the error message (can't remember what this was off hand) and hit return to continue booting.

The system booted and KDE ran OK, and removing uswsusp via adept solved the above error message upon rebooting. Unfortunately that's where my problems really started. I'm now unable to launch kde but just keep getting kicked back to the login box.

Can anyone give me any guidance as to how to begin diagnosing and fixing the problem. I'm reluctant to reinstall because I've spents months getting the install exactly how I like it, and I've even survived an upgrade from Edgy to Feisty.

Any help would be greatly appreciated. I have years of experience with both Windows and Mac OS but am a relative newbie to Linux / Ubuntu. :(

---

### Post by mrming on 2007-06-04
*bump*

Could anyone give me a quick rundown on how to diagnose a problem with a non-launching gui?

Cheers :)

---

### Post by mrming on 2007-06-05
OK, just in case this happens to anyone else:

First - check your disk space - my Kubuntu parition was 100% full.

Second - somehow an invalid line had made it's way into my /etc/fstab - the only cause I can think of is mkswap.

Third - boot in recovery mode and actually pay attention to anything that has "fail" next to it instead of ignoring it and going off on a wild goose chase for hours like I did.

Always learning... :)

---

