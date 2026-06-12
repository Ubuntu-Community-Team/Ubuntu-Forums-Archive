---
title: "Some dual boot problems"
date: 2012-01-09
forum: Desktop Environments
---

### Post by exzou on 2012-01-09
I have been using Ubuntu for about 10 months so I am still a bit wet behind the ears. I installed Ubuntu alongside vista basic on my Acer laptop with NO issues. I have a friend who wanted to dual boot vista/ Ubuntu (all versions of Ubuntu are 11.04) on his HP dv6-1030us. The first install Ubuntu worked just fine but the Grub did not detect Vista. ( I gave up trying to fix it and deleted all Vista partitions.) A couple months goes by and he decides he wants to run Vista and Ubuntu. I re-install Vista and it works just fine, however Ubuntu does not work. I do not even get a Grub menu. I am well above average ability in Windows but by no means am a professional but I can not understand why I am having so many problems.Last bit of info i thought of last minute, I have changed boot flags at some point to all partitions and can only get Vista to boot. I am beginning to think its some sort of HP problem on this model. Any assistance would be appreciated. If you need info from me on the PC just ask for it. 

The next question is if I just format and install Ubuntu with Windows in a virtual box, how well would it run running Vista Home in Ubuntu 11.04 on a Dual core T6400 running 2.00 ghz with 3gb of ram. More importantly would Netflix and I-Tunes work properly?

The ideal solution would be to get Vista and Ubuntu 11.04 to work together with Vista also running in Ubuntu.

Ideas? Thanks in advance all.

---

### Post by wildmanne39 on 2012-01-09
Hi, > The ideal solution would be to get Vista and Ubuntu 11.04 to work together with Vista also running in Ubuntu.Netflix is not going to run well in virtualbox without a lot of tweaking anyway and your system is a little light on resources to have great performance with vista and virtualbox with netflix in my opinion.

The reason ubuntu is not detected is that windows wants to be the only operating system on the computer and it over writes the grub menu of ubuntu but ubuntu is most likely still there unless you let windows have the entire desk. 

I am not an expert on this but here is a link for reinstalling grub.
[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)
You will need to use a livecd and chroot into ubuntu.

You can post the results of this command so we can see if your ubuntu is still there.
```
sudo fdisk -l
```
Thanks

---

### Post by exzou on 2012-02-18
Thanks for all the info. Finally got it up and running.

---

### Post by wildmanne39 on 2012-02-18
Hi, I am glad you got it working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

