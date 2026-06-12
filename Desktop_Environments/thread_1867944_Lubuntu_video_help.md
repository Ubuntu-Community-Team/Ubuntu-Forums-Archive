---
title: "Lubuntu video help"
date: 2011-10-23
forum: Desktop Environments
---

### Post by KBD47 on 2011-10-23
I like Lubuntu 11.04 and keep it on a usb as a portable system. With 11.10 I had the same problem with all the buntus, it broke my video. Everything else worked fine, but after trying several things my video remained slow and choppy. But perfect with 11.04
  KBD47

---

### Post by amjjawad on 2011-10-23
> **KBD47 said:**
> I like Lubuntu 11.04 and keep it on a usb as a portable system. With 11.10 I had the same problem with all the buntus, it broke my video. Everything else worked fine, but after trying several things my video remained slow and choppy. But perfect with 11.04
  KBD47

What is your Video Card?

---

### Post by KBD47 on 2011-10-23
What do I run in the terminal to find that? I'm sure I've seen it but I forget.
  I tried the flash-aid and other suggestions. It was suggested to me that my card might have been blacklisted.
KBD47

---

### Post by amjjawad on 2011-10-23
> **KBD47 said:**
> What do I run in the terminal to find that? I'm sure I've seen it but I forget.
  I tried the flash-aid and other suggestions. It was suggested to me that my card might have been blacklisted.
KBD47

```
sudo lshw -C display
```

---

### Post by KBD47 on 2011-10-23
> **amjjawad said:**
> ```
sudo lshw -C display
```

This the output:
*-display:0             
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:58180000-581fffff ioport:60c0(size=8) memory:40000000-4fffffff memory:58000000-580fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:58100000-5817ffff

---

### Post by amjjawad on 2011-10-23
> **KBD47 said:**
> This the output:
*-display:0             
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:58180000-581fffff ioport:60c0(size=8) memory:40000000-4fffffff memory:58000000-580fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:58100000-5817ffff

Mine is:

```
*-display               
       description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: [COLOR=Red]driver=i915[/COLOR] latency=0
       resources: irq:16 memory:e0200000-e027ffff ioport:b000(size=8) memory:d0000000-dfffffff memory:e0280000-e02bffff


```

But, why do you have two display devices?

---

### Post by nothingspecial on 2011-10-23
Issue moved to it's own thread.

---

### Post by amjjawad on 2011-10-23
> **nothingspecial said:**
> Issue moved to it's own thread.

Thanks, much better ;)

---

### Post by nothingspecial on 2011-10-23
> **amjjawad said:**
> Thanks, much better ;)

No problem :)

---

### Post by KBD47 on 2011-10-23
> **amjjawad said:**
> Thanks, much better ;)

Yes, thanks!

Re:video not sure why it would list 2 devices. It is a netbook Acer Aspire One D255E and as I mentioned, video works perfectly on the 11.04 buntus, but is slow and choppy on the 11.10 buntus. I installed flash-aid on firefox and tried several things but nothing helped. My concern is that I would like to use the LTS release next spring but if Ubuntu has done something to blacklist my video or the kernal has changed something I will be stuck at 11.04 on this netbook.
KBD47

---

### Post by KBD47 on 2011-10-23
Forgot to add that I tried Fuduntu with the newest kernal and video was much better, so I suspect it is something that changed from 11.04 to the 11.10 version.
Thanks!
KBD47

---

### Post by KBD47 on 2011-10-23
Also found this:
[http://www.bryceharrington.org/Arsenal/Reports/ubuntu-x-swat/symptoms_intel.html](http://www.bryceharrington.org/Arsenal/Reports/ubuntu-x-swat/symptoms_intel.html)

lots of bugs with Oneiric.

---

### Post by amjjawad on 2011-10-24
I need to do some search and get back to you.
If 11.04 was working better for you, why not install it? I'm still using Lubuntu 11.04 because I have all what I need. I don't need to upgrade or install the new one :)

Will try to get back to you ASAP :)

---

### Post by KBD47 on 2011-10-24
I'm using Xubuntu 11.04 now, and I'm fine with it. I have Lubuntu 11.04 on a live usb setup as a backup OS and just something to use when I want something different and light.
  11.10 definitely does not play well with my video card. I'm hoping by 12.04 they will have things worked out so it is working again.
Thanks for helping!
KBD47

---

### Post by amjjawad on 2011-10-24
> **KBD47 said:**
> I'm using Xubuntu 11.04 now, and I'm fine with it. I have Lubuntu 11.04 on a live usb setup as a backup OS and just something to use when I want something different and light.
  11.10 definitely does not play well with my video card. I'm hoping by 12.04 they will have things worked out so it is working again.
Thanks for helping!
KBD47

Yes, use whatever works for you and cause less headache. However, it's also good to learn/understand what is going on with you :)

---

### Post by amjjawad on 2011-10-24
> **KBD47 said:**
> My concern is that I would like to use the LTS release next spring but if Ubuntu has done something to blacklist my video or the kernal has changed something I will be stuck at 11.04 on this netbook.

Unfortunately, Lubuntu 12.04 will not be LTS, only Ubuntu 12.04 will be. Hope that will be changed but so far, everything as it's.

---

### Post by amjjawad on 2011-10-24
Are these specifications of your machine?
[http://www.bestnetbooksreview.com/acer-aspire-one-d255e-netbook-with-atom-dual-core-n550.html](http://www.bestnetbooksreview.com/acer-aspire-one-d255e-netbook-with-atom-dual-core-n550.html)

---

### Post by KBD47 on 2011-10-24
Thanks again!
 I do hope by next spring Lubuntu will decide to be an lts release.
 Yes, those are the specs of my computer. It runs well on the 11.04 buntus, especially Xubuntu and Lubuntu. I did add the Jupiter applet which helps the battery and keeps it running a bit cooler.
  Thanks again for your help!
  KBD47

---

### Post by amjjawad on 2011-10-25
> **KBD47 said:**
> 
 I do hope by next spring Lubuntu will decide to be an lts release.

I do hope that too.

 > Yes, those are the specs of my computer. It runs well on the 11.04 buntus, especially Xubuntu and Lubuntu. 

Perhaps it's a Kernel or Drivers issues.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+install+Intel+Graphics+Media+Accelerator+3150+driver&as_qdr=all&sa=Google+Search&lang=en#1048](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+install+Intel+Graphics+Media+Accelerator+3150+driver&as_qdr=all&sa=Google+Search&lang=en#1048)

I'll keep looking for something similar to your case.

I was just wondering what is really wrong? could you please explain in details?

I don't have much problems with my Video since day 1 with Linux but recently, I noticed there is a game on Facebook (Ninja Saga) which is DEAD SLOW on 11.04 but VERY Normal on Win7. I haven't checked 10.04 because it's on one of my HDDs and it's not connected.
Other than that, everything seems OK. I use VLC and it plays videos well. Same with YouTube.
What about you?

  > Thanks again for your help!
  KBD47
You most welcome but I haven't done much  :)

---

### Post by KBD47 on 2011-10-25
My problem is with playing video 0n 11.10 the picture is slow and choppy and out of sync with audio. Whether it is embedded video on facebook, youtube, discovery channel, wherever the video is bad on 11.10 but perfect on 11.04 on 11.04 it is like watching a movie on TV everything in sync like it should be. Using same flash plug in, newest is 11 I think, on both systems but 11.10 is horrible.

---

### Post by amjjawad on 2011-10-25
> **KBD47 said:**
> My problem is with playing video 0n 11.10 the picture is slow and choppy and out of sync with audio. Whether it is embedded video on facebook, youtube, discovery channel, wherever the video is bad on 11.10 but perfect on 11.04 on 11.04 it is like watching a movie on TV everything in sync like it should be. Using same flash plug in, newest is 11 I think, on both systems but 11.10 is horrible.

OK, that explains a lot, thank you :)

Have you tried to run Lubuntu 11.10 from the Live-CD or Live-USB before installing it? if yes, did you face the same problem?

---

### Post by KBD47 on 2011-10-25
Yes, I tried Lubuntu 11.10 from live usb, and also tried LXDE desktop from Ubuntu 11.10, both had same bad video.
Thanks.
KBD47

---

### Post by amjjawad on 2011-10-25
> **KBD47 said:**
> Yes, I tried Lubuntu 11.10 from live usb, and also tried LXDE desktop from Ubuntu 11.10, both had same bad video.
Thanks.
KBD47

I found this link: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

Check it out, it might fix your issue :)
I didn't know that Intel GMA 3150 is such a pain in the neck. I found many threads about it.

---

### Post by KBD47 on 2011-10-26
Yeah, the info on that page is pretty badly outdated. They only have the d255 not d255e and it only refers to Lucid. Evidently they brought some newer drivers in for the wireless and other things since then because everything, wireless etc., worked out of the box with Natty. They've changed something in either the kernal or Ubuntu itself to break my video in 11.10 I just hope they have it fixed by 12.04 If not I'll just stick with Natty until the repositories are closed and move to something else. I don't know why they would drop things in the kernal, my guess is something they changed for gnome 3 in 11.10 is what is causing my video problems, but it is all above my pay grade :-)
Thanks again.
KBD47

---

### Post by KBD47 on 2011-10-31
amjjawad if you are still monitoring this thread, my youtube video playback in 11.10 has been saved by using this:
[http://www.youtube.com/html5](http://www.youtube.com/html5)
  Now the videos come through good in Lubuntu 11.10 :-) I use the Chromium browser to watch them.
KBD47

---

### Post by amjjawad on 2011-10-31
> **KBD47 said:**
> amjjawad if you are still monitoring this thread, my youtube video playback in 11.10 has been saved by using this:
[http://www.youtube.com/html5](http://www.youtube.com/html5)
  Now the videos come through good in Lubuntu 11.10 :-) I use the Chromium browser to watch them.
KBD47

Hi,
Yes, I'm subscribed to this thread but honestly, I had to go back to post #1 to remember the issue :P sorry but I've been through too many posts, threads, guides, wiki pages, etc etc  ... u know :)

WOW, great :D
I've read it some where here on Ubuntu Forum that HTML5 is much better than Flash but never searched for any information regarding that. I don't have time :/

---

### Post by KBD47 on 2011-10-31
> **amjjawad said:**
> Hi,
Yes, I'm subscribed to this thread but honestly, I had to go back to post #1 to remember the issue :P sorry but I've been through too many posts, threads, guides, wiki pages, etc etc  ... u know :)

WOW, great :D
I've read it some where here on Ubuntu Forum that HTML5 is much better than Flash but never searched for any information regarding that. I don't have time :/

Yes the html5 is working good, and Lubuntu 11.10 had already given me better wireless than 11.04 so I'm a happy camper with Lubuntu 11.10 now :-)
KBD47

---

### Post by amjjawad on 2011-10-31
> **KBD47 said:**
> Yes the html5 is working good, and Lubuntu 11.10 had already given me better wireless than 11.04 so I'm a happy camper with Lubuntu 11.10 now :-)
KBD47

And you were blaming the new Kernel for breaking your video? :P

In fact, that proves how Linux is good and how Lubuntu is amazing. Learning and being patient is needed when it comes to Linux and I'm sure you have added something to your knowledge now :)

So happy to know 11.10 is working good now :)
I'm still with 11.04 and not willing to change ... don't have time to backup my stuff. Since it's a test PC (don't have my own laptop), I don't keep anything more than few weeks but because this is my lovely Lubuntu, I'll keep it.

---

### Post by KBD47 on 2011-10-31
> **amjjawad said:**
> And you were blaming the new Kernel for breaking your video? :P

In fact, that proves how Linux is good and how Lubuntu is amazing. Learning and being patient is needed when it comes to Linux and I'm sure you have added something to your knowledge now :)

So happy to know 11.10 is working good now :)
I'm still with 11.04 and not willing to change ... don't have time to backup my stuff. Since it's a test PC (don't have my own laptop), I don't keep anything more than few weeks but because this is my lovely Lubuntu, I'll keep it.

11.04 worked flawlessly for me except the wireless was weak. The wireless is much stronger in 11.10 glad I came across the youtube html5 thing, so nice to have working video :-)
  PS--when will the 12.04 Lubuntu beta come out? I will likely test it in virtualbox and/or live usb. Also, any way to nudge those guys into making Lubuntu 12.04 an LTS release, at least a 3 year LTS release? That would make a lot of people happy. It might last the rest of the life of some hardware.
Thanks.
KBD47

---

### Post by amjjawad on 2011-10-31
> **KBD47 said:**
> PS--when will the 12.04 Lubuntu beta come out? I will likely test it in virtualbox and/or live usb. Also, any way to nudge those guys into making Lubuntu 12.04 an LTS release, at least a 3 year LTS release? That would make a lot of people happy. It might last the rest of the life of some hardware.
Thanks.
KBD47

Still too early for that.

No, as long as we don't have enough resources, we can't go for LTS for now. But trust me in this ... we, home users, we don't really care about LTS or let's say, it won't make any difference. One year is not going to make huge difference. 2 years means 4 releases and NO ONE one of us will be patient enough NOT to try new releases :D

Anyway, I wish we could get extra resources but that's just a wish!

---

### Post by KBD47 on 2011-10-31
> **amjjawad said:**
> Still too early for that.

No, as long as we don't have enough resources, we can't go for LTS for now. But trust me in this ... we, home users, we don't really care about LTS or let's say, it won't make any difference. One year is not going to make huge difference. 2 years means 4 releases and NO ONE one of us will be patient enough NOT to try new releases :D

Anyway, I wish we could get extra resources but that's just a wish!

Well I wish I knew more about computer stuff. At least I can help beta test when the time rolls around. I would like to see a Lubuntu lts, but I can understand there not being enough resources. The good thing about Lubuntu is that it is unlikely to outrun hardware unless it is extremely old hardware.
KBD47

---

### Post by amjjawad on 2011-10-31
> **KBD47 said:**
> Well I wish I knew more about computer stuff. At least I can help beta test when the time rolls around. I would like to see a Lubuntu lts, but I can understand there not being enough resources. The good thing about Lubuntu is that it is unlikely to outrun hardware unless it is extremely old hardware.
KBD47

First of all, better late then never. 1000miles journey starts with one step :)

I have 12 years old laptop or maybe more? it's BROKEN but still working, not sure how? I'm trying to find some time to try Lubuntu on it. I can't install anything unless I take the HDD out and plugged in to my PC. Exactly a year ago, I spent 1 month trying to install Linux on that laptop ... nothing worked (tried 20 OS maybe?) except Mint LXDE 9. If Lubuntu can do it too, WOW :D

---

### Post by KBD47 on 2011-11-01
> **amjjawad said:**
> First of all, better late then never. 1000miles journey starts with one step :)

I have 12 years old laptop or maybe more? it's BROKEN but still working, not sure how? I'm trying to find some time to try Lubuntu on it. I can't install anything unless I take the HDD out and plugged in to my PC. Exactly a year ago, I spent 1 month trying to install Linux on that laptop ... nothing worked (tried 20 OS maybe?) except Mint LXDE 9. If Lubuntu can do it too, WOW :D

My guess is that since Mint LXDE worked on it, Lubuntu will as well :-)
  I've got a 12 year old dinosaur that I might try Lubuntu on someday, but it needs more ram, will take a maximum of 256 mg of ram, which should run Lubuntu. But anything on it will be slow, not sure what the processor is but would be slow.
KBD47

---

### Post by amjjawad on 2011-11-01
> **KBD47 said:**
> My guess is that since Mint LXDE worked on it, Lubuntu will as well :-)
  I've got a 12 year old dinosaur that I might try Lubuntu on someday, but it needs more ram, will take a maximum of 256 mg of ram, which should run Lubuntu. But anything on it will be slow, not sure what the processor is but would be slow.
KBD47

No, Lubuntu 10.04 (at that time - a year ago) didn't work. Only Mint LXDE 9 worked.
I'm not sure if it's worthy to try because the CPU is VERY SLOW, it's P2 with 366MHz and 64MB RAM. It's OmniBook 4150 HP.

With 256MB RAM, it won't be slow as mine, it will be acceptable.

The fun part of this is to make it work with what you already have without upgrading anything ;)

---

### Post by KBD47 on 2011-11-02
> **amjjawad said:**
> No, Lubuntu 10.04 (at that time - a year ago) didn't work. Only Mint LXDE 9 worked.
I'm not sure if it's worthy to try because the CPU is VERY SLOW, it's P2 with 366MHz and 64MB RAM. It's OmniBook 4150 HP.

With 256MB RAM, it won't be slow as mine, it will be acceptable.

The fun part of this is to make it work with what you already have without upgrading anything ;)

Those are about the same specs of my old computer, it has 64 mg of ram. It started to load an old version of Ubuntu 9 something I think, and nearly loaded Puppy Linux. I'm told there is a hack that will allow Puppy to load on very low ram, but I haven't tried it. I like Lubuntu better than Puppy because it has access to all the Ubuntu software. Lubuntu is so easy to adjust to that I find myself using it more and more on my netbook now.
KBD47

---

### Post by amjjawad on 2011-11-02
> **KBD47 said:**
> Those are about the same specs of my old computer, it has 64 mg of ram. It started to load an old version of Ubuntu 9 something I think, and nearly loaded Puppy Linux. I'm told there is a hack that will allow Puppy to load on very low ram, but I haven't tried it. I like Lubuntu better than Puppy because it has access to all the Ubuntu software. Lubuntu is so easy to adjust to that I find myself using it more and more on my netbook now.
KBD47

I'm ready to help you to install Lubuntu or any LXDE OS on that laptop. If your Laptop in better condition than mine and at least can boot from any device and you don't have to take the HDD out, it would be easier.
GRUB Legacy (AKA GRUB 0.97) NEVER worked on that laptop, only GRUB2 and I can't understand why?

See this: [http://ubuntuforums.org/showthread.php?t=1590614](http://ubuntuforums.org/showthread.php?t=1590614)

:)


[IMG]http://ubuntuforums.org/picture.php?albumid=2136&pictureid=7114[/IMG]

---

### Post by KBD47 on 2011-11-02
It is amazing that you got Mint LXDE to work with that little ram. My old computer is actually an Acer desktop. It has Windows 98 on it right now and will boot up and works fine with Windows. I will have to dig it out of the closet and try Lubuntu and Mint LXDE on it. Puppy almost booted up, it got so far as the bottom tool panel, but the rest never came up, so it's possible another light distro might work. May even give Slitaz a shot on it, or Bodhi, those are both quite light.
KBD47

---

### Post by amjjawad on 2011-11-02
> **KBD47 said:**
> It is amazing that you got Mint LXDE to work with that little ram.
But because the CPU is too slow, I can't use that laptop.  

> My old computer is actually an Acer desktop. It has Windows 98 on it right now and will boot up and works fine with Windows. 

That laptop had XP and it was slow more than anyone could imagine. Linux ran much faster.

> Puppy almost booted up, it got so far as the bottom tool panel, but the rest never came up, so it's possible another light distro might work. 

Didn't bother with Puppy. I prefer other alternatives.

> May even give Slitaz a shot on it, 

It's amazing you will get almost full OS with 30MB ONLY. However, drivers for Wireless Cards is a problem if you don't know how to get it.
I was about to join SliTaz team but Lubuntu is what I feel better with :)

> or Bodhi, 

I've never been a fan of E17 but I see everyone saying it's so light.

As I wrote on Lubuntu One Stop Thread, I'm trying to compare some systems and I just came to know that Crunchbang is by far has the lowest RAM usage, it's 52MB without anything opened.
This is as per Conky.

---

### Post by KBD47 on 2011-11-02
> **amjjawad said:**
> But because the CPU is too slow, I can't use that laptop.  


That laptop had XP and it was slow more than anyone could imagine. Linux ran much faster.


Didn't bother with Puppy. I prefer other alternatives.


It's amazing you will get almost full OS with 30MB ONLY. However, drivers for Wireless Cards is a problem if you don't know how to get it.
I was about to join SliTaz team but Lubuntu is what I feel better with :)


I've never been a fan of E17 but I see everyone saying it's so light.

As I wrote on Lubuntu One Stop Thread, I'm trying to compare some systems and I just came to know that Crunchbang is by far has the lowest RAM usage, it's 52MB without anything opened.
This is as per Conky.

Lubuntu is my favorite lightweight distro. I've tried E17 with Macpup and Bodhi, both were very attractive desktops, but I like that Lubuntu has all of Ubuntu behind it and that you can access all the Ubuntu software and support.
KBD47

---

