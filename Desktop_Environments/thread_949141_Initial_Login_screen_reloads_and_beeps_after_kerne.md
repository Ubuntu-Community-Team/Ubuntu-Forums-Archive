---
title: "Initial Login screen reloads and beeps after kernel upgrade"
date: 2008-10-15
forum: Desktop Environments
---

### Post by cjchand on 2008-10-15
Hello all,

I assume I'm perma-hosed at this point, but wanted to float out a post to see if this could be salvaged before I resigned myself to failure. 

My Ubuntu journey was going well until I mistakenly selected "Install All Updates," which updated the kernel on my 8.04 install - something I was explicitly looking to avoid. 

After that, I can see that the nvidia driver fails to load during bootup. When X loads, the login screen flashes for a brief second, I get a system beep, then the screen flashes, it beeps... Lather, rinse, repeat.

I can drop to a tty and stop X. Restarting X results in more of the same. 

Restarting the previous kernel also resulted in the same behavior.

Thinking I was hosed at this point, I figured I would try an upgrade to Ibex in the vein hopes that it might rectify things, but no joy.

Based on posts here and elsewhere, here's a list of what I've tried, to no avail (going off of memory - I'm sure there's more fiddling around I did than this):
[LIST=1]
[*]Manually forcing vesa and nv in xorg.conf
[*]Attempted to recompile the Nvidia drivers, but the compile dies at 43%. I did an apt-get install for kernel-headers and build-essential
[*]Ran reconfig on X (sudo dpkg-reconfigure -phigh xserver-xorg) about 20 times :)
[*]Tried purging all the nvidia packages and redownloading them
[*]Tried envy in CLI mode
[/LIST]

In case it matters, the vid card is a GeForce Ti4600 and the logs in /var/log show that it's trying to load the 96.43.XX (07, I believe - would have to look at the logs again) driver. 

I'm not sure what logs/conf files would be helpful, but I can boot the live CD and pull whatever we need. 

Any help would be greatly appreciated. I forgot how much I hate XP now that I've had to revert back :(

Cheers,
Chris

---

### Post by cjchand on 2008-10-18
Nevermind, I opted to resize my 8.04-based partition and made that my /home partition, then did a fresh install of 8.10 in the newly created root partition. 

I did confirm that my upgrade from 8.04 to 8.10 failed due to this bug: [https://bugs.launchpad.net/ubuntu/intrepid/+source/rarian/+bug/256131](https://bugs.launchpad.net/ubuntu/intrepid/+source/rarian/+bug/256131). The fix appears to be in the latest builds, so anyone looking to upgrade (as opposed to fresh install) from a prior release will want to get the latest release.

Cheers,
CJC

---

