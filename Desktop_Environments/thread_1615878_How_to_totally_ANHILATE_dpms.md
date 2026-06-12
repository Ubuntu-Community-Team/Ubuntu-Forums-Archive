---
title: "How to totally ANHILATE dpms???"
date: 2010-11-07
forum: Desktop Environments
---

### Post by fonestar78 on 2010-11-07
Hi,

I like my new installation of Ubuntu 8.10 on my Panasonic CF-18 Toughbook but the one thing that is REALLY annoying me is the screen blanking out!

This should NEVER hapen on a mission-critical host!  Personally, I don't know why it would ever be enabled by default??  Would you want your air traffic controller's monitor going to sleep?  How about your 911 operator's screen?

I have editied /etc/X11/xorg.conf..
I have tried setting "xset s off" and "xset -dpms" in rc.local
From boot "noapic" "nolapic" "acpi=off" "noapm"
Edited the hald

The problem is that none of the xorg settings are respected by kde apparently.  Why, I do not know.  If I am root of a system that means I am root, not KDE, selinux or any desktop manager. 

So does anyone know how to totally ELIMINATE dpms and ANY and ALL power save for good?  If I have to recompile the whole damn kernel I guess that's what I have to do but is there a simpler way?

Thanks for any tips as my googling was proving fruitless!

---

### Post by 3Miro on 2010-11-07
Have you tried tweaking the KDE settings. If Xorg and ACPI are turned off, then KDE power manager may be the cause of the issue.

You are using KDE on Ubuntu 8.10, so I guess this is Kubuntu 8.10. 8.10 is no longer supported (it only has like 18 months of support). 8.10 also comes with KDE 4.1 (this includes Kubuntu and Ubuntu). KDE 4.1 wasn't very stable, it was more like a beta release and a fully stable one, so it is possible that the settings for the KDE power manager were are not implemented in that release anyway.

If this is an important machine, you should upgrade to 10.04 (Ubuntu or Kubuntu).

---

