---
title: "Xubuntu 14.04 won't shutdown it logs out instead?"
date: 2014-05-05
forum: Desktop Environments
---

### Post by frank18 on 2014-05-05
Hi guys; Lately i've been having this issue, when i click on shutdown it goes to log out, screen then i log in and some time then i click shutdown  and it shuts off,why should i goes through all this now it never done it before it went LTS!

---

### Post by frank18 on 2014-05-06
Hello guys isn't this worth a reply with some Help?

---

### Post by frank18 on 2014-05-09
> **frank18 said:**
> Hello guys isn't this worth a reply with some Help?




Hi guys don't tell a simple Shutdown issue and  nobody has a clue why this happens,never had this in previous editions of Xubuntu, and i have to go and install other distro because of this?,i think it's ridiculous.

---

### Post by frank18 on 2014-05-09
Hi guys can someone please tell me why when i shutdown Xubuntu 14.04 it logs out instead? never had this in other editions

---

### Post by slooksterpsv on 2014-05-09
How did you install Xubuntu? Did you upgrade or new install? - Reason I ask is cause I've had this issues if I've had settings from my old profile copied over to a new install.

---

### Post by frank18 on 2014-05-09
> **slooksterpsv said:**
> How did you install Xubuntu? Did you upgrade or new install? - Reason I ask is cause I've had this issues if I've had settings from my old profile copied over to a new install.

Thanks slooksterpsy; i did a fresh install from Xubuntu ISO LTS after april 17 official release,
i never had this before xubuntu 12.04 or 1310 beta or 14.04 beta, so this  only happens  after the official release.

---

### Post by mörgæs on 2014-05-09
Threads merged. 
Please stop multiposting.

---

### Post by frank18 on 2014-05-09
> **mörgæs said:**
> Threads merged. 
Please stop multiposting.

Is that your way of helping?if i had help i would not need to multipost!

---

### Post by cariboo on 2014-05-10
Does:

```
sudo shutdown -h now
```

work for you?

---

### Post by CharlesA on 2014-05-10
> **frank18 said:**
> Is that your way of helping?if i had help i would not need to multipost!

You may bump your thread once every 24 hours if no one has replied to it. Creating multiple threads on the same subject just dilutes the community effort.

Try what cariboo907 suggested and see if that shuts the machine down or not.

---

### Post by slooksterpsv on 2014-05-10
Are you going through the Whisker menu to shutdown or the Action bar at the top right (by default)?

Besides that, could you paste your .xsession-errors and/or .xsession-errors.old to pastebin?

---

### Post by frank18 on 2014-05-11
> **cariboo907 said:**
> Does:

```
sudo shutdown -h now
```

work for you?

Thanks it did  shutdown but just till next reboot,i dicided to make another fresh install and it's ok for now, hope it stays that way,thanks anyway for your help and  effort.

---

### Post by charlieprime on 2014-07-31
I found a solution that works for *my* hardware.  
&#65279;
My machine is an old Acer TravelMate 4320 laptop.  It uses this wireless card: Broadcom BCM4311 802.11b/g WLAN.  I’m running a clean install of Xubuntu 14.04.

I tried all the various grub file changes to &#65279;GRUB_CMDLINE_LINUX_DEFAULT= recommended here on Ubuntu Forums.  None worked.

The problem appears to be with the package bcmwl-kernel-source. ( [http://packages.ubuntu.com/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/lucid/bcmwl-kernel-source) )

Removing that package allowed me to shutdown the machine using both the GUI and terminal.  Here is the command I used to remove that package:

*sudo apt-get remove bcmwl-kernel-source*

In order to get my Broadcom wireless “card” to work, I installed the drivers recommended for the BCM4311 here:

[https://wiki.debian.org/bcm43xx](https://wiki.debian.org/bcm43xx)

For me, it was the B43 drivers.  Use the driver appropriate for your wireless chipset. I used this command to install them:

*sudo apt-get install firmware-b43-installer b43-fwcutter*

I hope this helps you avoid the hours and frustration I spent on this problem.

---

### Post by slooksterpsv on 2014-07-31
Thank you for figuring that out, I never thought it would be a wireless driver issue. I'll keep that in mind if someone else has the same issue. If you could mark the Thread as Solved so they can see what you did to fix it, that'd be great! =D

---

### Post by john4068 on 2014-08-01
I have the same problem with 14.04 LTS(64 bit) and, yes, "sudo shutdown -h now" does make it shutdown.But that doesn't negate the fact there is something very wrong with the shutdown options. It was a full install recently, without any old settings. Even though it says "Shut Down" all you get when you click it is 'Lock' or 'Log Out' and they don't work anyway. Hibernate is also missing.
I have noticed that the Shutdown works correctly from the Login screen.
Not a 100% certain (old timers!) but I am sure the Shutdown did work when first installed. And the only software installed recently has been the updates.

Anyone like a challange?

---

