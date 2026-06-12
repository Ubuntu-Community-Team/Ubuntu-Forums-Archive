---
title: "Remanufactured Dell (8.04 &amp; 8.10 video)"
date: 2009-01-31
forum: General Help
---

### Post by theozzlives on 2009-01-31
Kinda curious, I just got a Dell 2.1 GHz single core through mail order. It comes with an Intel integrated GPU. I can install 8.04 on it but not 8.10. With 8.10 it gets to the login and goes black, I can install safe graphics but then am stuck with 640x480. Dell dont have linux drivers for my card. Windows reports it as an Intel 82845G/GL/GE/PE/GV any ideas?

my whole network is 8.10 and I was hoping to swap HDs with my Apache server without much trouble.

---

### Post by mb_webguy on 2009-01-31
You'd have to reinstall the OS when you swap hard drives, since the system architectures are different.

As for the graphics card, [this]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=865&DwnldID=8203&lang=eng") might help.  (Google is your friend. ;))

---

### Post by dcstar on 2009-01-31
> **theozzlives said:**
> Kinda curious, I just got a Dell 2.1 GHz single core through mail order. It comes with an Intel integrated GPU. I can install 8.04 on it but not 8.10. With 8.10 it gets to the login and goes black, I can install safe graphics but then am stuck with 640x480. Dell dont have linux drivers for my card. Windows reports it as an Intel 82845G/GL/GE/PE/GV any ideas?

my whole network is 8.10 and I was hoping to swap HDs with my Apache server without much trouble.

What is the output of:

```
lspci | grep VGA
```

8.10 will not work on old Nvidia cards, but I never saw a message about old Intel chips.

---

### Post by theozzlives on 2009-01-31
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

---

### Post by theozzlives on 2009-01-31
> **mb_webguy said:**
> You'd have to reinstall the OS when you swap hard drives, since the system architectures are different.

As for the graphics card, [this]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=865&DwnldID=8203&lang=eng") might help.  (Google is your friend. ;))

can't I have Ubuntu re-detect the hardware?

---

### Post by theozzlives on 2009-01-31
> **dcstar said:**
> What is the output of:

```
lspci | grep VGA
```

8.10 will not work on old Nvidia cards, but I never saw a message about old Intel chips.

If 8.10 won't work then future LTS releases wont either, am I correct? I'd be stuck with Winblows on that computer.

---

### Post by jespdj on 2009-01-31
> **theozzlives said:**
> If 8.10 won't work then future LTS releases wont either, am I correct? I'd be stuck with Winblows on that computer.
No, you're not correct. It depends on why it doesn't work. If it's because a bug, then it's possible that a future Ubuntu release will work if the bug is fixed.

With regards to nVidia: The reason why older nVidia cards don't work with 8.10 is because something has changed in the version of X.org (the X Windows software) that's used in 8.10, which makes it incompatible with older nVidia drivers. Probably nVidia is not going to fix those old drivers to work with the new X.org, so older nVidia cards will not be supported in future versions.

However, this is specific to nVidia and you have an Intel graphics card and not nVidia, so this does not apply to your system.

---

### Post by theozzlives on 2009-01-31
> **dcstar said:**
> What is the output of:

```
lspci | grep VGA
```

8.10 will not work on old Nvidia cards, but I never saw a message about old Intel chips.

> **jespdj said:**
> No, you're not correct. It depends on why it doesn't work. If it's because a bug, then it's possible that a future Ubuntu release will work if the bug is fixed.

With regards to nVidia: The reason why older nVidia cards don't work with 8.10 is because something has changed in the version of X.org (the X Windows software) that's used in 8.10, which makes it incompatible with older nVidia drivers. Probably nVidia is not going to fix those old drivers to work with the new X.org, so older nVidia cards will not be supported in future versions.

However, this is specific to nVidia and you have an Intel graphics card and not nVidia, so this does not apply to your system.

So your saying I can't use 8.10, but maybe 9.04? That makes the hard drive swap very complicated. I need to do this my web site is running on a 500 MHz w/256 RAM, the Dell is 2.1 GHz w/512 RAM. It just has a 20 GB hard drive and the one I want to put in is a 150 GB.

---

### Post by theozzlives on 2009-01-31
> **mb_webguy said:**
> You'd have to reinstall the OS when you swap hard drives, since the system architectures are different.

As for the graphics card, [this]("http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=865&DwnldID=8203&lang=eng") might help.  (Google is your friend. ;))

That driver didn't help. I guess since nobody out there has any answers, And you say I'm gonna have to re-install to swap drives, and I'm having partitioning problems. I'll just have to take my site down for a day, maybe tommorrow, I don't feel like it today.

---

### Post by theozzlives on 2009-02-16
I found the problem, it turned out to be the nUbuntu login screen I got from gnome-look.org. I changed my login screen and it works fine.

---

