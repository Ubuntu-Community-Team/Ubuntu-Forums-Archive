---
title: "Random issues after running upgrade (brightness won't adjust, desktop acting up)"
date: 2013-08-29
forum: Desktop Environments
---

### Post by soapdude on 2013-08-29
Hello, I have a Lenovo x121e running Ubuntu 12.04 LTS. I recently upgraded the system, and have since been having a lot of issues. The first and most noticeable issue was that the brightness would no longer adjust using the hardware key (or any other method). When I press the hardware key, the display pops up showing that the brightness is going up or down, but it has no effect on the actual screen brightness. I installed xbrightness, and ran xbrightness -set 50, but it also had no affect.

Other issues are quite bothersome. When I open a new document for example, I can still see the desktop background behind it, and sometimes I can't switch between open documents for some seconds.

Is there some easy way to revert to the state before the upgrade? How can I go about diagnosing the specific problem? Thank you in advance!

---

### Post by Petro Dawg on 2013-08-29
[http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version](http://askubuntu.com/questions/82140/how-can-i-boot-with-an-older-kernel-version)

Hold shift during boot to bring up Grub (if it doesn't automatically come up already)

in grub menu you should see an option to run "Previous Linux Version", select the last one that worked.

You can then uninstall the later version that does not work using Synaptic Package Manager or whatever other method you prefer.

---

### Post by soapdude on 2013-08-30
Hey thanks, I hadn't thought of that actually! This will revert me to a previous kernel, but there may have been many package updates since the last kernel update, is that correct?

I'll try this today, but I'm wondering if there's a way to revert recently upgraded packages as well? Or am I confusing myself? Thanks again!

---

### Post by Dennis N on 2013-08-30
Those other upgrades are not going to be changed by using the previous kernel and will still work.

---

### Post by soapdude on 2013-08-30
> **Dennis N said:**
> Those other upgrades are not going to be changed by using the previous kernel and will still work.

Right, I get this, so what I'm saying is could it possibly be that one of the packages is causing the problem instead of the kernel? If so, how can I go about determining which package caused the problem? Sorry, I haven't been able to test this yet as I'm not at this computer at the moment. Thanks!

---

