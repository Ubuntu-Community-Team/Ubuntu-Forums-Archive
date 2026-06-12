---
title: "Do I even bother to install on a Dell?"
date: 2012-02-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kcfromks13 on 2012-02-13
I have an old Dell Precision 650 workstation that I wish to install the latest version of ubuntu on, yet I keep hearing about problems installing on a Dell computer. Should I even bother and if so what kind of problems do I need to look out for? Any advice would be great. Thank you.

---

### Post by winh8r on 2012-02-13
I would suggest downloading and burning a live cd of LUBUNTU at first, this is a "lighter" version of ubuntu designed for older computers/laptops where space and resources are at a premium.

You can run the live cd without making any changes to your laptop to enable you to identify any issues before you install permanently.


Get Lubuntu here:


[https://help.ubuntu.com/community/Lubuntu/GetLubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")


it is a good idea to read the release notes for each version before you download to ensure that your laptop has the minimum requirements to run that version.

hope this helps

---

### Post by snowpine on 2012-02-13
Dell is one of the most Linux-friendly manufacturers, I think there is an excellent chance that Linux will run well on your computer. What are your hardware specs? :)

---

### Post by kcfromks13 on 2012-02-13
I am going to try lubuntu. Thank you.

---

### Post by kcfromks13 on 2012-02-13
Specs are Intel Xeon 2.40 chip, ati radeon 256 mb video card, 40 Gb hd and 2 Gb of ram.

---

### Post by snowpine on 2012-02-13
Your hardware more than meets the requirements listed here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

The only component that might give you some trouble is the ATI Radeon card, hopefully another reader who is an ATI expert can help you with that (or you can read the Wiki).

---

### Post by drmrgd on 2012-02-13
I have two Dell computers...an old one and a fairly new one...and Ubuntu runs great on both!  You should be fine.

---

### Post by kcfromks13 on 2012-02-13
> **drmrgd said:**
> I have two Dell computers...an old one and a fairly new one...and Ubuntu runs great on both!  You should be fine.
have tried to install ubuntu and keep getting blank screen after i click on install screen. I let it sit for a while and nothing. I even tried removing "silent splash" and still no luck. Any ideas?

---

### Post by PaulW2U on 2012-02-13
> **kcfromks13 said:**
> Specs are Intel Xeon 2.40 chip, ati radeon 256 mb video card, 40 Gb hd and 2 Gb of ram.

My specs are as per my signature.

Ok, so I've upgraded the RAM and hard drives but I've never had any problems running any version of Ubuntu/Kubuntu/Xubuntu that I've tried since version 10.04.

In fact I've never heard of anyone else having problems that were specifically due to them using a Dell computer.

---

### Post by snowpine on 2012-02-13
> **kcfromks13 said:**
> have tried to install ubuntu and keep getting blank screen after i click on install screen. I let it sit for a while and nothing. I even tried removing "silent splash" and still no luck. Any ideas?

Do a forum Search on your specific graphics card. ATI drivers are a very "frequently asked question" on these forums (but it's important to follow how-to's for your *specific* card).

---

### Post by SeijiSensei on 2012-02-13
> **kcfromks13 said:**
> have tried to install ubuntu and keep getting blank screen after i click on install screen. I let it sit for a while and nothing. I even tried removing "silent splash" and still no luck. Any ideas?

Boot from the CD and hit F6 when you see the initial menu.  You'll see a list of additional parameters you can pass to the kernel.  Select "nomodeset", then hit enter to continue booting.  That may cure the problem.

I've installed Linux on Dells  -- servers, desktops, and notebooks -- for over a dozen years with nary a problem.  I don't know why you think they are somehow problematic when it comes to Linux.

---

