---
title: "X doesn't catch button releases on touchpad tap"
date: 2013-01-24
forum: Desktop Environments
---

### Post by UserNameAlreadyTaken on 2013-01-24
I'm running Ubuntu 12.10 on a VMWare VM at work (I don't have the option of running it natively). I have a Logitech T650 touchpad for my pointing device. The pad is a big hardware button, but it also has the ability to register taps as clicks. Under Windows (the base OS), it works fine. Under Ubuntu, it does not always register a tap as a click. It acts identically to clicking the mouse button down, but not releasing it. If I then touch the pad again (not tap or click, just touch) and move my finger, it completes the click action. When I tap (not click) with two fingers for button 3 or with three fingers for button 2, it is fine.

I ran xinput test and got the following results.
This is from clicking the hardware button:
> 
button press   1 
button release 1

This is from a tap & release:
> button press   1

After the tap & release, I touched the pad again and moved laterally:
> motion a[0]=42139 a[1]=24310 
button release 1 
motion a[0]=42178 a[1]=24310 
motion a[0]=42217 a[1]=24310 
motion a[0]=42256 a[1]=24310 
motion a[0]=42295 a[1]=24310 

So for some reason, X is not catching my tap-release. Is there a way to adjust this? VMWare reports the device as a generic mouse, so I don't have anything on the touchpad configuration settings page.

---

