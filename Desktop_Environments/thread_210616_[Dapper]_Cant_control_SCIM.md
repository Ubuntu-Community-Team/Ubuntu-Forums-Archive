---
title: "[Dapper] Cant control SCIM"
date: 2006-07-07
forum: Desktop Environments
---

### Post by aha2006 on 2006-07-07
Hi All,

I just installed Ubuntu Dapper and everything is perfect except SCIM. When I installed my system, I chose Vietnamese as my default language and I got SCIM with Vietnamese input method (VIQR) installed by default. The problem is it seems I cannot temporarily turn on/off VIQR input method or change to other input methods (I installed Korean support after system installation). Trying to bring up SCIM using Ctrl+Space, Shift+Space also did nothing. I tried to run "scim -d" and got SCIM icon in my panel but there is nothing there except option to run SCIM-setup (same as in Preferences=>SCIM Input Method Setup).

Could you guys give me any suggestion?

Thank a million !!!

PS: Xgl+Compiz run well on my system (Pen4 1.6GHz + 1GB Ram + Geforce FX5200 - SLED 10.1 beta refused to support this card :(  ). However, running gset-compiz gives "Segmentation Fault". Did I miss anything?

---

### Post by aha2006 on 2006-07-08
UPDATE: I was able to fix the problem myself. I simply replace 90im-switch script in /etc/X11/Xsession.d/ with

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"

Then Ctrl+Space works perfectly. Also, the default short-cut to show IM Methods menu seems to conflict with "cube"-shortcut of Compiz. I just changed it to something else.

My Ubuntu system is now in a perfect shape. :D 

Cheers !!!

---

### Post by rykel on 2006-09-12
> **aha2006 said:**
> 
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"


Hi,

2 questions:

1. Does your script prevent SCIM from automatically loading up at boot-time? (I do NOT want SCIM all the time, as it conflicts with Gizmo and the official Firefox.)

2. Does it allow a user to turn on and off SCIM anytime easily?

When I am using SCIM, I use the smart Pinyin.

Thank you!

---

