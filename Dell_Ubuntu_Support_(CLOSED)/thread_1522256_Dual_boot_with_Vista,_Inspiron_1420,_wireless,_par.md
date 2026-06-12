---
title: "Dual boot with Vista, Inspiron 1420, wireless, partition issues"
date: 2010-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aaronchall on 2010-07-01
My friend wants to try Ubuntu on his laptop, while keeping his Vista installation. Thus, a dual boot is in order.

I want to help him, but I'm working around two specific issues. 

1) LiveCD didn't have wireless working right off, he has a Broadcom 1390 minicard. 

2) Vista shrink partition operation isn't showing more than 2 GB to shrink at the end of a MyDefrag Consolidate Free Space run. Is GParted from a Livecd an issue so long as I follow these instructions?: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

I'd like to install on an expanded recovery partition, so if he has the cd, is there a problem with this?

(Vista service pack 2 won't install for some reason, so he's using (I assume) service pack 1, any issues coming from this?)

Aaron

---

### Post by aaronchall on 2010-07-02
I'm gonna be working on this in about 30 minutes, so a few words of encouragement would be great.

Aaron

---

### Post by aaronchall on 2010-07-06
Well, I figure I'll document this experience here too, in case someone needs help with a similar case and finds my question with no answer:

"My friend wants to try Ubuntu on his laptop, while keeping his Vista installation. Thus, a dual boot is in order."

Instead of overwriting his recovery partition, I overwrote his media direct partition. Probably should have checked with him first, but it seemed like the best thing to do given the geometries of the dist according to GParted, and I'm pretty sure he never uses that.

"1) LiveCD didn't have wireless working right off, he has a Broadcom 1390 minicard."

Resolved by being plugged into ethernet cable and downloading Broadcom driver, I believe with System>>Administration>>Hardware Drivers (a GUI solution, but it worked). I did this after the install, which is now discussed below.

"2) Vista shrink partition operation isn't showing more than 2 GB to shrink at the end of a MyDefrag Consolidate Free Space run. Is GParted from a Livecd an issue so long as I follow these instructions?: [https://help.ubuntu.com/community/Ho...dowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")"

The specific instructions I was referring to are to "***remove the check mark in the 'round to cylinders' checkbox***." Otherwise, using GParted first seemed straightforward.  I wish there was a bit more guidance when using the install disk. 

Specifically, I shrunk the Vista partition with GParted because the "shrink partition" inside Vista would only give up 2 GB, and I wanted more like 15. Why would Microsoft/Windows/Bill Gates make a tool that doesn't work? Anyways, I used GParted, removed the check mark (maybe that should have a bit of an explanation in the live CD: like "don't check if dual booting Windows"), and didn't have to use the Vista restore disk CD. I rebooted Vista twice just to be certain.  Did NOT have ANY problems with Vista or the install.  I did the comprehensive media how-to for him, installed flash and some useful plugins for Firefox, and I installed VirtualBox and RCommander for future use, and he loves it. Now he can use Vista when he HAS to, but he has a much more usable/stable/fast operating system in Ubuntu. He sees what I did as valuable, which is what I was aiming for. And he's learning to run his system on his own.

Aaron

---

