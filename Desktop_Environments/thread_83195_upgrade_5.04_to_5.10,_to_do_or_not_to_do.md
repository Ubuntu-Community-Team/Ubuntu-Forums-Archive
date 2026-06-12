---
title: "upgrade 5.04 to 5.10, to do or not to do?"
date: 2005-10-28
forum: Desktop Environments
---

### Post by oasiscity on 2005-10-28
Hi, guys,

I am considering to have an upgrade, but a little bit wondering whether new things/improvements are worthing the upgrade. 
Meanwhile I heard that Chinese support in Breezy is worse than in hoary.(I am not sure if it is true).

so,anybody can convince me? what's the biggest reasons for the upgrade.
I read the featuer list in release notes, but I am not sure if those really matter in my daily use. 

thanks.

---

### Post by RikoW on 2005-10-28
Hi,

I actually upgrade from Hoary to Breezy about a week ago. The upgrade went suprisingly smooth with just using an Install-CD and apt-get. However, the daily work feeling didn't really change very much. I use it mainly as a regular office desktop however on a laptop with docking station. For those applications like Email (Thunderbird), calendaring (evolution with exchange connector) and open office, there is no real change. Openoffice comes a prerelease of 2.0, so I uninstalled and installed the official release version of 2.0 (maybe it's already in the repos'?).

The only noticable difference (except a bit a smoothing in various applications here and there) is the availability of suspend to disk in addition to hibernate with the new kernel. Of course, that matters only for laptop users.

I would suggest, you get the live CD of Breezy and see for yourself if it feels worth upgrading.

My main reason for upgrade was that like to be as up-to-date with all my software are possible and still have a stable distro to run.

Don't know if that helps any!

           Cheers,

                  Riko

EDIT: I guess, actually hibernate is suspend-to-disk and suspend is suspend-to-ram ....

---

### Post by FidelTheInfidel on 2006-01-02
For me the Evolution (with Exchange plugin) stopped working in 5.10, even if I reinstall from scratch. Still running fine on my other 5.04 box.

---

### Post by ysse on 2006-01-02
Hi,

After the last kernel updates in 5.04 I started getting unclean filesystems after shutting down. So, I decided to take the plunge.

First, I upgraded as RikoW did, with an install CD and apt-get. Then I decided to play around a bit with my partitions and did a fresh install. Besides, I had fiddled around a great deal with the sound bits, and I wanted a clean slate.

I can say that my experience with 5.10 is really good. Sound now works for more than one app at a time. Evolution with Exchange Connector is more stable - in 5.04 it terminated after startup almost half of the time. Suspend to disk works with ATI 3d accel enabled - never did in 5.04.

Java integration is much better, and with update-alternatives, switching between different JRE:s is painless.

I'm a laptop user and a Java programmer, so the last two issues are the most important to me. Eclipse is available as a package too, but that may have been there in 5.04 as well, don't know, because I had installed Eclipse manually in Hoary.

Just my experience, but I would recommend upgrading.

cheers
/Anders

---

