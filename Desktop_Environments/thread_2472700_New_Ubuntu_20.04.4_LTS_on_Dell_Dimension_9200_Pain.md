---
title: "New Ubuntu 20.04.4 LTS on Dell Dimension 9200 Painfully Slow Firebird &amp; FireFox Start"
date: 2022-03-09
forum: Desktop Environments
---

### Post by 58-fleetside on 2022-03-09
New Ubuntu user.  Lots of experience with Windows.  Minimal Linux/Unix background.  
I just did a clean install (Previously Win7) on a Dell Dimension 9200. Now ONLY Ubuntu, not a dual boot.
Intel Core 2 CPU 6300 @ 1.86Ghz
4G Memory
500G HD
Nvidia video (OS says NV84)

It seems to start OK.  File system seems OK, and I can see my Synology NAS.

Firefox starts painfully slow (5 minutes) but then sort of runs.  Youtube sort of works with sound and video, but hangs.

Thunderbird starts painfully slow and hangs.  Config for my iCloud account seemed to work.  I can see incoming email, but so far trying to Write a new email hangs everything for a long time, with just a mouse working.

Where do I start?  Is hardware to old?  Don't need super fast machine, but stable and functional would be nice.

John.

---

### Post by TheFu on 2022-03-09
If you installed the default Ubuntu which comes with Gnome3, you picked the heaviest version.  There are other Ubuntu flavors which are much lighter and make less demands.  Also, really old nvidia GPUs will only work with the F/LOSS drivers, since nvidia drops support for older cards after about every 10 yrs.

So, first thing is to switch away from Gnome3 to something else.  With an old GPU, the best solution is probably Lubuntu or Xubuntu. While it is possible to do the swap without reinstalling, due to your lack of experience, I think a fresh install of either versions of those to L/Xubuntu flavors will be much easier.  They both come with lighter versions of applications, though you can always install any application you like. The light versions are almost always sufficient for normal users.  I'd strongly push you to Lubuntu.

There are a number of reasons that your system is slow. Lubuntu will be the lightest choice.

As long as the GPU is old and doesn't support h.265/h.264 video decoding in hardware, you'll always see lagging video performance.  Not much you can do about that which would make sense.  Buying a cheap, newer, GPU really isn't possible. There is a shortage of GPUs and pricing for all of them are far out of whack.  I upgraded a 2010-ish system last fall and to avoid dealing with hoping to find a cheap GPU, I ended up spending $70 more to get an AMD Ryzen with an on-board GPU which is roughly equivalent to an nVidia GT 1040 (is that even a model? It is faster than the 1030, but not as capable as the 1050).  I have a GT 1030 bought 3+ yrs ago for $70 in another box, but today that same GPU is $140+. Just checked.

You'd be really amazed at what you can build reusing existing parts for $200.  Any Core i3 or Ryzen + MB + RAM that have iGPUs will easily beat your current box. You can reuse the PSU, case, HDD, keyboard, mouse, monitor ... 

You know, upgrading the HDD to an SSD would not be a waste of money. Get a $40 500G SATA-SSD and convert the 500G HDD into your external backup storage. The SSD will be 10x faster. They come in SATA 2.5inch format which can be mounted inside pretty much any older desktop or laptop using just 2-4 screws and the existing power and sata cables.

BTW, that CPU is pretty slow.  [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core2+Duo+E6300+%40+1.86GHz&id=908](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core2+Duo+E6300+%40+1.86GHz&id=908) Just 580 passmarks.  Cheap, cheap, current generation Core i3 CPUs are 3500 and higher passmarks.  Many chromebooks would be faster.  

If you lived near me, I'd happily sell for $20 a P45 MB + G3258 CPU + 8G DDR3 RAM for a 2000+ passmark computer just to get it out of the house.  In 2015 it was $126 for the parts. Most people would be better off going newer for $120+ than taking my trash.

---

### Post by grahammechanical on 2022-03-10
How much of its own memory does the Nvidia video adapter have? That could be the choke point. I have a Core 2 Duo system with an Intel 2.4GHz CPU. Your CPU is slower. I have a Nvidia GT 210 with 1GB memory. It runs Ubuntu 20.04 sufficiently.

As recommended by thefu an install of Lubuntu or Xubuntu would be a better choice for this machine.

Regards

---

### Post by naxal on 2022-03-11
Hello,

I too use Ubuntu on Older Hardware. Infact, one of my old desktop is very close to your configuration with Core 2 Quad Q6600. I found the bottleneck is with the HDD, modern OS, even standard Ubuntu performs really snappy when paired with a SSD. If possible, find a cheap low budget SSD and get the OS installed on that. In my case, I used a really old simple 64GB SSD for the above mentioned PC and difference in system snappiness is huge.

Thanks.

---

### Post by TheFu on 2022-03-11
FYI, a Core 2 Quad Q6600 is about 3x faster than the OPs CPU, so the comparison isn't really relevant. 1700 vs 580 passmarks.

+1 on switching to an SSD.  

64G SSDs are great and will easily hold the modern 20.04 OS plus all the documents that any single person would create. But the pricing seems to be much too high when compared to a quality 500G SSD or even cheap 500G SSD.  Basically, the vendors have all zoned in to the $40+ place as where it doesn't make sense to go any cheaper, so a 64G SSD will be $40 while a not-so-great-brand 500G SSD will be $50.  I've owned a number of small-by-today's-standards SSDs and for my needs, 64G was fine, plenty of room, provided I kept media (videos and music) on external flash drives.
On my 500G SSDs, I setup the layout as:
```
NAME                         SIZE TYPE FSTYPE   LABEL      MOUNTPOINT
sdz                  465G part LVM2_mem
  &#9500;&#9472;vg00-swap                4.1G lvm  swap             
  &#9500;&#9472;vg00-root                 35G lvm  ext4     root       /root
  &#9500;&#9472;vg00-var                  35G lvm  ext4     var        /var
  &#9492;&#9472;vg00-home                 25G lvm  ext4     home       /home
```
which is for a system with over 30TB connected.  As you can see, I really only expect to use about 50G of storage for the most important areas.  Ignore the 35G for /var. That's for a few play virtual machines and linux containers. Normal desktop users won't use those at all. Still, of the 465G (after format), less than 100G of space is being allocated for the OS. I expect this storage to be used for the next 10 yrs, BTW. 
Don't worry about the LVM stuff. Each of those vg00-<name> can be considered a LABEL (like a UUID) and LVM2 is just really flexible for modifying storage over years, at the price of complexity. Most end users don't use LVM, which is fine. Look at those like they are partitions. I'm not showing the EFI and /boot areas. Those are 50M and 600M, respectively.

---

### Post by DuckHook on 2022-03-11
Welcome to the forums 58-fleetside.

This one is a tough call. I'm an old HW hound. I used to love working with ancient, almost decrepit HW and bringing them back from the dead. Unfortunately, Ubuntu has moved further and further away from being able to do that old magic. These days, even Lubuntu is no longer very lean. They've moved to QT (it had to happen, so no blame there) and Canonical is dropping 32-bit support for everything but some very limited use cases, so I've had to look elsewhere for old HW support.

To be completely frank, none of the 'buntu flavours may be the right fit for you. I have a machine of about the same specs that I recently retired. At the end, I wasn't running 'buntu, but Bodhi Linux instead: [https://www.bodhilinux.com/](https://www.bodhilinux.com/)

The reason I retired the machine is because even such a super lightweight distro was a trying experience compared to the quickness that I'm used to in my main box. I'm getting impatient in my old age.

---

### Post by guiverc on 2022-03-11
One of my most used boxes in QA-testing is 

- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)

though I mostly use it for testing *flavors* like Lubuntu.. and whilst I may semi-regularly install Ubuntu to it, I generally only QA-testing the install & doing very simply tasks such as starting `firefox` only once to view a web page. I do use it often for support purposes (*exploring what users have done & testing prior to responding to them*) but again GNOME is a little heavy for it and wouldn't be my choice.

Key comment I'd make is to match your wanted apps with the desktop. ie. Lubuntu uses the LXQt desktop, so it's libraries are Qt5, meaning it'll be most efficient if you're using Qt5 apps with it; but far less so if you're trying to use GTK3 apps. Xubuntu uses the Xfce desktop which is GTK3 based (*GTK3 is much heavier than Qt5*) however if using GTK3 apps the desktop & your apps can share resources so it's extra weight (when contrasted with LXQt) is not significant.

I've not experienced your issue with firefox though at all. I'd likely explore logs and look for clues; open a terminal & explore resources (`htop` etc.. it's not installed by default with Ubuntu but as I'm often using Lubuntu where it is default it's my general goto). Do you have swap configured appropriately (`firefox` *& such apps are horrifically slow if swap isn't setup appropriately..*)

My dc7700 had Xubuntu (2x 20.04.4), Ubuntu-MATE (20.04.4), Lubuntu (jammy & 20.04.4) & another I now forget installed on it yesterday and I'd not have expected your described behavior on any. Those have since been wiped (*i had too many*) & it's got a *fresh* install of Ubuntu-MATE *jammy*; with `firefox` loading in less than 20 secs on a fresh boot.; however NOTE that may not be a comparable time to a 20.04.4 system as *jammy* will use the *snap* packaged version of `firefox` which is slower to start  (*20.04.4 would be the ~same OR faster, but not slower* I'd expect)... Currently *jammy* installs like my one have both versions installed ([*a known bug* *that is being worked on*]("https://bugs.launchpad.net/ubuntu/+source/lubuntu-default-settings/+bug/1963672")) and I didn't look to see which one starts. Whilst the *snap* version is slower on first run, it's equal once going & on subsequent starts. Either way it less than 20 secs for my hp dc7700 running Ubuntu-MATE *jammy* and i'd expect the ~same on other Ubuntu *flavors* too (*main Ubuntu is only a touch slower than the slowest flavor in my experience*).

At first read - I'd check *swap* is configured correctly and appropriately, and then if no issues are found there - I'd be exploring your hardware for issues. My own dc7700 uses an old 80GB hdd that isn't super-healthy (*doesn't look great looking at it's SMART output*) but as I'm getting no errors (*just mild drop in performance*) I'm ignoring it... Your system may need a replacement drive being in way worse shape than my own; have you checked?  My current drive cost me $3 from a recycler so they're not expensive to replace (*just the hassle of going out to purchase them*).

FYI:  *jammy* is the codename of what will become Ubuntu 22.04 LTS on release.

---

### Post by DuckHook on 2022-03-12
> **guiverc said:**
> …`firefox` loading in less than 20 secs on a fresh boot.; however NOTE that may not be a comparable time to a 20.04.4 system as *jammy* will use the *snap* packaged version of `firefox` which is slower to start…
20 seconds to first load of FF is… well… enough lag to run for a coffee.

Another instance of my growing curmudgeonly impatience. :redface:

---

### Post by 58-fleetside on 2022-03-14
Thanks to all for your responses.  Really appreciated.

I'm struggling with the steep learning curve of all the terms :(

For now I've given up on the old Dell Dimension.  I'm now spending some time resurrecting an old Lenovo (AMD® Athlon(tm) dual core processor 5000b × 2; AMD® Rs780) that my  late father had an old Fedora OS installed on. For now I've moved the HDD from the Dell to the Lenovo, so I wouldn't trash the Fedora.  I did a clean Ubuntu install and the Lenovo runs fairly well.  At least simple apps (FireFox, Thunderbird, Rhythmbox) start OK and are functional.  I think I'll check Amazon.CA for a small SSD.

Not sure if I should ask additional questions on this thread, or start new threads for specific issues.

---

### Post by ActionParsnip on 2022-03-14
If its installed by Snap then the first run will always be slower. After that it'll open much quicker

---

### Post by DuckHook on 2022-03-14
> **58-fleetside said:**
> …I'm struggling with the steep learning curve of all the terms :(
Please ask for explanations about the jargon and don't be intimidated by it. It's an old chronic malady that we geeks fall into: using initialisms, acronyms and geek-speak because we forget how disconcerting these can be for those starting out.
> Not sure if I should ask additional questions on this thread, or start new threads for specific issues.
Yes, please start new threads for specific issues. That's the way the forums are designed to run.

---

### Post by TheFu on 2022-03-14
> **ActionParsnip said:**
> If its installed by Snap then the first run will always be slower. After that it'll open much quicker

Quicker than the first time. Probably not quicker than a normal package. Also, it will use more RAM, sometimes 600MB more, if it is the first program to use a GUI toolkit that hasn't already been loaded. OTOH, if the correct version of the GUI toolkit snap package is already loaded, then no more added RAM will be used. It works like a normal shared library.

---

