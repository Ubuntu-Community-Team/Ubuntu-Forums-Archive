---
title: "Intel graphics performance fix on Jaunty"
date: 2009-04-24
forum: General Help
---

### Post by monkeyKata on 2009-04-24
So I updated my system to Jaunty yesterday.  I have an integrated Intel i945 or something-or-another video card in my laptop.  Everything was fine except my video performance was pretty choppy.  I could play videos and flash without any problems, but just about any Compiz effects were running noticeably slower than before.  I had noticed this 'regression' on Intel video moving from Hardy to Intrepid, and yesterday moving to Jaunty it was even worse.  Even the World of Goo demo, which was perfectly playable in Intrepid, had become too choppy to play.  And I didn't want to just disable Compiz effects because I find some of them quite useful (magnify, zoom, scale...) and others like wobbly windows add some life to the desktop that I like, even if they're not too useful.

I'll share the fix I found.  Try this if you have Intel video i810, i815, i830, i845, i855, i865, i915, i945 or i965 series.  

First in Synaptic I removed xserver-xorg-video-i740 because I'm not using that model and I read the suggestion elsewhere that the driver may have been in conflict with xserver-xorg-video-intel, which is the driver that corresponds with the above-mentioned video chipsets.  This had no effect, however, and probably isn't necessary to do.

Next I reverted to an older Intel graphics driver.  Follow the directions here:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Aside from adding those two lines to the Third-Party Software tab of your Software Sources, you'll need to add the correct GPG key under the Authentication tab.  Directions here:
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

Here's the launchpad site for this repository:
[https://launchpad.net/~siretart/+archive/ppa](https://launchpad.net/~siretart/+archive/ppa)

And the key itself just a few clicks away:
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79)

What you do is open Text Editor and copy/paste that whole thing starting with "-----BEGIN PGP PUBLIC KEY BLOCK-----" and ending with "-----END PGP PUBLIC KEY BLOCK-----"

Save the text file, then under Software Sources/Authentication click on Import Key File... and load this file you saved.

Then just do those two commands in the terminal as noted on the "Reverting the Jaunty Xorg intel driver to 2.4" and restart.  If something doesn't work, this page also describes how to undo these changes.

For me this did the trick.  Compiz effects are running smoother than in Intrepid, a stark difference from the default Intel driver included in Jaunty.

Hope this helps someone.

---

### Post by twinklellon on 2009-04-24
The best way I found that can really solve this problem is to upgrade the kernel.

It is easy and harmless:

HOWTO upgrade the kernel to 2.6.30rc3: (download the corresponding deb packages and install them in order.)
- 32bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)

- 64bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)

After that, reboot Ubuntu, and enter the system with 2.6.30 kernel. 
Some article might ask you to use UXA mode, but no need to follow that. UXA is extremely unstable. Just keep the EXA mode, and that means no changes on xorg.conf.

---

### Post by monkeyKata on 2009-04-24
Hey thanks,

So you had issues with Intel graphics as well?  Is this updated kernal stable?  And would I just run each of those deb packages in order, reboot, and I'm set?

I guess before hand I'd have to revert to the default Intel driver that comes with Jaunty.

You haven't had any issues with this.... it's been stable and quick?

---

### Post by twinklellon on 2009-04-24
> **monkeyKata said:**
> Hey thanks,

So you had issues with Intel graphics as well?  Is this updated kernal stable?  And would I just run each of those deb packages in order, reboot, and I'm set?

I guess before hand I'd have to revert to the default Intel driver that comes with Jaunty.

You haven't had any issues with this.... it's been stable and quick?

Yes, simply install those deb packages, and you're all set.
But, maybe there are still some issues with the kernel. Ubuntu did freeze for a unknown reason.
Syslog got this message:
[drm:i915_gem_execbuffer] *ERROR* Failed to copy relocations back out: -1070762178

---

### Post by nnarayann on 2009-04-24
Hi!!. I think I have a similar problem with my Intel 855:

[[IMG]http://img134.imageshack.us/img134/6567/pantallazoelt.th.png[/IMG]](http://img134.imageshack.us/my.php?image=pantallazoelt.png)

Updating the kernel could solve it? I have a lot of problems with scrolling on firefox too, on maximizing/minimizing windows and above all the things shows in the capture above.

Does this may be due to something else?

Thanks in advance,

nnarayann.

PS. Sorry for my english ;)

**Edit:** I've upgraded the kernel to 2.6.30rc3 and it keeps the same. Any idea? I'll try the monkeyKata's solution too.

---

### Post by deathspal on 2009-04-24
Nix.....   rc3 did not fix my lockups (i915 chipset)

---

### Post by deathspal on 2009-04-24
Reverting to the 2.4 Intel drivers has cured all my Ills. no more lockups with all my effects turned back on including burn-up

@monkeyKata  Thanks!

---

### Post by mikeglover on 2009-04-25
> **twinklellon said:**
> The best way I found that can really solve this problem is to upgrade the kernel.

It is easy and harmless:

HOWTO upgrade the kernel to 2.6.30rc3: (download the corresponding deb packages and install them in order.)
- 32bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb")
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb")
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb")

- 64bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb")
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb")
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb")

After that, reboot Ubuntu, and enter the system with 2.6.30 kernel. 
Some article might ask you to use UXA mode, but no need to follow that. UXA is extremely unstable. Just keep the EXA mode, and that means no changes on xorg.conf.

After updating to Jaunty, watching BBC iPlayer in fullscreen was very choppy and unwatchable.
I have an Intel GMA 915.
Installing the 2.6.30 kernel has fixed this issue for me. :)

---

### Post by jordan420 on 2009-04-26
hey guys i upgraded the kernel and the intel-xorg package to the newest and on the up side the visuals are working alot better, seriously i've been running kubuntu on the new kernel with UXA enabled and its never been better on linux. but on the downside my BCM4328 wireless has stopped working. i read something about a possible bug with the broadcom drivers.  any news on this?

---

### Post by IainPurdie on 2009-04-26
Any idea when the 2.6.30RC kernel will be released "properly" via Update Manager? If it's short-term I can live with the minor hiccups I've got until then.

I'm using i900 which isn't listed on the original post, but prepared to have a dig and see what happens if required!

[update] I stepped through the first post to change my drivers, and it's made absolutely no different at all. Still getting little bits of corruption in the same places as before (opening WINE Config, Display in Preferences and flickering when using the controls in full-screen MPlayer - none of which were a problem in Intrepid).

---

### Post by _tom_ on 2009-04-26
x4500: Performance is much better with 2.6.30 rc2, but less good with 2.6.30 rc3. 
Does anybody else see this regression from rc2 to rc3?

---

### Post by r1ch on 2009-04-26
I'm using an i965 system, the old 2.4 drivers did nothing for me, however upgrading to the rc kernel solved the stuttering flash video on firefox. Despite this I still can't enable desktop effects.

---

### Post by r1ch on 2009-04-26
Solution to my aforementioned desktop effects issue is in this post...

[http://ubuntuforums.org/showthread.php?t=1136256&highlight=desktop+effects]("http://ubuntuforums.org/showthread.php?t=1136256&highlight=desktop+effects")

sourced from this blog...
[http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

In combination with latest kernel, everything seems to be slowly getting back to normal

---

### Post by higashi on 2009-04-26
thanks soo machhh

---

### Post by nfox on 2009-04-26
i definately don't want to jinx anything but the 30RC seems like a godsend in terms of performance. seems to be running like ye olde times with Hardy. Intrepid, with my experience seemed horribly slow compared to older versions and Jaunty seemed like a nice try but no go.

With freezes and hangs averaging 10-20 a day while I'm at work, I was seriously thinking of downgrading but with the new unreleased debs you posted, everything seems more sane. The jury is still out though about crashes and hard freezes.

I will go and post this at Launchpad but there are a lot of open bug posts there concerning freezes with Intel and if this can be the fix then it will help upstream. Please help me get the word out.

---

### Post by djuliette on 2009-04-26
Intel 4500 did show improvement with 30rc3, but still not as good as it was under 8.10. (though I didn't try kernel 30rc2, some have gotten better results with that)

I've tried everything I could find listed in the forums, various xorg.conf changes, rolling back the intel driver to ver 2.4 (no effect reverted back to 2.6) and installing the 30rc3 kernel is the only thing that showed any improvement.
Still looking for the way to get video running as it was under 8.10.

---

### Post by RikBlankestijn on 2009-04-28
I used to use i810 driver. This page describes the solution that worked for me: [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by chezzo on 2009-04-28
thank you so much! reverting to the old driver worked wonders :)
compiz, awn and boxee all work fine again!

(i'm using an intel core solo T1350 with 945 integrated graphics on a dell inspiron 640m)

---

### Post by Tuxoid on 2009-04-28
> **twinklellon said:**
> The best way I found that can really solve this problem is to upgrade the kernel.

It is easy and harmless:

HOWTO upgrade the kernel to 2.6.30rc3: (download the corresponding deb packages and install them in order.)
- 32bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)

- 64bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)

After that, reboot Ubuntu, and enter the system with 2.6.30 kernel. 
Some article might ask you to use UXA mode, but no need to follow that. UXA is extremely unstable. Just keep the EXA mode, and that means no changes on xorg.conf.

Thank you very much. My wine games are now running optimally.

much appreciated :popcorn:

---

### Post by deathspal on 2009-04-28
after upgrading the kernel to rc3 the load and shutdown splash screens no longer display. I only get text mode. anyone know how to re-enable them....

my grub line looks correct and includes splash. if I load the older kernel the splash screens work

```
title		Ubuntu 9.04, kernel 2.6.30-020630rc3-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.30-020630rc3-generic root=UUID=8d0463e2-def6-4e08-a26a-47c1f2b0b9bd ro quiet splash 
initrd		/boot/initrd.img-2.6.30-020630rc3-generic
quiet
```

---

### Post by jordan420 on 2009-04-29
helllo. i can confirm that the new kernel does indeed improve the graphics situation. but i cant figure out how to get my broadcom wireless working under that kernel. and suggestions? under the regular kernel i have to install the restricted modules package to enable it.

---

### Post by markovuc on 2009-05-01
> **jordan420 said:**
> helllo. i can confirm that the new kernel does indeed improve the graphics situation. but i cant figure out how to get my broadcom wireless working under that kernel. and suggestions? under the regular kernel i have to install the restricted modules package to enable it.

You will have to compile the broadcom driver by yourself. Search for the procedure (unless somebody already did it for this version of kernel, and created the .deb package).

Every time you install the new (unofficial) kernel, you will have to take care about the drivers not included in kernel (in your case, broadcom wireless).

---

### Post by jordan420 on 2009-05-01
i've tried to compile the driver myself in the new kernel, but i keep getting make errors. ```
make[1]: *** [/home/j/src/linux-restricted-modules-2.6.28/ubuntu-restricted/broadcom/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/j/src/linux-restricted-modules-2.6.28/ubuntu-restricted/broadcom] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.30-020630rc3-generic'
``` any idea what i might be doing wrong? ive tried the source from the broadcom site and from the restricted-modules package

---

### Post by IainPurdie on 2009-05-01
Anyone any idea when this kernel will move from Release Candidate to actual general release? My graphics performance is *lousy* since the Jaunty upgrade but I also have a Broadcom and I've utterly no clue (and in honesty no inclination) to go tinkering with kernels by myself.

---

### Post by jordan420 on 2009-05-01
there are quite a few solutions for improving graphics performance in jaunty. try [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html]("http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html")

---

### Post by zevans on 2009-05-01
There's corruption bugs, freeze bugs, and performance issues, and there seem to be different sets of these for at least 945 and 965, so that's at least 6 bugs right there, and a strong suspicion of multiple freeze bugs.

> **IainPurdie said:**
> 

[update] I stepped through the first post to change my drivers, and it's made absolutely no different at all. Still getting little bits of corruption in the same places as before (opening WINE Config, Display in Preferences and flickering when using the controls in full-screen MPlayer - none of which were a problem in Intrepid).

Iain - the phrase "Intel graphics" has become a bit of a melting pot for several different bugs which need different troubleshooting approaches.

In your case you get the same problem across all driver versions you tried, and (presumably) you'd immediately be able to tell if a trial fix had worked - could be worth filing a bug the official way. [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

If you've got a repeatable corruption bug, then obviously that's bad for eye candy but it's good, because it's repeatable and perhaps easier to get a handle on.

Meanwhile - what's an i900, can't figure out what Intel's "offical" name for that is... [Wikipedia page on Intel chipsets]("http://en.wikipedia.org/wiki/Intel_GMA").

---

### Post by zevans on 2009-05-01
For the i965 users here - that seems to be the vast majority of compiz related complaints - A FIX IS UNDER BUILD AND WILL SHORTLY BE RELEASED TO JAUNTY-PROPOSED.

See [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for documentation how to enable and use -proposed.

So anyone hacking on workarounds and bizarre driver versions - could you try this instead please and confirm it fixes the freezes for you? 

(It won't fix the MTRR performance issue if you have that - separate bug - I'm off to find out the latest on those bug reports...)

---

### Post by PhantoMEngineeR on 2009-05-01
> **twinklellon said:**
> The best way I found that can really solve this problem is to upgrade the kernel.

It is easy and harmless:

HOWTO upgrade the kernel to 2.6.30rc3: (download the corresponding deb packages and install them in order.)
- 32bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)

- 64bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)

After that, reboot Ubuntu, and enter the system with 2.6.30 kernel. 
Some article might ask you to use UXA mode, but no need to follow that. UXA is extremely unstable. Just keep the EXA mode, and that means no changes on xorg.conf.

Hey, guys! I've had trouble with the graphics performance of my laptop after upgrade from Intrepid to Jaunty. I'm using Compaq Presario V5000. This tut did the trick for me. My graphics performance is now 100% the way it was. Thanks dude.

---

### Post by colo505 on 2009-05-03
> **twinklellon said:**
> The best way I found that can really solve this problem is to upgrade the kernel.

It is easy and harmless:

HOWTO upgrade the kernel to 2.6.30rc3: (download the corresponding deb packages and install them in order.)
- 32bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)

- 64bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb)
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_amd64.deb)

After that, reboot Ubuntu, and enter the system with 2.6.30 kernel. 
Some article might ask you to use UXA mode, but no need to follow that. UXA is extremely unstable. Just keep the EXA mode, and that means no changes on xorg.conf.

How about the linux-restricted-modules package for this kernel? Is it not required? If yes, where does one find it?

Thanks

---

### Post by jordan420 on 2009-05-03
it is required if you want to keep your broadcom wireless or any other hardware that runs with proprietary drivers working. im trying to find a solution but im not having much luck. i cant seem to get the broadcom driver to compile manually.

---

### Post by densou on 2009-05-04
I already sent bad words torwards Canonical due to not include .29 Kernel on Jaunty but I realized lately it was up to that broadcom stuff and its issues with newest kernels. 

Compiling (from scratch) seems not enough according to this [thread]("thread"), a patch is required :(

~off-topic ended~

regarding Intel crap, I hope my whole xorg.conf could helpful somehow:

```
Section "Module"
	Load 	"ddc"
	Load 	"dri"
	Load 	"glx"
	Load	"GLcore"
	Load	"v4l"
EndSection

Section "Device"
	Identifier 	"Configured Video Device"
	Driver 		"intel"
	Option		"AccelMethod"	"UXA"
	Option          "XvMC"  "true"
#	Option		"EXAOptimizeMigration"		"true"
#	Option		"MigrationHeuristic"		"greedy"
	VideoRam	261376
EndSection

Section "Screen"
        Identifier 	"Default Screen"
	Monitor		"Generic Monitor"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "DRI"
	Mode 	0666
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Extensions"
	Option 		"Composite" 		"true"
EndSection
```

specs: Jaunty default Kernel, GMA950/i945gc, Latest stable Intel drivers from Ubuntu-X-Swat PPA, TFT Display - compiz OFF, metacity ON

note: I also updated gnome-player to 0.9.5 version (avaiable on .deb - not through Synaptic :( ), this is the best setting so far on this PC thus I'll continue to find more ways to improve performances (how? Testing more stuff as possible, of course)

---

### Post by IainPurdie on 2009-05-04
zevans - I'd have replied sooner but I only just got an email notification of a response on this thread...

> **zevans said:**
> In your case you get the same problem across all driver versions you tried, and (presumably) you'd immediately be able to tell if a trial fix had worked - could be worth filing a bug the official way. [https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

Makes sense. I'll get into it. I noticed the same corruption is occurring when I load Picasa as well. It's like a flickering mess, but vanishes as soon as the application loads so it's not a show-stopper... but it does point at something being wrong.

My guess is that it's because the graphics card is "shared memory" as typical in laptops. As the driver we have at the moment is... well... crap, it's somehow confusing the memory being used for graphics and that being used for general use. Thus overwriting one when it should be safely fenced off.

Or something. I'm no expert :)

> **zevans said:**
> Meanwhile - what's an i900, can't figure out what Intel's "offical" name for that is... [Wikipedia page on Intel chipsets]("http://en.wikipedia.org/wiki/Intel_GMA").

I'll have to dig further. I looked on the Acer site for the specs for my laptop (TravelMate 2410) and the model it gives on there is "Intel i900". Maybe they used different cards on different machines in the run so they're generalising.

UPDATE: Just checked another website and it states I have a 910GML (which uses the 900i architecture - thanks for being specific, Acer).

---

### Post by zevans on 2009-05-08
> **IainPurdie said:**
> 
My guess is that it's because the graphics card is "shared memory" as typical in laptops. As the driver we have at the moment is... well... crap, it's somehow confusing the memory being used for graphics and that being used for general use. Thus overwriting one when it should be safely fenced off.


I think you're right... you have to map your icon or whatever to a different piece of memory that the video card can get at, and then the video card itself has to map that into the specific region that's currently being displayed on the screen. 

I think MigrationHeuristic Greedy controls how and when that's done, and other tweaks also affect the order of events. Hence, for me in UXA mode sometimes the area of memory is mapped to the actual screen before the application has filled it with the intended content, and I see garbage which then sorts itself out when the app gets around to putting the right stuff into that "bucket."

Hope you're getting somewhere now...

---

### Post by IainPurdie on 2009-05-08
> **zevans said:**
> Hope you're getting somewhere now...

Sadly, no. Just living with things until the relevant kernel is finally compiled and released into the wild!

---

### Post by b@sh_n3rd on 2009-05-09
> **twinklellon said:**
> The best way I found that can really solve this problem is to upgrade the kernel.

It is easy and harmless:

HOWTO upgrade the kernel to 2.6.30rc3: (download the corresponding deb packages and install them in order.)
- 32bit -
Kernel Header:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3_2.6.30-020630rc3_all.deb")
Kernel Header Generic:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-headers-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb")
Kernel Header Image:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb")

... ... ...

After that, reboot Ubuntu, and enter the system with 2.6.30 kernel. 
Some article might ask you to use UXA mode, but no need to follow that. UXA is extremely unstable. Just keep the EXA mode, and that means no changes on xorg.conf.

Hey dude, when I try linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb, it gives this;

```
(Reading database ... 123579 files and directories currently installed.)
Preparing to replace linux-image-2.6.30-020630rc3-generic 2.6.30-020630rc3 (using linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.30-020630rc3-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.30-020630rc3-generic
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.30-020630rc3-generic (2.6.30-020630rc3) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-020630rc3-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.30-020630rc3-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.30-020630rc3-generic (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-020630rc3-generic
```The above is the second time I tried...:(...please help...the same thing happened last night when trying a different fix and it broke my system..
PS: If this doesn't work...Is there a way of undoing the installation of the first two packages?? OR, is there a way of booting into the old kernel via the boot menu? Thanks...

**EDIT:** Hey, I tried rc4 too but same result :(...

---

### Post by mac79 on 2009-05-09
> **b@sh_n3rd said:**
> Hey dude, when I try linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb, it gives this;

```
(Reading database ... 123579 files and directories currently installed.)
Preparing to replace linux-image-2.6.30-020630rc3-generic 2.6.30-020630rc3 (using linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.30-020630rc3-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.30-020630rc3-generic
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.30-020630rc3-generic (2.6.30-020630rc3) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.30-020630rc3-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.30-020630rc3-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.30-020630rc3-generic (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.30-020630rc3-generic
```The above is the second time I tried...:(...please help...the same thing happened last night when trying a different fix and it broke my system..
PS: If this doesn't work...Is there a way of undoing the installation of the first two packages?? OR, is there a way of booting into the old kernel via the boot menu? Thanks...

**EDIT:** Hey, I tried rc4 too but same result :(...
hi m8
I'm not Linux expert but I noticed 
**gzip: stdout: No space left on device**

Looks like You need to buy another hard drive :-) or perform small cleaning 

cheers
mac

---

### Post by b@sh_n3rd on 2009-05-15
> **mac79 said:**
> hi m8
I'm not Linux expert but I noticed 
**gzip: stdout: No space left on device**

Looks like You need to buy another hard drive :-) or perform small cleaning 

cheers
mac

Hi, I found the bug. I've partitioned a seperate /boot partition with only 32MiB coz I had no idea about kernel images goin over there :D. That's the partitioning system I used in Gentoo see? :D. Anyways, It's workin cool now...Thanks...Sorry for the late reply though..

---

### Post by uniqueseason on 2009-05-15
I so tired about ubuntu and decide i never used ubuntu. They are slow my system and more complex.. I know very well their performance is so poor.

Thanks

---

### Post by b@sh_n3rd on 2009-05-15
> **uniqueseason said:**
> I so tired about ubuntu and decide i never used ubuntu. They are slow my system and more complex.. I know very well their performance is so poor.

Thanks

By saying, "I simply give up Ubuntu", you admit that you're a looser when it comes to Ubuntu...In fact, Ubuntu is the best and fastest release I've ever used...and I'm STUCK to it. To be precise, Jaunty Jackelope brought a whole level of "coolness" to my "most-powerful" desktop PC...If you just say Ubuntu sucks and stuff before TRYING, then you are just a bad looser...No offense...

---

### Post by Kareeser on 2009-05-15
Downloaded and installed the 2.6.30 rc5 kernel. Problem solved, great work!

Can't wait to see it included by default in Karmic. Jaunty's been nothing but fantastic except when it came to Intel graphics. Better late than never!!

---

### Post by IainPurdie on 2009-05-15
I tried the RC kernel as a test and it failed miserably - loads of errors on boot. Strangely, my wifi still worked when I was under the impression that it wouldn't (Broadcom).

I stepped back, then managed to find some (effectively Beta) drivers on launchpad. Look for "ubuntu-x-swat". Added their repository to my software sources, did an update... and performance is back!

I still have some minor graphic niggles, but on the whole it's much improved.

The only issue I had was that I had to disable ubuntu-x-swat in my sources afterwards so that I didn't get the next update they launched. This one works just fine, thank you! No crashes as yet.

---

### Post by colo505 on 2009-06-12
What about VMWare workstation? Will it work with the new kernel?

---

### Post by drdreau on 2009-09-10
Updating the Kernel improved performance i have an intel 915, but it's still choppier then when I used to run windows.

---

