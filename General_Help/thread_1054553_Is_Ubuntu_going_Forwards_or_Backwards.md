---
title: "Is Ubuntu going Forwards or Backwards?"
date: 2009-01-29
forum: General Help
---

### Post by abyssius on 2009-01-29
Please I hope someone has the patience to bear with this massively long post. I'm writing this in frustration because today's 8.04 Kernel upgrade broke my system by initiating a problem I had already encountered using 8.10, and believed I had resolved by reverting back to 8.04.1.

First, a little history is in order. I used this system with no problems for many months running 8.04.1, 64-bit. I updated to 8.10 via Synaptic update and upon restart the system booted into low graphics mode and my wireless adapter (which previously worked flawlessly) refused to work. 

First, let me discuss the wireless adapter. I had a D-link DWL520e PCI adapter, which I originally got working using the hostap driver and downloaded firmware binaries. After, updating to 8.10, hostap refused to load the firmware files anymore. I won't dwell on this because I finally gave up on the D-link card. It was old and 802.11b, so I purchased a Linksys USB 802.11g adapter and a Linksys WRT54G2 802.11g router. I was impressed that 8.10 immediately supported my adapter. However, this excitement was tempered by the fact that it routinely drops my connection, forcing me to unplug then re-insert the USB cable to re-connect. The relevant messages are, I believe:

> 
[   31.009080] wlan0: disassociating by local choice (reason=3)
[ 9651.464030] wlan0: No ProbeResp from current AP 00:80:c8:2a:a8:ea - assume out of range


I searched for answers to this, found bug reports, but no solution. I figured I'd try the Windows driver via ndiswrapper. However 8.10 informed me I was attempting "bad magic" by trying to use a 32-bit driver with a 64-bit system.

Okay. I installed 8.10 32-bit on a new partition. The same dropped wireless connections occurred using native support. However, I was able to load the windows driver via ndiswrapper. This driver ended my sporadic disconnect problems (using 32-bit, anyway).

The second problem I mentioned upon upgrade to 8.10 was with my graphics card. This I believed would be easier to resolve. I re-loaded the recommended NVIDIA driver. I was impressed that 8.10 recommended the 173.xx.xx or 96.xx.xx drivers off the bat instead of forcing the latest NVIDIA driver on me as was the 8.04 policy. I loaded the driver, got the usual (for me) 640X480 graphics screen. Fixed it by editing xorg.conf. I did this for both the 64-bit and 32-bit 8.10 versions. The graphics card works at the correct resolution with special effects, etc. However, with both versions, I encounter sporadic screen freezes (although sometimes the mouse can still be moved) with no way out except a hard reset. 

Eventually, for troubleshooting purposes, I replaced my FX5200 with an old MX200 that I knew was in good condition. I changed the NVIDIA driver to 96.xx.xx to accommodate the card. I got full graphics capability, but continued to experience random lock-ups. After some more research, I downloaded a new beta version of the NVIDIA 96.xx.xx driver. This didn't correct my freezing problem. Because of this problem, both 8.10 64-bit and 8.10 32-bit was completely unreliable for me.

I added a new hard-drive to my system, installed 8.04.1, the 96.xx.xx driver and the windows wireless driver. Everything was working perfectly with 8.04.1. No screen freezes. Constant wireless connectivity. Everything was cool. I should point out that even though 8.04.1 worked flawlessly, every time I booted either of my 8.10 versions the previously described problems returned.

Anyway, I was content simply using 8.04.1. However, today, after I downloaded the updates which included a kernel update, now I'm getting the sporadic screen freezes with 8.04.1. I wish I could undo the update, but I'm not sure how to do this.

[U]
My system as it is right now[/U]: ASROCK MB, 1 gig DDR400 RAM, AMD Athlon 64 3700, clocked at 2.4 Ghz, NVIDIA MX200 graphics card, 120 gig HDD with 8.04.1 32-bit installed; 80 gig HDD, with dual partitions: one with 8.10 64-bit and another with 8.10 32-bit installed.

I'm not sure what to do next. But, if updates are going to break systems, then I think there may be serious problems with the new Ubuntu kernels - hence the title of this thread.

---

### Post by bumanie on 2009-01-29
I think it is a dubious assumption to think ubuntu is going backwards. The main issue is that there are a multitude of hardware in the market place and a multitude of firmware produced for the hardware. Open source, traditionally get little to no help from manufacturers with trying to make the hardware compatible with linux, thus open source coders have to interface these things themselves. Covering every little idiosyncrasy with everyone's particular computer is almost impossible. For instance, I had a bad time with gutsy, some minor issues with hardy and so far have found intrepid ibex to be the most stable - but that's on my machine, yours is different. On 8.04, one kernel knocked out my sound, a friend had exactly the same components as I, but his components were 10 months younger ie later mobo (although same make/model), possibly later firmware and his sound was never affected. It's hard for open source to cover every single configuration, although they try and thus have a bug report facility via launchpad. You should place a bug report with launchpad and it will be looked at. Launchpad is there to get to the bottom of issues like yours and to improve ubuntu for all.

---

### Post by abyssius on 2009-01-29
> **bumanie said:**
> I think it is a dubious assumption to think ubuntu is going backwards. The main issue is that there are a multitude of hardware in the market place and a multitude of firmware produced for the hardware. Open source, traditionally get little to no help from manufacturers with trying to make the hardware compatible with linux, thus open source coders have to interface these things themselves. Covering every little idiosyncrasy with everyone's particular computer is almost impossible. For instance, I had a bad time with gutsy, some minor issues with hardy and so far have found intrepid ibex to be the most stable - but that's on my machine, yours is different. On 8.04, one kernel knocked out my sound, a friend had exactly the same components as I, but his components were 10 months younger ie later mobo (although same make/model), possibly later firmware and his sound was never affected. It's hard for open source to cover every single configuration, although they try and thus have a bug report facility via launchpad. You should place a bug report with launchpad and it will be looked at. Launchpad is there to get to the bottom of issues like yours and to improve ubuntu for all.

I don't disagree with you. That's why I had no problem buying a new wireless adapter. However, the hardware combination I was using was perfectly stable with 8.04.1 until today's update. I don't support the notion that you have to be prepared to modify your hardware with every release or upgrade. As for launchpad, there are already existing Launchpad reports with the errors I've described with 8.10 - plenty of discussion but no solution I've seen thus far. That's why I reverted from 8.10 back to 8.04.1 in the first place. I went backwards - I didn't expect the 8.04.1 kernel to follow me :)

---

### Post by niteshifter on 2009-01-29
Hi,

> Anyway, I was content simply using 8.04.1. However, today, after I downloaded the updates which included a kernel update, now I'm getting the sporadic screen freezes with 8.04.1. I wish I could undo the update, but I'm not sure how to do this.


Via the grub menu at startup. When the machine boots, press ESC and select the previous kernel. This will let you rollback the kernel temporarily (must be done each boot).

True - sometimes kernel updates break things. They also fix things, eventually. But that comes about more slowly if bug reports aren't filed (hint;)).

If your machine is stable with the previous version and you wish to rollback permanently edit your /boot/grub/menu.lst file and remove or comment out the newer kernel entries. You can also remove the new kernel files from /boot. You'll be nagged by the updater about new kernels, AFIK the only option is to ignore the nag (or turn updates off completely).

Consisder backing up /boot - all of it - first if you'll be deleting things!

---

### Post by jrusso2 on 2009-01-29
> **abyssius said:**
> I don't disagree with you. That's why I had no problem buying a new wireless adapter. However, the hardware combination I was using was perfectly stable with 8.04.1 until today's update. I don't support the notion that you have to be prepared to modify your hardware with every release or upgrade. As for launchpad, there are already existing Launchpad reports with the errors I've described with 8.10 - plenty of discussion but no solution I've seen thus far. That's why I reverted from 8.10 back to 8.04.1 in the first place. I went backwards - I didn't expect the 8.04.1 kernel to follow me :)

You do have to be prepared to fix certain drivers after a kernel update, esp those that are proprietary.  Long time users of Linux know this by now.

I wait to do kernel updates until the drivers are all there.

---

### Post by abyssius on 2009-01-29
> **jrusso2 said:**
> You do have to be prepared to fix certain drivers after a kernel update, esp those that are proprietary.  Long time users of Linux know this by now.

I wait to do kernel updates until the drivers are all there.

This is sage advice. I've been experimenting with Ubuntu for a year after being completely saturated in Windows for many years. In all fairness, I am using a spare computer and leveraging old parts whenever I can. Maybe, I should by a brand new computer and see where that gets me. I was completely confident with Ubuntu until this happened.

---

### Post by abyssius on 2009-01-29
> **niteshifter said:**
> Hi,



Via the grub menu at startup. When the machine boots, press ESC and select the previous kernel. This will let you rollback the kernel temporarily (must be done each boot).

True - sometimes kernel updates break things. They also fix things, eventually. But that comes about more slowly if bug reports aren't filed (hint;)).

If your machine is stable with the previous version and you wish to rollback permanently edit your /boot/grub/menu.lst file and remove or comment out the newer kernel entries. You can also remove the new kernel files from /boot. You'll be nagged by the updater about new kernels, AFIK the only option is to ignore the nag (or turn updates off completely).

Consisder backing up /boot - all of it - first if you'll be deleting things!

Problems similar to what I've described are already registered in Launchpad. Should I post them again? I'm not sure how that facility should be used.

---

### Post by s3kt0r on 2009-01-29
> **niteshifter said:**
> Hi,



Via the grub menu at startup. When the machine boots, press ESC and select the previous kernel. This will let you rollback the kernel temporarily (must be done each boot).

True - sometimes kernel updates break things. They also fix things, eventually. But that comes about more slowly if bug reports aren't filed (hint;)).

If your machine is stable with the previous version and you wish to rollback permanently edit your /boot/grub/menu.lst file and remove or comment out the newer kernel entries. You can also remove the new kernel files from /boot. You'll be nagged by the updater about new kernels, AFIK the only option is to ignore the nag (or turn updates off completely).

Consisder backing up /boot - all of it - first if you'll be deleting things!

@ abyssius, next time do like niteshifter is writing. Even if you do update the kernel, you can always rollback to the previous one. For example, I've compiled latest kernel with latest patch on Intrepid and out the window goes my sound support. Just rolled back to previous version with no patch, all is good.

@ niteshifter, backing up /boot is a nice way to do it, but one could also just backup the kernel images and associated files, rather than the whole dir?

> **abyssius said:**
> This is sage advice. I've been experimenting with Ubuntu for a year after being completely saturated in Windows for many years. In all fairness, I am using a spare computer and leveraging old parts whenever I can. Maybe, I should by a brand new computer and see where that gets me. I was completely confident with Ubuntu until this happened.

Try to look around for hints on which hardware is better supported.

---

### Post by jrusso2 on 2009-01-29
> **abyssius said:**
> This is sage advice. I've been experimenting with Ubuntu for a year after being completely saturated in Windows for many years. In all fairness, I am using a spare computer and leveraging old parts whenever I can. Maybe, I should by a brand new computer and see where that gets me. I was completely confident with Ubuntu until this happened.

Well I have that video card in another computer and it is getting a bit old.

---

### Post by abyssius on 2009-01-29
> **jrusso2 said:**
> Well I have that video card in another computer and it is getting a bit old.

I was originally using a FX5200 when I first encountered the problem. I know this is also old, but cards with the FX5200 chipset are still sold. The MX200 (I assume you mean this card) is certainly old, but it worked fine, even with full effects activated. I'm beginning to think that I'm blaming the kernel update incorrectly. Now, when I think about it, I also saw some nvidia related updates listed also. How do I find out what exactly was included in the update I received today?

---

### Post by Boelcke on 2009-01-29
Good advice about the updates and drivers.  One thought:  Why upgrade?

One of the things I love about this (linux in general, ubuntu in particular) is that it stays stable and operating for a long time.  I have a laptop that I bought new (came with Vista), and immediately installed ubuntu 7.10 on it.  I had some issues with sound, found the fix on here, and it works great.  I've thought about upgrading it, but I haven't found a need.  Why should I?  I might eventually, but I expect it'll involve fixing something.  In the meantime, it works great for what I do on it (email, photo editing, scripting, writing...).

I've also got an old box for the kids, with the original Dapper install.  It still works, I ain't touching it.  I might install a fresh one on there sometime, but I've just had better things to do...

---

### Post by niteshifter on 2009-01-30
Hi s3kt0r,

Yes one can just grab what's needed from /boot. Why I wrote what I did:

I recommended editing menu.lst and deleting old images - two things in two places. Getting all of /boot covers against any oopsies.

There's not usually all that much in /boot, some 10's of MB typically, maybe  a few hundred MB on a kernel-hack's box. Tarballing it off to an external drive or burning to CD shouldn't take more than a couple of minutes. Cheap insurance if you will.

Lastly, I'm a belt & suspenders type when it comes to system maintenance. I like the warm fuzzies one gets from having a nice, safe backup.

---

### Post by Neural oD on 2009-01-30
i agree with Boelcke - why fix what isn't broken - but if u **need** to - be prepared for a bit of tinkering.

---

### Post by LowSky on 2009-01-30
Belt and suspenders is a little bit of everkill...lol

Personally I'm more of a sweatpants kind of guy...j/k   :P

Anyway, to roll back your kernel, you can uninstall the newest kernel from synaptic, and it will update /boot and grub automatically.
As for the graphics, I'm recalling reading something that the FX5200 was a horrible chipset for Linux. Upgrading to a Nvidia 8xxx or 9xxx series is rather cheap and most of those cards work great

---

### Post by druellan on 2009-01-30
The fact is that this is something that Canonical must address sooner or later, at least if they want to keep the idea of a all-users-desktop-linux, because I don't see any warning no notices referring to be careful on the updates: Ubuntu just says "push here to update" and go on. Also, on Hardy being a LTS is supposed to avoid changing things on a radical way.

Anyway, things are breaking up for a good reason: a bunch of new technologies are being pushed up to the kernel thanks to a better involvement of the hardware companies, a very positive thing, but bugfixies must wait until everything is in place.

And a more important fact: the concept of a monolithic kernel is pushed hard and both developers and distros must find new ways to better handle this kind of issues.

---

