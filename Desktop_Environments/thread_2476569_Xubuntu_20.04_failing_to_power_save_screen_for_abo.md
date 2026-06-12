---
title: "Xubuntu 20.04 failing to power save screen for about the past month"
date: 2022-06-29
forum: Desktop Environments
---

### Post by mdlueck on 2022-06-29
Greetings,

I keep up with the regular Xubuntu 20.04 updates.

For perhaps the past month, my system will put on the screen saver as normal, but skips over the next step of putting the screen to sleep. If I IPL the system (reboot) then the screen will go to sleep for a while, but soon back to just screen saver only, no screen sleep mode.

Has anyone else noticed this, and have a resolution for the behavior?

I am thankful,

---

### Post by guiverc on 2022-06-29
G'day

Ubuntu LTS releases have two primary kernel stack choices; GA & HWE (*plus OEM options I'll ignore here*), and you may find using the other kernel stack will help (*plus it's easy*).  If you're **not** using *closed-source kernel modules* (ie. proprietary video drivers), you can also have both kernel stacks installed & select at boot which you'll use thus it's an easy thing to try, back out if unhelpful too  (*both stacks mean you just get updates for both, meaning slightly larger upgrades & kernel footprint on your disk; if you have a small /boot that could be an issue though!*).

For Ubuntu 20.04 LTS the GA kernel stack uses the 5.4 kernel for the life of the product, and with the HWE kernel stack you'll find you're using 5.13 at 20.04.4 (*it'll upgrade to 5.15 with 20.04.5 so check what you have; 20.04.5 is getting close!*). You didn't indicate which you're using.

For more details you can read - [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)  but with Xubuntu (*or any flavor in fact*), installation media dictates the default; for 20.04 & 20.04.1 media the GA kernel is default; however if 20.04.2 or later media is used the default is HWE.

 Xubuntu uses the `ubiquity` installer so it's possible neither is used, but an OEM option if your hardware is detected as benefiting from an OEM kernel at install time, but I've not experienced this with Xubuntu as my hardware doesn't trigger it (*I just know it can occur with Ubuntu Desktop so I've assumed Xubuntu too**; Lubuntu does not offer OEM I do know*).

If you don't want to make changes; I'd likely test using *live* media; I just checked and the [Lubuntu *daily* of *focal*]("https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest") (*what will be 20.04.5 when released*) now comes with 5.15 kernel, *hey it just appeared for Xubuntu too - [https://cdimage.ubuntu.com/xubuntu/focal/daily-live/20220630/focal-desktop-amd64.manifest](https://cdimage.ubuntu.com/xubuntu/focal/daily-live/20220630/focal-desktop-amd64.manifest)*.  The *daily* will allow a fully-upgraded current HWE build to be tested *live*, alas it's more work for a *live* GA system as new ISOs for *focal* come with HWE only now.

I'd firstly look at which kernel stack you're using, switching stacks is an easy option & can help in my experience; if it doesn't; it's also easy to reverse & it's only packages installed that can also be as easily removed (*though more complex if you're using certain closed-source kernel modules/aka drivers where I'd hope for something better*)

FYI: IPL made me smile...  I didn't notice it until I read the "(reboot)" & I wondered why that was included... then the :P so thanks.

---

### Post by mdlueck on 2022-06-30
Greetings guiverc,


> **guiverc said:**
> I'd firstly look at which kernel stack you're using, switching stacks is an easy option & can help in my experience; if it doesn't; it's also easy to reverse & it's only packages installed that can also be as easily removed (*though more complex if you're using certain closed-source kernel modules/aka drivers where I'd hope for something better*)


I use the Nvidia binary drivers.

Currently running on kernel:

```
$ uname -a
Linux jaakob 5.13.0-51-generic #58~20.04.1-Ubuntu SMP Tue Jun 14 11:29:12 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

$ dpkg -l | grep linux-
ii  binutils-x86-64-linux-gnu                     2.34-6ubuntu1.3                                             amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                    4.5ubuntu3.7                                                all          Linux image base package
ii  linux-firmware                                1.187.31                                                    all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                       5.13.0.51.58~20.04.31                                       amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.13.0-51-generic               5.13.0-51.58~20.04.1                                        amd64        Linux kernel headers for version 5.13.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04               5.13.0.51.58~20.04.31                                       amd64        Generic Linux kernel headers
ii  linux-hwe-5.13-headers-5.13.0-51              5.13.0-51.58~20.04.1                                        all          Header files related to Linux kernel version 5.13.0
ii  linux-image-5.13.0-51-generic                 5.13.0-51.58~20.04.1                                        amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                 5.13.0.51.58~20.04.31                                       amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          5.4.0-121.137                                               amd64        Linux Kernel Headers for development
ii  linux-modules-5.13.0-51-generic               5.13.0-51.58~20.04.1                                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.13.0-51-generic         5.13.0-51.58~20.04.1                                        amd64        Linux kernel extra modules for version 5.13.0 on 64 bit x86 SMP
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
```

> **guiverc said:**
> FYI: IPL made me smile...  I didn't notice it until I read the "(reboot)" & I wondered why that was included... then the :P so thanks.

haha.... Initial Process Load.... mainframe terminology. And I commonly refer to storage as DASD also. ;-)

> **guiverc said:**
>  however if 20.04.2 or later media is used the default is HWE.

Most odd situation here... I could not get Xubuntu 20.04 to install on my system with MSI MPG Z490 motherboard until the release of 20.04.2. It refused to boot from DASD.

My prior system from 2009 built around an Intel DG33BUC motherboard works just fine on the initial 20.04 release, and.... drum roll.... refuses to work when booting from a 20.04.2 DVD. eyeyeyeyeyeyeyeyeye........

I am thankful,

---

### Post by mdlueck on 2022-07-13
Any suggestions why screen power save is failing on my Xubuntu 20.04.2 based system?

I am thankful,

---

### Post by guiverc on 2022-07-13
I didn't respond further as I couldn't think of anything meaningful to respond.

*I open threads (here & elsewhere) & they sit open awaiting me to have a chance to respond (with something meaningful/useful ideally) but I couldn't offer much then, or now.  I reboot this machine once a ~fortnight; so unanswered threads get forgotten as they'll close during my reboot.  Your prior thread was closed day-before-last when I rebooted.*

DASD - I haven't thought about that for *years!*, but yeah I hated using `dd` to write ISOs to thumb-drive as to me for a *loooong* time DD was *data definition/description* used in JCL *many many times a day*. I think DASD was something I spoke/said far more than typed, so that wasn't as difficult to *kick*.

I have limited experience with NVidia drivers; most of my hardware uses AMD or intel, and the couple of HP boxes where I have NVidia I don't do much with ([I]one is used purely for QA-test installs & some testing but rarely video/GPU related, the other had a QA-test failure last week & sits waiting for me to find time to precisely work out how I can resolve before 20.04.5 & 22.04.1's release; I'm convinced the issue isn't installer related for 22.04.1 (next release date) so its not [currently] high priority for me; for support purposes I did some weird things to the install I'd never do myself, and I believe they're now biting me).


[/I]I would hope you have more luck with the current 5.15 kernel, as it's the GA kernel stack from Ubuntu 22.04 LTS thus 3rd parties put more effort into supporting it than non-LTS stacks like 5.13; but yeah I'm *hoping* and my knowledge in this area is too limited (*5.15 has started rolling out the last ~week for focal or 20.04*).  I'd also likely explore each other GA/HWE stack, but again your NVidia makes than much harder (*and  specific to the actual driver you use with your hardware*).  Normally I'd likely (*since you have one box that likes the GA stack & another that likes HWE*) create a persistent *live* system on thumb-drive on the box where it's easier, then test that on the other box (*and vice-versa*), but I have no experience with Nvidia, and if they both use different kernel modules (Nvidia *drivers*) again added complexity I've not dealt with. I'd likely also look up bug reports from others experiencing it, but I've not had time sorry.

Sorry i can't offer anything help.

---

### Post by mdlueck on 2022-07-15
> **guiverc said:**
> I didn't respond further as I couldn't think of anything meaningful to respond.


haha guiverc, I did not mean that just you are the only other one reading this forum!


> **guiverc said:**
>  (*5.15 has started rolling out the last ~week for focal or 20.04*). 


And I seem to have picked it up already...

```
$ uname -a
Linux jaakob 5.15.0-41-generic #44~20.04.1-Ubuntu SMP Fri Jun 24 13:27:29 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

Power save for the screen still not activating.... screen saver keeps on running.

I am thankful,

---

### Post by mdlueck on 2022-07-16
Greetings,

I have logged the bug / defect here:

"Failing to power save the screen"
[https://bugs.launchpad.net/bugs/1981897](https://bugs.launchpad.net/bugs/1981897)

I am thankful,

---

