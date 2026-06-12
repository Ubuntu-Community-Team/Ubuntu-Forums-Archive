---
title: "console wireless and powertop battery life"
date: 2009-06-10
forum: General Help
---

### Post by heluani on 2009-06-10
These should probably be in two different threads but anyhow. 

I am trying to reduce battery consumption on a Macbook Air 2,1. I found that console with lynx is more than enough for most of my work. The problem is that I don't know how to connect to wireless if I kill gdm. I couldn't manage to set up wpa_supplicant correctly (wpa_client complains about not being able to comunicate with it) but nm-tools shows the available access points, so the interface is fine. Under X the gnome network manager works fine. Is wpa_supplicant the only way to connect to a WPA2 AP? if so, is there a way of finding out which command is nm-applet actually invoking?

On another note (also trying to reduce battery consumption). When I'm running X I get over 500 wakeups per second (reported by powertop) from 
```
<kernel core> : hrtimer_start (tick_sched_timer)
```
found a couple of bugs reported on this, but no clue as to how to solve this. Any ideas?

R.

---

