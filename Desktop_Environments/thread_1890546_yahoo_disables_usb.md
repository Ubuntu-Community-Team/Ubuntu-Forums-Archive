---
title: "yahoo disables usb"
date: 2011-12-03
forum: Desktop Environments
---

### Post by ZenMasta on 2011-12-03
I set my brother up with a refurbished hp a while ago, has 10.04. It's been humming along just great until this past week.

Certain websites, especially yahoo.com will disable all usb devices (which consist of keyboard and mouse).

At first I thought it was just crashing, but when I was able to press the power button and get the friendly shutdown/restart screen I figured it was something else. So sure enough I plug in a ps2 keyboard and it works fine I can ctrl+c firefox to close it. But usb is still disabled.

He was using firefox 3x so I upgraded to 8x thinking it might be a flash issue but it does the same thing with firefox 8 and to verify it wasn't a flash problem, youtube.com works just fine.

Installed chrome and there is no problem with yahoo.com that causes usb devices to get turned off.

I prefer firefox so I'd like to solve this problem instead of working around by just using chrome instead. This is one of the most bizzare things I've encountered I think.

Any ideas? Intel Core 1.86 GHz and 1gb ram 
:popcorn:

---

### Post by bluexrider on 2011-12-03
I don't see that Firefox would have anything to do with system commands unless he's got something cached as a .js that would invoke this.

if you use the system monitor are there any strange processes running before opening Firefox or rather when using Firefox? 

I would set another profile on the machine and run Firefox to see if it kills the USB if it does its a system issue. If it doesn't its a user issue.

---

### Post by oldtimer7777 on 2011-12-03
Clear your caches with Bleachbit when you have a chance and see if that helps at all.

sudo apt-get install bleachbit
sudo bleachbit

Be careful not to delete your bookmarks or passwords using bleachbit. 

> **ZenMasta said:**
> I set my brother up with a refurbished hp a while ago, has 10.04. It's been humming along just great until this past week.

Certain websites, especially yahoo.com will disable all usb devices (which consist of keyboard and mouse).

At first I thought it was just crashing, but when I was able to press the power button and get the friendly shutdown/restart screen I figured it was something else. So sure enough I plug in a ps2 keyboard and it works fine I can ctrl+c firefox to close it. But usb is still disabled.

He was using firefox 3x so I upgraded to 8x thinking it might be a flash issue but it does the same thing with firefox 8 and to verify it wasn't a flash problem, youtube.com works just fine.

Installed chrome and there is no problem with yahoo.com that causes usb devices to get turned off.

I prefer firefox so I'd like to solve this problem instead of working around by just using chrome instead. This is one of the most bizzare things I've encountered I think.

Any ideas? Intel Core 1.86 GHz and 1gb ram 
:popcorn:

---

