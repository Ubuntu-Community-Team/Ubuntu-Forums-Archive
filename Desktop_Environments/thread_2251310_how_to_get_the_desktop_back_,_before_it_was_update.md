---
title: "how to get the desktop back , before it was updated to the new look"
date: 2014-11-03
forum: Desktop Environments
---

### Post by stroma on 2014-11-03
I had opted for Ubuntu because i trust into the opensource comunity. Kicked Windows 8 out and installed Ubuntu. On Nov 2, 2014 I updated my ubuntu 14.04 as usual - after all we all want a secure and stable system.  But.. OOOPS! My unity has gone, the clock looks different, I have no time indication for other locations anymore, everything is spread all over the screen, the windows cannot be minimized anymore, etc etc. I want my old desktop look back  - but i cannot find any way to get it looking the same again. I understand that "always forward" is the policy these days - but sometimes, some people just don't have the time to get learning all new things, just because they do an update. I would so much appreciate to be informed about such a major change, so i can decide myself, if i want to "eat" it...

---

### Post by vasa1 on 2014-11-03
Most people feel that there was no major change in 14.04 > 14.10. So it's probable that something went wrong in your "update".

BTW, staying with 14.04 would have kept you with "a secure and stable system". 14.04 is LTS.

---

### Post by grahammechanical on 2014-11-03
Updates do not run in the background unless we have set the Update Manager to run security updates automatically. Update Manager always shows me a list of packages to be updated and I am asked to confirm. With some updates I am even required to authenticate by entering my password.

I do not accept your criticism of the way updates are handled in Ubuntu. It is a fact that Long Term Support versions such as 14.04 do not get changes to the User Interface. They do get kernel upgrades to fix security vulnerabilities and they require a recompiling of the video driver. This is done as part of the update and sometimes things break when using a proprietary video driver.

Things also break if we have heavily modified the user interface. Are you using a default theme? There are a couple of things you can try.

1) At the boot menu select the Advanced Options for Ubuntu sub-menu and then select one of the previous kernel versions. If that has the desired effect continue using that kernel until another kernel update fixes the problem.

2) At the boot menu select Advanced Options for Ubuntu and select Recovery Mode. At the Recovery menu select Resume. That may get you to a desktop using an open source video driver. At the desktop use Additional drivers to experiment with video drivers.

---

### Post by buzzingrobot on 2014-11-03
> **stroma said:**
> I had opted for Ubuntu because i trust into the opensource comunity. Kicked Windows 8 out and installed Ubuntu. On Nov 2, 2014 I updated my ubuntu 14.04 as usual - after all we all want a secure and stable system.  But.. OOOPS! My unity has gone, the clock looks different, I have no time indication for other locations anymore, everything is spread all over the screen, the windows cannot be minimized anymore, etc etc. I want my old desktop look back  - but i cannot find any way to get it looking the same again. I understand that "always forward" is the policy these days - but sometimes, some people just don't have the time to get learning all new things, just because they do an update. I would so much appreciate to be informed about such a major change, so i can decide myself, if i want to "eat" it...

Updating 14.04 would not do that unless some serious and unusual breakage occured somewhere.  *Upgrading* to 14.10 would not have done that either; it's using the same version of Unity.

Have you altered your software sources beyond the default? Added PPA's that overwrote core system packages?

If possible, a screenshot would be useful to see if you have a broken Unity or somehow added a different interface altogether.

---

### Post by JohnnyComeL8ly on 2014-11-05
Maybe OP would like to try reinstalling his/her Lubuntu? Just an idea...

---

